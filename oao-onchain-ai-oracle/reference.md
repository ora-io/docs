# Reference

## Models

<table data-full-width="false"><thead><tr><th width="125">Model ID</th><th width="165">Model</th><th width="203">Fee</th><th>Deployed Network</th></tr></thead><tbody><tr><td>11</td><td>LlaMA 3 (8B)</td><td>Mainnet: 0.0003 ETH / 3 MATIC<br>Testnet: 0.01 ETH</td><td>Ethereum &#x26; Ethereum Sepolia, Optimism &#x26; Optimism Sepolia, Arbitrum &#x26; Arbitrum Sepolia, Manta &#x26; Manta Sepolia, Linea, Base, Mantle</td></tr><tr><td>13</td><td>OpenLM (1B)</td><td>Mainnet: 0.0003 ETH<br>Testnet: 0.01 ETH</td><td>Ethereum &#x26; Ethereum Sepolia</td></tr><tr><td>14</td><td>OpenLM Score (7B)*</td><td>Mainnet: 0.0003 ETH<br>Testnet: 0.01 ETH</td><td>Arbitrum &#x26; Arbitrum Sepolia, Ethereum Sepolia</td></tr><tr><td>15</td><td>OpenLM Chat (7B)*</td><td>Mainnet: 0.0003 ETH<br>Testnet: 0.01 ETH</td><td>Arbitrum &#x26; Arbitrum Sepolia, Ethereum Sepolia</td></tr><tr><td>50</td><td>Stable Diffusion**</td><td>Mainnet: 0.0003 ETH / 3 MATIC<br>Testnet: 0.01 ETH</td><td>Ethereum &#x26; Ethereum Sepolia, Optimism &#x26; Optimism Sepolia, Arbitrum &#x26; Arbitrum Sepolia, Manta &#x26; Manta Sepolia, Linea, Base, Mantle</td></tr></tbody></table>

\*:\
Prompt is with the format of JSON String: `{"instruction":"${instruction}","input":"${prompt}"}`. See [example](https://sepolia.etherscan.io/tx/0x45c32b649e8a3c4b0a8fc419514cf166683ffa92cb89bf534834c058559ec367#eventlog).\
Default instruction (if sending raw prompt only) is `You are a helpful assistant.`

\*\*:\
Return value is IPFS Hash (access with IPFS gateway, see [example](https://ipfs.io/ipfs/QmTJGTnAHLaYSVz8xbWZBVwAWNUJSi7GKZDzkCLMHTxAXt)).

## Deployed Addresses

[Prompt](https://github.com/ora-io/OAO/blob/main/contracts/Prompt.sol) and [SimplePrompt](https://github.com/ora-io/OAO/blob/main/contracts/SimplePrompt.sol) are both example smart contracts interacted with OAO.

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
