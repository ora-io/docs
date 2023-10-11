# Develop Guide

### zkGraph Configuration (`zkgraph.yaml`)

`zkgraph.yaml` defines the configuration of zkGraph.

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

More examples can be found at [zkGraph template repo](https://github.com/hyperoracle/zkgraph/tree/master/example), and [zkUsecase repo](https://github.com/LiRiu/zkUsecase/tree/master/example).

#### Supported Networks (network)

`network` specifies the `dataSource` network for data source or `dataDestination` network for verification contract deployment or zkGraph publish.

`network` should follow the format of all lower-case letters (eg. mainnet, or goerli) with the following naming.

<table><thead><tr><th>Network (ChainID)</th><th>Name in zkgraph.yaml</th><th data-type="checkbox">dataSource</th><th data-type="checkbox">dataDestination</th></tr></thead><tbody><tr><td>Ethereum Mainnet (1)</td><td><code>mainnet</code></td><td>true</td><td>false</td></tr><tr><td>Ethereum Goerli (5)</td><td><code>goerli</code></td><td>true</td><td>true</td></tr><tr><td>Ethereum Sepolia (11155111)</td><td><code>sepolia</code></td><td>true</td><td>true</td></tr></tbody></table>

#### apiVersion

`apiVersion` specifies the `zkgraph-lib` version or any other libraries, used by a zkGraph, in Hyper Oracle Node or Hyper Oracle compiler server.

| apiVersion | zkgraph-lib Version |
| ---------- | ------------------- |
| 0.0.1      | 0.0.7               |

#### specVersion

`specVersion` specifies the `zkgraph.yaml` configuration format version, parsed by Hyper Oracle Node or other libraries.

<table><thead><tr><th>specVersion</th><th>Updated Data Fields</th><th data-type="content-ref">Example</th></tr></thead><tbody><tr><td>0.0.1</td><td>/</td><td><a href="https://github.com/hyperoracle/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml">https://github.com/hyperoracle/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml</a></td></tr></tbody></table>

### zkGraph Development Tips

#### Develop

1. Provable program needs to be compilable and runnable in normal execution runtime first.
2. To running on zkwasm, do not use io syscalls like `console` etc.

#### Optimize

1. Look at (approximate) WASM cost for each operation! More complex logic (eg. anything with lots of `if` statements or `string`) usally means more instructions, which means longer proof generation time.
2. Don't use template literals (`${}`), for example when throwing errors, because it will be compiled to too many WASM instructions (\~1000 diff).
3. Try not to use keywords that may introduce extra global init code e.g. `new`, `static` etc. (`changetype` is fine).
4. You can use third-party optimization tools (such as [wasm-opt](https://www.npmjs.com/package/wasm-opt)) to reduce WASM binary size.
