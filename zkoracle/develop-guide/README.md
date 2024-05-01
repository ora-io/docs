---
description: Guide on coding CLE.
---

# Develop Guide

## Pre-requisites

#### Required

* Basic knowledge of Ethereum smart contract development ([tutorials](https://ethereum.org/en/developers/tutorials/))
* Basic knowledge of Ethereum Architecture ([State Trie](https://medium.com/@eiki1212/ethereum-state-trie-architecture-explained-a30237009d4e)), Solidity Events (recommended readings [1](https://consensys.net/blog/developers/guide-to-events-and-logs-in-ethereum-smart-contracts/), [2](https://medium.com/mycrypto/understanding-event-logs-on-the-ethereum-blockchain-f4ae7ba50378), [3](https://thegraph.com/blog/event-driven-development-unlocking-optimized-dapps-and-subgraphs/), [4](https://mirror.xyz/spacesailor.eth/LEe2yoLoqy97BWHyO6J65XhnG8t33Nmvz\_Vsa3ve7rY)), Contract Storage (recommended reading [1](https://docs.soliditylang.org/en/v0.8.17/internals/layout\_in\_storage.html), [2](https://degatchi.com/articles/low\_level\_guide\_to\_soliditys\_storage\_management)), Ethereum Transaction ([Calldata](https://www.quicknode.com/guides/ethereum-development/transactions/ethereum-transaction-calldata), [Payload](https://oxpampam.hashnode.dev/ethereum-transaction-payload-explained), [Difference](https://ethereum.stackexchange.com/questions/127048/calldata-and-payload-for-multiple-calls))

#### Optional

* Subgraph development experience ([tutorial](https://thegraph.academy/developers/defining-a-subgraph/))
* AssemblyScript development experience ([book](https://www.assemblyscript.org/concepts.html))

## Methods for Development

For the development of a CLE, we offer two development methods:

1. [CLE Studio on Web UI](getting-started/1.-zkgraph-studio-ui.md) (🐣 INTRODUCTORY): Easy-to-use integrated web code editor and interface for experiencing CLE development for the first time.
2. [CLE Scaffold](getting-started/2.-zkgraph-scaffold.md) (✨ RECOMMENDED): More customizable and end-to-end scaffold for CLE development.

## Resources

Example zkOracle CLEs can be found as [templates of CLE scaffold](https://github.com/ora-io/cle-cli/tree/main/packages/create-zkgraph/templates).

## Quickstart

### CLE Configuration (`cle.yaml`)

`cle.yaml` defines the configuration of a CLE.

It specifies information including:

* data source
* target blockchain network
* target smart contract address
* target event
* event handler

An example of `cle.yaml`:

```yaml
specVersion: 0.0.2
apiVersion: 0.0.2
name: eg_event
description: "This demo cle shows 3 ways to access / filter out source events."
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

More examples can be found as [templates of CLE scaffold](https://github.com/ora-io/cle-cli/tree/main/packages/create-zkgraph/templates).

#### Supported `network` with Features

`network` specifies the `dataSource` network for data source or `dataDestination` network for verification contract deployment and CLE publish.

`network` should follow the format of all lower-case letters (eg. mainnet, or goerli) with the following naming.

<table data-full-width="false"><thead><tr><th width="191">Network (ChainID)</th><th width="148">Name in YAML</th><th width="191">dataSource</th><th width="156">dataDestination</th><th width="194">CLE Deployment</th></tr></thead><tbody><tr><td><p>Ethereum Mainnet</p><p>(1)</p></td><td><code>mainnet</code></td><td>✅ <br>(<code>handleBlocks</code>)</td><td>❌</td><td>❌</td></tr><tr><td><p>Ethereum Goerli</p><p>(5)</p></td><td><code>goerli</code></td><td>✅ <br>(<code>handleBlocks</code>)</td><td>❌</td><td>❌</td></tr><tr><td><p>Ethereum Sepolia</p><p>(11155111)</p></td><td><code>sepolia</code></td><td>✅ <br>(<code>handleBlocks</code>)</td><td>✅</td><td>✅</td></tr></tbody></table>

#### `apiVersion`

`apiVersion` specifies the `cle-lib` version or any other libraries, used by a CLE, in ZK Oracle including CLE compiler.

<table><thead><tr><th width="132">apiVersion</th><th width="186.33333333333331">cle-lib Version</th><th>Notes</th></tr></thead><tbody><tr><td>0.0.1</td><td>0.0.8</td><td>Added <code>event</code> as data source, multi-address and multi-sources for data source.</td></tr><tr><td>0.0.2</td><td>1.0.0</td><td>Updated <code>block</code> as data source, <code>block</code> contains both <code>event</code> and <code>account</code> data.</td></tr></tbody></table>

#### specVersion

`specVersion` specifies the `cle.yaml` configuration format version, parsed by ORA Node or other libraries.

<table><thead><tr><th width="147.33333333333331">specVersion</th><th width="274">Updated Data Fields</th><th data-type="content-ref">Example</th></tr></thead><tbody><tr><td>0.0.1</td><td>/</td><td><a href="https://github.com/ora-io/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml">https://github.com/ora-io/zkgraph/blob/4329897bf502ecf8cc36ecac8d39df75bf3b8f8f/src/zkgraph.yaml</a></td></tr><tr><td>0.0.2</td><td><code>apiVersion</code>, <code>dataSources</code>, <code>mapping</code></td><td><a href="https://github.com/ora-io/cle-cli/blob/abfbb9b33e91099b1f4b791aefe2bf7decc05741/packages/create-zkgraph/templates/template-event/src/zkgraph.yaml">https://github.com/ora-io/cle-cli/blob/abfbb9b33e91099b1f4b791aefe2bf7decc05741/packages/create-zkgraph/templates/template-event/src/zkgraph.yaml</a></td></tr></tbody></table>

### CLE Mapping (`mapping.ts`)

A required function for CLE mapping is `handleBlocks`.

The `mapping.ts` with `handleBlocks` should be structured as follows, and should not be modified in most cases:

```typescript
// imports
import { require, Bytes, Event, BigInt } from "@ora-io/cle-lib";
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

* **Function definition of required function must be** `function handleBlocks(blocks: Block[]): Bytes`**.**
* **Return value of required function must be** `Bytes`**.** The best practice is to set it as [a payload / calldata](getting-started/#pre-requisites), so that it can be used with [ZK Automation](../zkoracle-standards/zkautomation/) directly.

#### Access `Event` Data

1. Define specific contract address and events in `cle.yaml`.
2. Access specific events in `mapping.ts` `handleBlocks()`, after `cle.yaml`'s filtering.

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

1. Define specific storage address and slots in `cle.yaml`.
2. Access specific slots in `mapping.ts` `handleBlocks()`, after `cle.yaml`'s filtering.

```typescript
// get source Account object by address
let acct: Account = blocks[0].account(addr);
  
// Option #1: access source Slot value by key
let slotValue: Bytes = acct.storage(key);

// Option #2: access source Slot object by key
let slot: Slot = acct.slots[acct.getSlotId(key)];
```

See [full example here](https://github.com/hyperoracle/zkgraph-cli/blob/d624dcb03d0d916f08bf3b2970c69b034ec753a3/packages/create-zkgraph/templates/template-storage/src/mapping.ts).
