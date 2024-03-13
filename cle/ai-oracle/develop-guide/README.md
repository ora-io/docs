# Develop Guide

## Source Code

OAO: [https://github.com/ora-io/OAO](https://github.com/ora-io/OAO)

## Supported Models

<table><thead><tr><th width="124">Model ID</th><th width="152">Model</th><th>Return Value</th></tr></thead><tbody><tr><td>11</td><td>LlaMA 2</td><td>Text</td></tr><tr><td>50</td><td>Stable Diffusion</td><td>IPFS Hash (access it with IPFS gateway, see <a href="https://ipfs.io/ipfs/QmTJGTnAHLaYSVz8xbWZBVwAWNUJSi7GKZDzkCLMHTxAXt">example</a>)</td></tr></tbody></table>

## Contract Addresses

<table><thead><tr><th width="287">Contract</th><th width="440">Address</th><th>Archive Address</th></tr></thead><tbody><tr><td>AIOracle</td><td>Sepolia: <a href="https://sepolia.etherscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td><td><a href="https://sepolia.etherscan.io/address/0xb880D47D3894D99157B52A7F869aB3B1E2D4349d">259f94e</a></td></tr><tr><td><p>Prompt</p><p>(example usage contract)</p></td><td>Sepolia: <a href="https://sepolia.etherscan.io/address/0x64BF816c3b90861a489A8eDf3FEA277cE1Fa0E82">0x64BF816c3b90861a489A8eDf3FEA277cE1Fa0E82</a></td><td><a href="https://sepolia.etherscan.io/address/0x5d6963003Ad172Fd1D2A2fD18bB3967eA7Aef1a2">259f94e</a></td></tr></tbody></table>

## Workflow

1. The user contract sends the AI request to OAO on chain, by calling `requestCallback` function on the OAO contract.
2. Each AI request will initiate an opML request.
3. OAO will emit a `requestCallback` event which will be collected by opML node.
4. opML node will run the AI inference, and then upload the result on chain, waiting for the challenge period.
   1. During the challenge period, the opML validators will check the result, and challenge it if the submitted result is incorrect.
   2. If the submitted result is successfully challenged by one of the validators, the submitted result will be updated on chain.
   3. After the challenge period, the submitted result on chain is finalized.
5. When the result is uploaded or updated on chain, the provided result in opML will be dispatched to the user's smart contract via its specific callback function.

## Integration

### Overview

To integrate with OAO, you will need to write your own contract.

To build with AI models of OAO, we provided an example of integration to LlaMA2 model: [Prompt](https://sepolia.etherscan.io/address/0x3E774275c7761CFb781715A47cAE694BA9dEb44A).

### Fee

Usage of OAO requires fee for each request.

It is required to obtain the current fee by calling `estimateFee` in OAO or your usage contract with specific model id, then proceed to send request.

Flow of getting and setting fee is:

1. Call to read `estimateFee` (on OAO or your contract if implemented) for inference with certain model
2. Get estimated fee in wei (eg. [21300788080000000](https://sepolia.etherscan.io/unitconverter?wei=21300788080000000))
3. Call to write and request AI inference on your contract, and fill in estimated fee in ether (eg. [0.02130078808](https://sepolia.etherscan.io/unitconverter?wei=21300788080000000))
