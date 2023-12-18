# User Guide

If you want your zkGraph to use zkAutomation, then you need to make two changes to the zkGraph and set Bounty when deploying:

#### 1. Set dataDestinations in `zkgraph.yaml`

In a zkGraph that uses zkAutomation, you need to first define the onchain smart contract that will be called when automation should be triggered.

For example:

```yaml
specVersion: 0.0.2
apiVersion: 0.0.2
# ...

dataSources:
# ...

# dataDestinations field with valid contract address is required for zkAutomation.
dataDestinations:
  - kind: ethereum
    network: sepolia
    address: "0xdeadbeef000000000000000000000000000000000"
```

Note that if you don't need to use zkAutomation, you don't need to set dataDestinations or just set the address to be something like burner address.

#### 2. Return Payload (Calldata) in `mapping.ts`

In the previous step, we have defined the blockchain network triggered by automation and the smart contract.

The role of mapping.ts:

* **Determining whether automation needs to triggered**: When `handleBlocks` does not return a value (eg. exit due to false condition in `require`), the automation does not need to be triggered.
* **Setting the payload (calldata) for the trigger:** when `handleBlocks` returns value, the automation needs to be triggered, and the return value is used as the payload (calldata) for the call. If you are confused about these concepts, please check [introduction page of zkGraph](../../zkgraph/introduction.md).

For example:

This zkGraph's zkAutomation will never be triggered.

```typescript
export function handleBlocks(blocks: Block[]): Bytes {
  // Always exit at this line.
  require(false);
  return Bytes.empty();
}
```

This zkGraph's zkAutomation will always be triggered, and function of `run()` will be [called](https://sepolia.etherscan.io/tx/0x4f0c30fa489989d679acefa9fdaf7022d4a12c35eab9494a3b4eceb44006d8af).

```typescript
export function handleEvents(blocks: Block[]): Bytes {
  // run() func signature           - c0406226
  // zkAuto call input data onchain - 0xc0406226
  return Bytes.fromHexString("c0406226").padEnd(32);
}
```

#### 3. Set Bounty when Publishing

Since each proof generation and onchain call (including verification and later calls to `dataDestinations`) consumes fund, we set up the Bounty mechanism.

Bounty mechanism means that the user of zkAutomation will deposit the bounty into our contract in advance, and set the amount of bounty that the zkOracle node can draw from each time zkAutomation is triggered at the time of deployment.

Currently in the testnet phase, you just need to set the `bounty_reward_per_trigger` when publishing zkGraph:

```bash
# Publish Command in zkGraph CLI
zkgraph publish <ipfs_hash> <bounty_reward_per_trigger>
```
