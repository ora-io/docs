# Getting Started

### Pre-requisite

#### Required

* Basic knowledge on Ethereum smart contract development
* Basic knowledge on Solidity Events (recommended readings [1](https://consensys.net/blog/developers/guide-to-events-and-logs-in-ethereum-smart-contracts/), [2](https://medium.com/mycrypto/understanding-event-logs-on-the-ethereum-blockchain-f4ae7ba50378), [3](https://thegraph.com/blog/event-driven-development-unlocking-optimized-dapps-and-subgraphs/), [4](https://mirror.xyz/spacesailor.eth/LEe2yoLoqy97BWHyO6J65XhnG8t33Nmvz\_Vsa3ve7rY)), and [Ethereum Transaction Payload](https://oxpampam.hashnode.dev/ethereum-transaction-payload-explained)

#### Optional

* [Subgraph development](https://thegraph.academy/developers/defining-a-subgraph/) experience
* AssemblyScript development experience

### Methods for Development

For the development of zkGraph, we offer two development methods:

1. zkGraph Studio on Web UI: Easy-to-use integrated web code editor and interface for zkGraph development.
2. zkGraph Template Locally: More customizable and end-to-end local scaffold for zkGraph development.

### zkGraph Development Tips

#### Develop

1. Provable program needs to be compilable and runnable in normal execution runtime first.
2. To running on zkwasm, do not use io syscalls like `console` etc.

#### Optimize

1. Look at (approximate) WASM cost for each operation! Complexer logic (eg. anything with lots of `if` or `string`) usally means more instructions, which means longer proof generation time.
2. Don't use template literals (`${}`), for example when throwing errors, because it will be compiled to too many WASM instructions (\~1000 diff).
3. Try not to use keywords that may introduce extra global init code e.g. `new`, `static` etc. (`changetype` is fine).
