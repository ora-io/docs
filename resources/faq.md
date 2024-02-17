---
description: Frequently Asked Questions
---

# FAQ

### Why are indexing and automation considered oracles?

Our [framing of oracles](https://ethresear.ch/t/defining-zkoracle-for-ethereum/15131) categorizes oracles into three different types: input oracle (price feeds for example, inputs off-chain data to on-chain), output oracle (indexing, outputs on-chain data to off-chain), and I/O oracle (automation, output oracle + input oracle, outputs on-chain data to off-chain then computes and feeds result back to on-chain).

Our zkOracle CLE Standards (Meta Apps) are output zkOracle and I/O zkOracle.

### Why zkWASM, not zkEVM?

We want to support AssemblyScript code of zkOracle CLE for Subgraph-equivalence. This will power our ecosystem with the existing one of Subgraph. What zkEVM does is similar: support existing codes of EVM with EVM-equivalence and EVM-compatibility.

### What are security mechanisms for other zkOracle networks?

First, traditional oracle networks are mostly based on "PoS". [PoS in oracle networks is always insecure](https://mirror.xyz/hyperoracleblog.eth/RA-c\_9ydwKhSo-KV2Ti5Fu4YwThxSTQuBrlLX1\_huFw).

Output oracles such as The Graph have fisherman mechanism ([doc](https://thegraph.com/docs/en/network/indexing/#what-are-disputes-and-where-can-i-view-them), [code](https://github.com/graphprotocol/contracts/blob/dev/contracts/disputes/DisputeManager.sol)). It is kind of like Optimistic Rollups' fault/fraud proof, but without verifiability and decentralization. How it works is that during a week-long dispute period, someone can stake their token to challenge the computation (indexing or querying) and result of a node operator (indexer), and arbitrator council decides if challenge gets accepted.

I/O oracles such as Gelato Network and Keep3r Network have governance for security. Some of them are [not permissionless](https://docs.gelato.network/introduction/executor-operators#who-can-become-an-executor) now and requires legal bindings for operating a node. The networks with [governance as security mechanism](https://docs.keep3r.network/roles/governance) requires someone to challenge a node operator (executor) on their governance platform (usually a forum) and members will manually examine the challenge.

### Is zk necessary for an oracle network?

Yes.

We believe the advancement in zk technology will drive down the cost of compute power and time required for proof generation to make zkOracle network desirable. We believe a fully trustless, decentralized, secure, and verifiabe oracle network as middleware for DApps is vital. If one component is centralized, the whole DApp is just a App with smart contract.

### Is ORA a rollup or layer 2?

Neither.

ORA is verifiable oracle protocol. ORA network looks like a "layer 2" on a typical blockchain network. However, it doesn't scale smart contracts' computation, but extends smart contracts' features. An actual rollup requires [a bridge](https://drive.google.com/file/d/1KOEKNDGLBiLbaUDnIxCV6L1aBJblGPJs/view) or [an aggregator](https://www.youtube.com/watch?v=NKQz9jU0ftg).

### Is ORA zkOracle "zk" (with privacy) or "validity"?

Validity, for now.

Given that oracle often operates for public computation and handles public data for blockchains, it may not be necessary to add a private layer on validity. We may explore privacy in some future use cases.&#x20;

### What computation in ORA zkOracle is secured by zk?

The whole pipeline of zkOracle.

Data source accessing is secured by zkPoS, and off-chain computation is secured by zkWASM.

### How data source of zkOracle is secured since zk are only safeguarding computation?

On-chain data.

The computation is secured by zk, but data source cannot be guaranteed to be safe only by zk. If we use any kind of data from any source, this may break the security of zkOracle even though computation is  valid. On-chain data is already verified and secured by the base layer blockchain. That's why we are only developing output zkOracle and I/O zkOracle.

### Is ORA "adding new features" to existing oracles, or "rebuilding and replacing"?

Rebuilding and replacing.

We are the first and your last oracle.

### Who will need ORA zkOracle CLE Standards?

All Web3 developers.

All developers that need to handle blockchain data and interact with smart contract will need ORA CLE Standards. Especially, developers value decentralization and performance will choose ORA CLE Standards than other oracle networks.

### What is the zk tech stack of ORA zkOracle?

Halo2 PSE and UltraPLONK.

More details can be found in our Github.

### Will ORA do Input zkOracle?

Yes.

We may experiment with input zkOracles such as zkML in the future.

### What will be the economic design for ORA Network?

Currently, it is not final.

But our idea is that the whole economic model should be simple enough, not a system that is difficult to understand through various [complex mechanisms](https://twitter.com/matthuang/status/1638359675258421248). Compared to similar oracle networks, we will remove some unnecessary "added to maintain the token price" mechanisms, while our zk mechanism is essentially replacing the unnecessary staking mechanism in oracle networks. Our final model will probably be like PoW's Ethereum or Aleo.

### Is ORA network permissionless?

Yes.

In the future, anyone will be able to run a ORA zkOracle node. In the meantime, we will make technical and architectural efforts to make the hardware requirements to run the node even lower, even running a prover in the web.

### Is ORA a oracle?

Yes.

ORA is the verifiable oracle protocol.

### Does cost of using ORA zkOracle CLE Standards higher than other oracle services without zk?

Overall, lower sometimes; in terms of unit calculations, slightly higher.

Overall, each CLE requires only one zkOracle node to ensure security, while other oracle networks require a very large number of nodes to ensure computational validity with these redundancies. Therefore, on the whole system, only 1 node is needed for the overhead of the whole service without considering the overall robustness, uptime, and performance improvement.

If the calculation is based on each index or query, then there is always an additional proof generation cost for each calculation. However, in the case of the zkEVM Rollup, these premiums are evened out, ending up with an additional $0.0...N per computed proof. In addition, some proof generation results can be shared, such as zkPoS and event proof.

### Why I/O oracle, not O/I oracle?

The I/O oracle data flow is actually output oracle, then input Oracle. It is not called O/I, because O/I is less common than I/O. Also, there is no real combination of input oracle and then output oracle. It's more like two separate oracles.

### Is rollup a kind of oracle?

No.

We really want to frame rollup as a kind of oracle, and zk rollup as a zkOracle. However, rollup’s system is more complex. The core part of oracle is not about "oracle". To avoid confusion, rollup is not one category in zkOracle.

### Is price feeds an input oracle if data source is price of on-chain assets?

Yes.

Even if data source is about on-chain assets, the price still comes from something like CEX. It still meets the definition of Input Oracle, having data feeds from off-chain (even if they are about on-chain data).

### Will all codes of ORA be open-sourced?

Yes.

### Why ORA is trustless, not trust-minimized/trustful?

Strictly speaking, nothing is trustless because you still have to trust some fundamental rules like Math or Cryptography. But we still use the term of trustless to demonstrate the trustworthiness, security, verifiability, and decentralization of our network. [Trust-minimized](https://twitter.com/toghrulmaharram/status/1643739327128829955) is still a good word that describes ORA.

### Why finality matters and does overhead in proof generation makes ORA zkOracle slower?

Finality means the ultimate certainty and correctness of the data. Any use and presentation of the data is only completely secure once the finality is confirmed. This is essential for an oracle.

In contrast to the dispute period mechanism, zk shortens the time from weeks to seconds.

### What is zkPoS exactly?

A component that simply gets valid block header by proving Ethereum consensus with zk.

### What is the relationship between World Supercomputer and ORA?

Simply put, ORA is a key network of the entire World Supercomputer network. In addition, World Supercomputer is also served by Ethereum as the consensus network and Storage Rollup as the storage network.

### What is the difference between World Supercomputer and Rollups?

The main difference between modular blockchain (including L2 Rollup) and world computer architecture lies in their purpose: Modular blockchain is designed for creating a new blockchain by selecting modules (consensus, DA, settlement, and execution) to put together into a modular blockchain; while World Supercomputer is designed to establish a global decentralized computer/network by combining networks (base layer blockchain, storage network, computation network) into a world computer.

### ...still got questions?

Reach out in our [Discord](https://discord.gg/MgyYbW9dQj).
