---
description: https://www.hyperoracle.io/app/mvp
---

# Testing Guide

### Intro to Hyper Oracle MVP

[Hyper Oracle MVP](https://www.hyperoracle.io/app/mvp) is a pre-release of Hyper Oracle Testnet. Watch [video walkthrough of MVP](https://youtu.be/peF8AlxIIxA)!

The MVP shows how developers can write AssemblyScript code (a TypeScript variant for WebAssembly, similar to JavaScript) to perform both off-chain program execution and zk proof generation in zkWASM.

The difference between our MVP and other projects is that Hyper Oracle generates zkp for the programmable off-chain program, which trustlessly performs off-chain complex computations of on-chain data.

In the future Hyper Oracle Testnet, developers will be able to write and deploy any zkGraph via AssemblyScript to perform trustless computation with any off-chain program.

### 1. Top Up Testnet ETH Balance

In order to setup zkGraph, generate proof and deploy verification contract, one need to top up Testnet ETH first.

#### Prerequisite

* MetaMask Wallet
* Goerli Address with >0.02 ETH (Recommended)
* Sepolia Address with >0.005 ETH (Recommended)

#### Top Up Balance

Click the `Connect` button in the upper right corner of the MVP page, select `MetaMask`, confirm the connection in the wallet, and switch to the Goerli network.

After a successful connection, you will see the `Connect` button change to your address, e.g. `0x420...6969`.

Click the `0x420...6969` button in the upper right corner again. At this point, the Top Up session box will pop up.

In the text box under `ETH Amount`, enter the amount you want to deposit, 0.02 is recommended (at least 0.004). Click `Confirm` and confirm the transaction in the wallet.

{% hint style="info" %}
If balance is not updated with confirmation of transaction, click "use a transaction hash" to post it.
{% endhint %}

<figure><img src="../.gitbook/assets/截屏2023-05-30 01.44.00.png" alt=""><figcaption></figcaption></figure>

You can click on the `0x420...6969` button again to see if the `ETH Balance` has changed.

### 2. Setup zkWASM Image

A [zkGraph](https://docs.hyperoracle.io/meta-apps/zkgraph/structure) has 2 major parts: `mapping.ts` (data mapping for off-chain computation), and `zkgraph.yaml` (configuration for this zkGraph).&#x20;

In the Hyper Oracle MVP page, we can see the Code Editor at the top. There are two files `mapping.ts` and `library.ts`.&#x20;

On the right, the input boxes represent a simplified form of `zkgraph.yaml`.

The following is a more specific description of the two code files:

* `mapping.ts` is the core logic of zkGraph, defining the off-chain computational logic that will be used to run and generate proofs in zkWASM. You can modify it as you like.
* `library.ts` is the wrapping logic which should NOT be modified by default.

<figure><img src="../.gitbook/assets/截屏2023-05-15 15.59.34.png" alt=""><figcaption></figcaption></figure>

We start by clicking the light blue Start button in the upper right corner of the Code Editor. In the Code Editor file, a `mvp.wat` file will appear, which is the wat format of our compiled wasm file, and you can directly view its underlying code and other content.

Scroll down to the `< Step 1 > Setup` section, and you will see `hyper_oracle_mvp.wasm` generated under Generated String, which is the binary format of the wasm file. You can download it by clicking on it.

<figure><img src="../.gitbook/assets/截屏2023-05-15 16.01.19.png" alt=""><figcaption></figcaption></figure>

Go ahead and click the `SET UP` button in the bottom right corner, and after a while, you will see the created ZKWASM Image ID. In this step we deploy the wasm file we just generated to the Hyper Oracle prover node, for proof generation.

<figure><img src="../.gitbook/assets/截屏2023-05-15 16.27.47.png" alt=""><figcaption></figcaption></figure>

### 3. Generate Output State

Scroll down to the `< Step 2 > Execute` section. You can see that we will be executing on a specific block `0x9825...`. This step will perform pure execution and generate output state for our zkGraph.

After clicking `EXECUTE` and waiting for a while, we can see that the Output State has been updated, which means that the state of our zkGraph has been updated and the execution was successful.

<figure><img src="../.gitbook/assets/截屏2023-05-15 16.28.53.png" alt=""><figcaption></figcaption></figure>

### 4. Proof Generation

Scroll down to the `< Step 3 > Proof Generation` section. We have everything ready for zk proof generation for the zkGraph run. Click `GENERATE`, sign it in the wallet, start zk proof generation, and after a while, we can see the proof details finally being generated and confirmed.

<figure><img src="../.gitbook/assets/截屏2023-05-28 12.46.20.png" alt=""><figcaption></figcaption></figure>

You can view the zk proof directly by clicking on `View Detail`.

<div data-full-width="false">

<figure><img src="../.gitbook/assets/截屏2023-05-28 12.46.30.png" alt=""><figcaption></figcaption></figure>

</div>

### 5. Verify Proof On-chain

{% hint style="info" %}
In this step, we recommend to deploy the contract on Sepolia rather than Goerli to save gas.
{% endhint %}

Scroll down to the `< Step 4 > Verification` section. In this step, we will deploy a Verifier contract to verify zkp on the blockchain.&#x20;

After selecting the target network for deployment, click `DEPLOY` and sign it in the wallet. After some time, we can see that the Verifier Contract is successfully deployed.&#x20;

We can then click `VERIFY` to send our zk proof to the contract we just deployed for verification.

<figure><img src="../.gitbook/assets/截屏2023-05-28 12.46.42.png" alt=""><figcaption></figcaption></figure>

🎉 Congratulations on your successful completion of the Hyper Oracle MVP full test. If you have any question or comment, please feel free to contact us.
