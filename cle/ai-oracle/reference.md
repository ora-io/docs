# Reference

## Models

<table><thead><tr><th width="124">Model ID</th><th width="152">Model</th><th width="149">Fee (in ETH)</th><th width="415">Note</th></tr></thead><tbody><tr><td>9</td><td>Grok (300B)</td><td>Mainnet: 0.005</td><td>/</td></tr><tr><td>11</td><td>LlaMA 2 (7B)</td><td>Mainnet: 0.005<br>Sepolia: 0.01</td><td>/</td></tr><tr><td>50</td><td>Stable Diffusion</td><td>Mainnet: 0.005<br>Sepolia: 0.01</td><td>Return value is IPFS Hash (access with IPFS gateway, see <a href="https://ipfs.io/ipfs/QmTJGTnAHLaYSVz8xbWZBVwAWNUJSi7GKZDzkCLMHTxAXt">example</a>)</td></tr></tbody></table>

## Deployed Addresses

Prompt and SimplePrompt are both example integrated contract. SimplePrompt saves gas by only emitting the event without storing all historical data.

**Ethereum Mainnet**

| Contract     | Mainnet Address                            |
| ------------ | ------------------------------------------ |
| OAO Proxy    | 0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0 |
| OAO Logic    | 0x6d431EB9563984E5733B95521F7a672ADD8175a4 |
| Prompt       | 0xb880D47D3894D99157B52A7F869aB3B1E2D4349d |
| SimplePrompt | 0x61423153f111BCFB28dd264aBA8d9b5C452228D2 |

#### **Sepolia**

| Contract     | Sepolia Address                            |
| ------------ | ------------------------------------------ |
| OAO Proxy    | 0x0A0f4321214BB6C7811dD8a71cF587bdaF03f0A0 |
| OAO Logic    | 0xe47BC46FE676642eAED860E319363350B334236a |
| Prompt       | 0xe75af5294f4CB4a8423ef8260595a54298c7a2FB |
| SimplePrompt | 0x696c83111a49eBb94267ecf4DDF6E220D5A80129 |

Deprecated contracts: [AIOracle](https://sepolia.etherscan.io/address/0xb880D47D3894D99157B52A7F869aB3B1E2D4349d), [Prompt](https://sepolia.etherscan.io/address/0x5d6963003Ad172Fd1D2A2fD18bB3967eA7Aef1a2).
