---
description: ⚠️Ongoing Experimental Design⚠️
---

# Develop

## Create zkGraph

### Install `graph-cli`&#x20;

```bash
# NPM
npm install -g @graphprotocol/graph-cli

# Yarn
yarn global add @graphprotocol/graph-cli
```

### Create new zkGraph

#### Option 1 (Recommended): New zkGraph that indexes all events of an existing contract.

```bash
graph init \
  --product zkgraph-studio
  --from-contract <CONTRACT_ADDRESS> \
  [--network <ETHEREUM_NETWORK>] \
  [--abi <FILE>] \
  <ZKGRAPH_ID> [<DIRECTORY>]
```

`<FILE>` is a fallback for local contract ABI file path if ABI cannot be fetched from Etherscan.

#### Option 2: New zkGraph from scratch.

```bash
graph init --studio <ZKGRAPH_ID>
```

## Develop zkGraph

### zkGraph Manifest

`zkgraph.yaml` defines information including data source, Meta Apps used, target blockchain network, and target smart contract.

#### Add new data source

Add new data source to existing zkGraph manifest

```bash
graph add <address> [<zkgraph-manifest default: "./zkgraph.yaml">]
Options:
      --abi <path>           Path to the contract ABI (default: download from Etherscan)
      --contract-name        Name of the contract (default: Contract)
      --merge-entities       Whether to merge entities with the same name (default: false)
      --network-file <path>  Networks config file path (default: "./networks.json")
```

#### Example `zkgraph.yaml` using zkIndexing:

```yaml
specVersion: 0.0.2
description: Indexing the Real Time ETH Price in USDC based on the UniswapV2 USDC-ETH Pool.
repository: https://github.com/hyperoracle/zkgraph
dataSources:
  - kind: ethereum/contract
    network: mainnet
    source:
      address: '0xb4e16d0168e52d35cacd2c6185b44281ec28c9dc'
      startBlock: 16317568
    mapping:
      kind: ethereum/events
      apiVersion: 0.0.1
      language: wasm/assemblyscript
      file: ./mapping.ts
      eventHandlers:
        - event: Sync(uint112,uint112)
          handler: handleEvent
```

### zkGraph Mapping

zkGraph mappings take data from a source and transform it into entities that you defined. Mappings are written in a subset of [TypeScript](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html) with stricter syntax called [AssemblyScript](https://github.com/AssemblyScript/assemblyscript/wiki) which can be compiled to WASM.

For zkGraph using zkIndexing, mapping is called `mapping.ts` because it transforms data into GraphQL entities for indexing.

For zkGraph using zkAutomation, mapping is called `automation.ts` because it defines trigger condition and automation job.

#### Example `mapping.ts` using zkIndexing:

```typescript
import { Bytes } from "../sdk/type";
export function handleEvent(esig: Uint8Array, topic1: Uint8Array, topic2: Uint8Array, topic3: Uint8Array, data: Uint8Array): Uint8Array {
    var source = changetype<Bytes>(data);
    let reserve0 = source.slice(31, 32);
    let reserve1 = source.slice(63, 64);

    let state = Bytes.new(32);
    state[31] = reserve0.toU32() / reserve1.toU32();
    return state as Uint8Array;
}
```

#### Example `automation.ts` using zkAutomation:

```typescript
import { BigInt } from "as-bigint";
import { Event, GraphState, Bytes32, Bytes } from "../type";

var trigger_price_threshold = BigInt.fromInt16(200);
export function handleEvent(event: Event, pre_state: GraphState = 0): GraphState{
    var next_state: GraphState;
    if (event.topics[0] == Bytes32.fromHex(esig_sync)){
        var reserve0 = Bytes.fromUint8Array(event.data.data.slice(0,32)).toBigInt()
        var reserve1 = Bytes.fromUint8Array(event.data.data.slice(32)).toBigInt()

        var price = reserve0.mul(1000).div(reserve1);
        var is_trigger;
        var payload;
        if (price > trigger_price_threshold.mul(1000)){
            is_trigger = 1;
            payload = price.toInt32();
        } else {
            is_trigger = 0;
            payload = 0;
        }
        next_state = changetype<GraphState>(is_trigger<<255 & payload);

    } else { // not possible
        next_state = pre_state
    }
    return next_state;
}
```
