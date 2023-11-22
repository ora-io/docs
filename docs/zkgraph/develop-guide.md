# Develop Guide

### zkGraph Configuration (`zkgraph.yaml`)

`zkgraph.yaml` defines the configuration of a zkGraph.

It specifies information including:

* data source
* target blockchain network
* target smart contract address
* target event
* event handler

An example `zkgraph.yaml`:

```yaml
specVersion: 0.0.1
name: ex_addr
description: "Demo graph for zkAutomation. Use the source contract address as the trigger payload."
repository: https://github.com/hyperoracle/zkgraph
dataSources:
  - kind: ethereum/contract
    network: sepolia
    source:
      address: '0xa60ecf32309539dd84f27a9563754dca818b815e'
    mapping:
      kind: ethereum/events
      apiVersion: 0.0.1
      language: wasm/assemblyscript
      file: ./mapping.ts
      eventHandlers:
        - event: "Sync(uint112,uint112)"
          handler: handleEvents
dataDestinations:
  - kind: ethereum/contract
    network: sepolia
    destination:
      address: "0x0000000000000000000000000000000000000000"
```

More examples can be found as [templates of zkGraph scaffold](https://github.com/hyperoracle/zkgraph-cli/tree/main/packages/create-zkgraph/templates).

#### Supported Networks (network)

`network` specifies the `dataSource` network for data source or `dataDestination` network for verification contract deployment and zkGraph publish.

`network` should follow the format of all lower-case letters (eg. mainnet, or goerli) with the following naming.

<table><thead><tr><th width="263">Network (ChainID)</th><th data-hidden data-type="checkbox">zkGraph Register</th><th data-hidden>Name in zkgraph.yaml</th><th data-hidden data-type="checkbox">dataSource</th><th data-hidden data-type="checkbox">dataDestination</th></tr></thead><tbody><tr><td>Ethereum Mainnet (1)</td><td>false</td><td><code>mainnet</code></td><td>true</td><td>false</td></tr><tr><td>Ethereum Goerli (5)</td><td>false</td><td><code>goerli</code></td><td>true</td><td>false</td></tr><tr><td>Ethereum Sepolia (11155111)</td><td>true</td><td><code>sepolia</code></td><td>true</td><td>true</td></tr></tbody></table>

#### apiVersion

`apiVersion` specifies the `zkgraph-lib` version or any other libraries, used by a zkGraph, in Hyper Oracle Node or Hyper Oracle compiler server.

<table><thead><tr><th width="146">apiVersion</th><th width="186.33333333333331">zkgraph-lib Version</th><th>Notes</th></tr></thead><tbody><tr><td>0.0.1</td><td>0.0.8</td><td>Added <code>event</code> as data source, multi-address and multi-sources for data source.</td></tr></tbody></table>

#### specVersion

`specVersion` specifies the `zkgraph.yaml` configuration format version, parsed by Hyper Oracle Node or other libraries.

<table><thead><tr><th>specVersion</th><th>Updated Data Fields</th><th data-type="content-ref">Example</th></tr></thead><tbody><tr><td>0.0.1</td><td>/</td><td><a href="https://github.com/hyperoracle/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml">https://github.com/hyperoracle/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml</a></td></tr></tbody></table>

### zkGraph Mapping (`mapping.ts`)

A required function for zkGraph mapping is `handleEvents`.

The `mapping.ts` with `handleEvents` should be structured as follows, and should not be modified in most cases:

```typescript
// imports
import { require, Bytes, Event, BigInt } from "@hyperoracle/zkgraph-lib";
// ...import from other local files

// other functions
// ...

// handleEvents function
export function handleEvents(events: Event[]): Bytes {
  // ...core logics
  return state;
}
```

#### Requirements

* **Function Definition of `handleEvents`**: `export function handleEvents(events: Event[]): Bytes {}`
* **Return Value of `handleEvents`**: 32-byte length `Bytes`. Use `Bytes.padStart` or `Bytes.padEnd` to pad it to required length.

### zkGraph Development Tips

#### Develop

* Provable program needs to be compilable and runnable in normal execution runtime first.

```typescript
// Code not compilable (due to reassign `state` which is constant)
export function handleEvents(events: Event[]): Bytes {
  const state = new Bytes(0);
  state = new Bytes(0);
  return state;
}

// Code not executable or runnable (due to divide number by zero)
export function handleEvents(events: Event[]): Bytes {
  const state = new Bytes(0);
  const NAN = BigInt.fromI32(0).div(0);
  return state;
}
```

* For generating proof on zkWASM, do not use io syscalls like `console` etc. `console.log(string)` (note that only `string` type is supported in AssemblyScript) should only be used in debug stage.

```typescript
export function handleEvents(events: Event[]): Bytes {
  let state = new Bytes(0);
  // Won't be compiled, because type not supported in AssemblyScript
  console.log(state);
  // Will be executed, but won't be proved successfully.
  console.log(state.toString());
  return state;
}
```

#### Optimize

* Look at (approximate) WASM cost for each operation! More complex logic (eg. anything with lots of `if` statements or `string`) usally means more instructions, which means longer proof generation time.

```typescript
// WASM cost: 65 line of wat.
Bytes.padStart(targetLength: i32, padDigit: u8 = 0): Bytes

// WASM cost: 1177 lines of wat.
BigInt.toString(radix: i32 = 10): string
```

* Don't use template literals (`${}`), for example when throwing errors, because it will be compiled to too many WASM instructions (\~1000 diff).

```typescript
// 2547 lines in generated .wat file with template literal
export function handleEvents(events: Event[]): Bytes {
  let state = new Bytes(0);
  if (state.length != 0) {
    throw new Error(`Invalid state length: ${state.length}, expected 0 bytes.`);
  }
  return state;
}

// 2179 lines in generated .wat file without template literal
export function handleEvents(events: Event[]): Bytes {
  let state = new Bytes(0);
  if (state.length != 0) {
    throw new Error(`Invalid state length, expected 0 bytes.`);
  }
  return state;
}
```

* Try not to use keywords that may introduce extra global init code e.g. `new`, `static` etc. `changetype` is fine, [because](https://github.com/AssemblyScript/assemblyscript/issues/549#issuecomment-474005579) it just changes the type statically and does not result in any actual instructions.
* You can use third-party optimization tools (such as [wasm-opt](https://www.npmjs.com/package/wasm-opt)) to reduce WASM binary size.
