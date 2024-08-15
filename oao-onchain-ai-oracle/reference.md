---
description: Supported AI Models and Deployment Addresses of Onchain AI Oracle.
---

# Reference

## Models

#### [Llama3 8B Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct)

<table data-full-width="true"><thead><tr><th width="130"></th><th>Llama3 8B Instruct</th></tr></thead><tbody><tr><td>Model ID</td><td>11</td></tr><tr><td>Deployed Network</td><td>Ethereum &#x26; Ethereum Sepolia, Optimism &#x26; Optimism Sepolia, Arbitrum &#x26; Arbitrum Sepolia, Manta &#x26; Manta Sepolia, Linea, Base, Mantle, Polygon PoS</td></tr><tr><td>Fee</td><td>Mainnet: 0.0003 ETH / 3 MATIC / 3 MNT<br>Testnet: 0.01 ETH</td></tr><tr><td>Usage</td><td>Input: Prompt (<a href="https://etherscan.io/tx/0xa2e4af640c8aed49b689ac47d46534c7e1854212b3cb877f4bc2c55f3c6c04d5">example tx</a>).<br>Output: Inference result (<a href="https://etherscan.io/tx/0x738e20692c6159f3ebe4eb993b007dd6da26b2db15ecb97d2994d64741b547a3">example tx</a>).</td></tr></tbody></table>

#### [OpenLM 1B](https://github.com/mlfoundations/open\_lm)

<table data-full-width="true"><thead><tr><th width="130"></th><th>OpenLM 1B</th></tr></thead><tbody><tr><td>Model ID</td><td>13</td></tr><tr><td>Deployed Network</td><td>Ethereum &#x26; Ethereum Sepolia</td></tr><tr><td>Fee</td><td>Mainnet: 0.0003 ETH<br>Testnet: 0.01 ETH</td></tr><tr><td>Usage</td><td>Input: Prompt (<a href="https://etherscan.io/tx/0x307d219dfd91fd77e92e0e199be54feda5eaa8ffd426ac592a069190f8038c72">example tx</a>).<br>Output: Inference result (<a href="https://etherscan.io/tx/0xc72bed0224607dbf967a424de6ef09bdff8b65e08df4a7cd3149cd607e63ba79">example tx</a>).</td></tr></tbody></table>

#### [OpenLM Score 7B](https://huggingface.co/OLMResearch/olm-score-7b), aka. (A.I.)location Oracle

<table data-full-width="true"><thead><tr><th width="130"></th><th>OpenLM Score 7B, aka. (A.I.)location Oracle</th></tr></thead><tbody><tr><td>Model ID</td><td>14</td></tr><tr><td>Deployed Network</td><td>Arbitrum &#x26; Arbitrum Sepolia, Ethereum Sepolia</td></tr><tr><td>Fee</td><td>Mainnet: 0.0003 ETH<br>Testnet: 0.01 ETH</td></tr><tr><td>Usage</td><td>Input: Instruction and prompt with the format of JSON String: <code>{"instruction":"${instruction}","input":"${prompt}"}</code> (<a href="https://arbiscan.io/tx/0x26fe26d3cee4aae650cb40718592e42969a84862620ff69a03cf23fafb8391ec">example tx</a>). Default instruction (if sending raw prompt only) is <code>You are a helpful assistant</code>.<br>Output: Inference result (<a href="https://arbiscan.io/tx/0xe9e0a45d0f263ec010ff60e508d8b1acb49216223ced21c8d5d6d46aa94a40b1">example tx</a>).</td></tr></tbody></table>

#### [OpenLM Chat 7B](https://huggingface.co/OLMResearch/olm-chat-7b)

<table data-full-width="true"><thead><tr><th width="130"></th><th>OpenLM Score 7B, aka. (A.I.)location Oracle</th></tr></thead><tbody><tr><td>Model ID</td><td>15</td></tr><tr><td>Deployed Network</td><td>Arbitrum &#x26; Arbitrum Sepolia, Ethereum Sepolia</td></tr><tr><td>Fee</td><td>Mainnet: 0.0003 ETH<br>Testnet: 0.01 ETH</td></tr><tr><td>Usage</td><td>Input: Instruction and prompt with the format of JSON String: <code>{"instruction":"${instruction}","input":"${prompt}"}</code> (<a href="https://arbiscan.io/tx/0x29aef16c9eb5e9233e9ece7ff68043b247a1bc42a39d132e340f9eb0d332d13c">example tx</a>). Default instruction (if sending raw prompt only) is <code>You are a helpful assistant</code>.<br>Output: Inference result (<a href="https://arbiscan.io/tx/0x3b242919ea952400ca7240ddc8f9976aede2c0b77a039f89ba71f707112b5d47">example tx</a>).</td></tr></tbody></table>

#### [Stable Diffusion](https://huggingface.co/CompVis/stable-diffusion-v1-4)

<table data-full-width="true"><thead><tr><th width="130"></th><th>Stable Diffusion</th></tr></thead><tbody><tr><td>Model ID</td><td>50</td></tr><tr><td>Deployed Network</td><td>Ethereum &#x26; Ethereum Sepolia, Optimism &#x26; Optimism Sepolia, Arbitrum &#x26; Arbitrum Sepolia, Manta &#x26; Manta Sepolia, Linea, Base, Mantle, Polygon PoS</td></tr><tr><td>Fee</td><td>Mainnet: 0.0003 ETH / 3 MATIC / 3 MNT<br>Testnet: 0.01 ETH</td></tr><tr><td>Usage</td><td>Input: Prompt (<a href="https://etherscan.io/tx/0x7fc0e6cb44d6a450b5b1cb5fc5e7ea64f6c8f7b60052f3fba5eae1ea3edd2ff7">example tx</a>).<br>Output: IPFS hash of inference result (<a href="https://etherscan.io/tx/0xf1dec4934204edde2f8ba1957ae4e97df56c2a55e55eec7efb8831a1bcf68e60">example tx</a>). Access with IPFS gateway, see <a href="https://ipfs.io/ipfs/QmTJGTnAHLaYSVz8xbWZBVwAWNUJSi7GKZDzkCLMHTxAXt">example</a>.</td></tr></tbody></table>

## Deployed Addresses

[Prompt](https://github.com/ora-io/OAO/blob/main/contracts/Prompt.sol) and [SimplePrompt](https://github.com/ora-io/OAO/blob/main/contracts/SimplePrompt.sol) are both example smart contracts interacted with OAO.

For simpler application scenarios (eg. Prompt Engineering based AI like GPTs), you can directly use Prompt or SimplePrompt.

SimplePrompt saves gas by only emitting the event without storing historical data.

**Ethereum Mainnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://etherscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://etherscan.io/address/0xb880D47D3894D99157B52A7F869aB3B1E2D4349d">0xb880D47D3894D99157B52A7F869aB3B1E2D4349d</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://etherscan.io/address/0x61423153f111BCFB28dd264aBA8d9b5C452228D2">0x61423153f111BCFB28dd264aBA8d9b5C452228D2</a></td></tr></tbody></table>

#### **Ethereum Sepolia**

<table data-view="cards"><thead><tr><th>Contract</th><th>Sepolia Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://sepolia.etherscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://sepolia.etherscan.io/address/0xe75af5294f4CB4a8423ef8260595a54298c7a2FB">0xe75af5294f4CB4a8423ef8260595a54298c7a2FB</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://sepolia.etherscan.io/address/0x696c83111a49eBb94267ecf4DDF6E220D5A80129">0x696c83111a49eBb94267ecf4DDF6E220D5A80129</a></td></tr></tbody></table>

Deprecated contracts: [AIOracle](https://sepolia.etherscan.io/address/0xb880D47D3894D99157B52A7F869aB3B1E2D4349d), [Prompt](https://sepolia.etherscan.io/address/0x5d6963003Ad172Fd1D2A2fD18bB3967eA7Aef1a2).

**Optimism Mainnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://optimistic.etherscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://optimistic.etherscan.io/address/0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD">0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://optimistic.etherscan.io/address/0xBC24514E541d5CBAAC1DD155187A171a593e5CF6">0xBC24514E541d5CBAAC1DD155187A171a593e5CF6</a></td></tr></tbody></table>

**Optimism Sepolia**

<table data-view="cards"><thead><tr><th>Contract</th><th>Sepolia Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://sepolia-optimism.etherscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://sepolia-optimism.etherscan.io/address/0x3c8Cd1714AC9c380702D160BE4cee0D291Eb89C0">0x3c8Cd1714AC9c380702D160BE4cee0D291Eb89C0</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://sepolia-optimism.etherscan.io/address/0xf6919ebb1bFdD282c4edc386bFE3Dea1a1D8AC16">0xf6919ebb1bFdD282c4edc386bFE3Dea1a1D8AC16</a></td></tr></tbody></table>

**Arbitrum Mainnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://arbiscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://arbiscan.io/address/0xC20DeDbE8642b77EfDb4372915947c87b7a526bD">0xC20DeDbE8642b77EfDb4372915947c87b7a526bD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://arbiscan.io/address/0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD">0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD</a></td></tr></tbody></table>

**Arbitrum Sepolia Testnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Testnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://sepolia.arbiscan.io/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://sepolia.arbiscan.io/address/0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD">0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://sepolia.arbiscan.io/address/0xBC24514E541d5CBAAC1DD155187A171a593e5CF6">0xBC24514E541d5CBAAC1DD155187A171a593e5CF6</a></td></tr></tbody></table>

**Manta Mainnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://pacific-explorer.manta.network/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://pacific-explorer.manta.network/address/0xBC24514E541d5CBAAC1DD155187A171a593e5CF6">0xBC24514E541d5CBAAC1DD155187A171a593e5CF6</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://pacific-explorer.manta.network/address/0x523622DfEd0243B0DF80CC9275764B0f432D33E3">0x523622DfEd0243B0DF80CC9275764B0f432D33E3</a></td></tr></tbody></table>

**Manta Sepolia Testnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Testnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://pacific-explorer.sepolia-testnet.manta.network/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://pacific-explorer.sepolia-testnet.manta.network/address/0xC20DeDbE8642b77EfDb4372915947c87b7a526bD">0xC20DeDbE8642b77EfDb4372915947c87b7a526bD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://pacific-explorer.sepolia-testnet.manta.network/address/0x3bfD1Cc919bfeC7795b600E764aDa001b58f122a">0x3bfD1Cc919bfeC7795b600E764aDa001b58f122a</a></td></tr></tbody></table>

**Linea Mainnet**

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://lineascan.build/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://lineascan.build/address/0xC20DeDbE8642b77EfDb4372915947c87b7a526bD">0xC20DeDbE8642b77EfDb4372915947c87b7a526bD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://lineascan.build/address/0xb880D47D3894D99157B52A7F869aB3B1E2D4349d">0xb880D47D3894D99157B52A7F869aB3B1E2D4349d</a></td></tr></tbody></table>

#### Base Mainnet

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://basescan.org/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://basescan.org/address/0xC20DeDbE8642b77EfDb4372915947c87b7a526bD">0xC20DeDbE8642b77EfDb4372915947c87b7a526bD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://basescan.org/address/0xc3287bdef03b925a7c7f54791edadcd88e632ccd">0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD</a></td></tr></tbody></table>

#### Polygon PoS Mainnet

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://polygonscan.com/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://polygonscan.com/address/0xC20DeDbE8642b77EfDb4372915947c87b7a526bD">0xC20DeDbE8642b77EfDb4372915947c87b7a526bD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://polygonscan.com/address/0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD">0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD</a></td></tr></tbody></table>

#### Mantle Mainnet

<table data-view="cards"><thead><tr><th>Contract</th><th>Mainnet Address</th></tr></thead><tbody><tr><td>OAO Proxy</td><td><a href="https://explorer.mantle.xyz/address/0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0">0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0</a></td></tr><tr><td>Prompt</td><td><a href="https://explorer.mantle.xyz/address/0xC20DeDbE8642b77EfDb4372915947c87b7a526bD">0xC20DeDbE8642b77EfDb4372915947c87b7a526bD</a></td></tr><tr><td>SimplePrompt</td><td><a href="https://explorer.mantle.xyz/address/0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD">0xC3287BDEF03b925A7C7f54791EDADCD88e632CcD</a></td></tr></tbody></table>
