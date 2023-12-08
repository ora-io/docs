# Develop Guide

### zkGraph Configuration (`zkgraph.yaml`)

`zkgraph.yaml` defines the configuration of a zkGraph.

It specifies information including:

* data source
* target blockchain network
* target smart contract address
* target event
* event handler

An example of `zkgraph.yaml`:

```yaml
specVersion: 0.0.2
apiVersion: 0.0.2
name: eg_event
description: "This demo zkGraph shows 3 ways to access / filter out source events."
repository: https://github.com/hyperoracle/zkgraph
dataSources:
  - kind: ethereum
    network: sepolia
    event:
      - address: '0xa60ecf32309539dd84f27a9563754dca818b815e'
        events: 
          - "Sync(uint112,uint112)"

mapping:
  language: wasm/assemblyscript
  file: ./mapping.ts
  handler: handleBlocks

dataDestinations:
  - kind: ethereum
    network: sepolia
    address: "0x0000000000000000000000000000000000000001"
```

More examples can be found as [templates of zkGraph scaffold](https://github.com/hyperoracle/zkgraph-cli/tree/main/packages/create-zkgraph/templates).

#### Supported `network` with Features

`network` specifies the `dataSource` network for data source or `dataDestination` network for verification contract deployment and zkGraph publish.

`network` should follow the format of all lower-case letters (eg. mainnet, or goerli) with the following naming.

<table data-full-width="false"><thead><tr><th width="191">Network (ChainID)</th><th width="148">Name in YAML</th><th width="191">dataSource</th><th width="156">dataDestination</th><th width="194">zkGraph Deployment</th></tr></thead><tbody><tr><td><p>Ethereum Mainnet</p><p>(1)</p></td><td><code>mainnet</code></td><td>✅ <br>(<code>handleBlocks</code>)</td><td>❌</td><td>❌</td></tr><tr><td><p>Ethereum Goerli</p><p>(5)</p></td><td><code>goerli</code></td><td>✅ <br>(<code>handleBlocks</code>)</td><td>❌</td><td>❌</td></tr><tr><td><p>Ethereum Sepolia</p><p>(11155111)</p></td><td><code>sepolia</code></td><td>✅ <br>(<code>handleBlocks</code>)</td><td>✅</td><td>✅</td></tr></tbody></table>

#### `apiVersion`

`apiVersion` specifies the `zkgraph-lib` version or any other libraries, used by a zkGraph, in zkOracles including zkGraph compiler.

<table><thead><tr><th width="132">apiVersion</th><th width="186.33333333333331">zkgraph-lib Version</th><th>Notes</th></tr></thead><tbody><tr><td>0.0.1</td><td>0.0.8</td><td>Added <code>event</code> as data source, multi-address and multi-sources for data source.</td></tr><tr><td>0.0.2</td><td>1.0.0</td><td>Updated <code>block</code> as data source, <code>block</code> contains both <code>event</code> and <code>account</code> data.</td></tr></tbody></table>

#### specVersion

`specVersion` specifies the `zkgraph.yaml` configuration format version, parsed by Hyper Oracle Node or other libraries.

<table><thead><tr><th width="147.33333333333331">specVersion</th><th width="274">Updated Data Fields</th><th data-type="content-ref">Example</th></tr></thead><tbody><tr><td>0.0.1</td><td>/</td><td><a href="https://github.com/hyperoracle/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml">https://github.com/hyperoracle/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml</a></td></tr><tr><td>0.0.2</td><td><code>apiVersion</code>, <code>dataSources</code>, <code>mapping</code></td><td><a href="https://github.com/hyperoracle/zkgraph-cli/blob/abfbb9b33e91099b1f4b791aefe2bf7decc05741/packages/create-zkgraph/templates/template-event/src/zkgraph.yaml">https://github.com/hyperoracle/zkgraph-cli/blob/abfbb9b33e91099b1f4b791aefe2bf7decc05741/packages/create-zkgraph/templates/template-event/src/zkgraph.yaml</a></td></tr></tbody></table>

### zkGraph Mapping (`mapping.ts`)

#### Basic

A required function for zkGraph mapping is `handleBlocks`.

The `mapping.ts` with `handleBlocks` should be structured as follows, and should not be modified in most cases:

```typescript
// imports
import { require, Bytes, Event, BigInt } from "@hyperoracle/zkgraph-lib";
// ...import from other local files

// other functions
// ...

// handleBlocks function
export function handleBlocks(blocks: Block[]): Bytes {
  // ...core logics
  return state;
}
```

#### Requirements

* **Function definition of required function needs to match with the defined definition.**
* **Return value of required function needs to match with the defined definition.**

#### Access `Event` Data

1. Define specific contract address and events in `zkgraph.yaml`.
2. Access specific events in `mapping.ts` `handleBlocks()`, after `zkgraph.yaml`'s filtering.

```typescript
// Option #1: access all (matched) events of the latest block
let events: Event[] = blocks[0].events;

// Option #2: access (matched) events, if with a given account address
let eventsByAcct: Event[] = blocks[0].account(address).events;

// Option #3: access (matched) events, if with a given account address and a given esig
let eventsByAcctEsig: Event[] = blocks[0].account(address).eventsByEsig(esig_sync);
```

See [full example here](https://github.com/hyperoracle/zkgraph-cli/blob/d624dcb03d0d916f08bf3b2970c69b034ec753a3/packages/create-zkgraph/templates/template-event/src/mapping.ts).

#### Access `Account` (storage slot) Data

1. Define specific storage address and slots in `zkgraph.yaml`.
2. Access specific slots in `mapping.ts` `handleBlocks()`, after `zkgraph.yaml`'s filtering.

```typescript
// get source Account object by address
let acct: Account = blocks[0].account(addr);
  
// Option #1: access source Slot value by key
let slotValue: Bytes = acct.storage(key);

// Option #2: access source Slot object by key
let slot: Slot = acct.slots[acct.getSlotId(key)];
```

See [full example here](https://github.com/hyperoracle/zkgraph-cli/blob/d624dcb03d0d916f08bf3b2970c69b034ec753a3/packages/create-zkgraph/templates/template-storage/src/mapping.ts).

### zkGraph Development Tips

#### Develop

* Provable program needs to be compilable and runnable in normal execution runtime first.

```typescript
// Code not compilable (due to reassign `state` which is constant)
export function handleBlocks(blocks: Block[]): Bytes {
  const state = new Bytes(0);
  state = new Bytes(0);
  return state;
}

// Code not executable or runnable (due to divide number by zero)
export function handleBlocks(blocks: Block[]): Bytes {
  const state = new Bytes(0);
  const NAN = BigInt.fromI32(0).div(0);
  return state;
}
```

* For generating proof on zkWASM, do not use io syscalls like `console` etc. `console.log(string)` (note that only `string` type is supported in AssemblyScript) should only be used in debug stage.

```typescript
export function handleBlocks(blocks: Block[]): Bytes {
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
export function handleBlocks(blocks: Block[]): Bytes {
  let state = new Bytes(0);
  if (state.length != 0) {
    throw new Error(`Invalid state length: ${state.length}, expected 0 bytes.`);
  }
  return state;
}

// 2179 lines in generated .wat file without template literal
export function handleBlocks(blocks: Block[]): Bytes {
  let state = new Bytes(0);
  if (state.length != 0) {
    throw new Error(`Invalid state length, expected 0 bytes.`);
  }
  return state;
}
```

* Try not to use keywords that may introduce extra global init code e.g. `new`, `static` etc. `changetype` is fine, [because](https://github.com/AssemblyScript/assemblyscript/issues/549#issuecomment-474005579) it just changes the type statically and does not result in any actual instructions.
* You can use third-party optimization tools (such as [wasm-opt](https://www.npmjs.com/package/wasm-opt)) to reduce WASM binary size.
