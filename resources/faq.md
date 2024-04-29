---
description: Frequently Asked Questions
---

# FAQ

### Why are indexing and automation considered oracles?

Our [framing of oracles](https://ethresear.ch/t/defining-zkoracle-for-ethereum/15131) categorizes oracles into three different types: input oracle (price feeds for example, inputs off-chain data to on-chain), output oracle (indexing, outputs on-chain data to off-chain), and I/O oracle (automation, output oracle + input oracle, outputs on-chain data to off-chain then computes and feeds result back to on-chain).

Our ZK Oracle CLE Standards (Meta Apps) are output zkOracle and I/O zkOracle.

### What are security mechanisms for other ZK Oracle networks?

First, traditional oracle networks are mostly based on "PoS". [PoS in oracle networks is always insecure](https://mirror.xyz/hyperoracleblog.eth/RA-c\_9ydwKhSo-KV2Ti5Fu4YwThxSTQuBrlLX1\_huFw).

Output oracles such as The Graph have fisherman mechanism ([doc](https://thegraph.com/docs/en/network/indexing/#what-are-disputes-and-where-can-i-view-them), [code](https://github.com/graphprotocol/contracts/blob/dev/contracts/disputes/DisputeManager.sol)). It is kind of like Optimistic Rollups' fault/fraud proof, but without verifiability and decentralization. How it works is that during a week-long dispute period, someone can stake their token to challenge the computation (indexing or querying) and result of a node operator (indexer), and arbitrator council decides if challenge gets accepted.

I/O oracles such as Gelato Network and Keep3r Network have governance for security. Some of them are [not permissionless](https://docs.gelato.network/introduction/executor-operators#who-can-become-an-executor) now and requires legal bindings for operating a node. The networks with [governance as security mechanism](https://docs.keep3r.network/roles/governance) requires someone to challenge a node operator (executor) on their governance platform (usually a forum) and members will manually examine the challenge.

### Is zk necessary for an oracle network?

Yes.

We believe the advancement in zk technology will drive down the cost of compute power and time required for proof generation to make ZK Oracle network desirable. We believe a fully trustless, decentralized, secure, and verifiabe oracle network as middleware for DApps is vital. If one component is centralized, the whole DApp is just a App with smart contract.

### Is ORA a rollup or layer 2?

Neither.

ORA is verifiable oracle protocol. ORA network looks like a "layer 2" on a typical blockchain network. However, it doesn't scale smart contracts' computation, but extends smart contracts' features. An actual rollup requires [a bridge](https://drive.google.com/file/d/1KOEKNDGLBiLbaUDnIxCV6L1aBJblGPJs/view) or [an aggregator](https://www.youtube.com/watch?v=NKQz9jU0ftg).

### Is ORA zkOracle "zk" (with privacy) or "validity"?

Validity, for now.

Given that oracle often operates for public computation and handles public data for blockchains, it may not be necessary to add a private layer on validity. We may explore privacy in some future use cases.&#x20;

### What computation in ORA zkOracle is secured by zk?

The whole pipeline of ZK Oracle.

Data source accessing is secured by zkPoS, and off-chain computation is secured by zkVM.

### How data source of zkOracle is secured since zk are only safeguarding computation?

On-chain data.

The computation is secured by zk, but data source cannot be guaranteed to be safe only by zk. If we use any kind of data from any source, this may break the security of ZK Oracle even though computation is  valid. On-chain data is already verified and secured by the base layer blockchain. That's why we are only developing output ZK Oracle and I/O ZK Oracle.

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

We may experiment with input ZK Oracles such as zkML in the future.

### What will be the economic design for ORA Network?

Currently, it is not final.

But our idea is that the whole economic model should be simple enough, not a system that is difficult to understand through various [complex mechanisms](https://twitter.com/matthuang/status/1638359675258421248). Compared to similar oracle networks, we will remove some unnecessary "added to maintain the token price" mechanisms, while our ZK mechanism is essentially replacing the unnecessary staking mechanism in oracle networks. Our final model will probably be like PoW's Ethereum or Aleo.

### Is ORA network permissionless?

Yes.

In the future, anyone will be able to run a ORA zkOracle node. In the meantime, we will make technical and architectural efforts to make the hardware requirements to run the node even lower, even running a prover in the web.

### Is ORA an oracle?

Yes.

ORA is the verifiable oracle protocol.

### Is the cost of using ORA zkOracle CLE Standards higher than other oracle services without zk?

Overall, lower sometimes; in terms of unit calculations, slightly higher.

Overall, each CLE requires only one zkOracle node to ensure security, while other oracle networks require a very large number of nodes to ensure computational validity with these redundancies. Therefore, on the whole system, only 1 node is needed for the overhead of the whole service without considering the overall robustness, uptime, and performance improvement.

If the calculation is based on each index or query, then there is always an additional proof generation cost for each calculation. However, in the case of the zkEVM Rollup, these premiums are evened out, ending up with an additional $0.0...N per computed proof. In addition, some proof generation results can be shared, such as zkPoS and event proof.

### Why I/O oracle, not O/I oracle?

The I/O oracle data flow is actually output oracle, then input Oracle. It is not called O/I, because O/I is less common than I/O. Also, there is no real combination of input oracle and then output oracle. It's more like two separate oracles.

### Is rollup a kind of oracle?

No.

We really want to frame rollup as a kind of oracle, and zk rollup as a ZK Oracle. However, rollup’s system is more complex. The core part of oracle is not about "oracle". To avoid confusion, rollup is not one category in ZK Oracle.

### Is price feeds an input oracle if data source is price of on-chain assets?

Yes.

Even if data source is about on-chain assets, the price still comes from something like CEX. It still meets the definition of Input Oracle, having data feeds from off-chain (even if they are about on-chain data).

### Will all codes of ORA be open-sourced?

Yes.

### Why is ORA trustless, not trust-minimized/trustful?

Strictly speaking, nothing is trustless because you still have to trust some fundamental rules like Math or Cryptography. But we still use the term of trustless to demonstrate the trustworthiness, security, verifiability, and decentralization of our network. [Trust-minimized](https://twitter.com/toghrulmaharram/status/1643739327128829955) is still a good word that describes ORA.

### Why does finality matter and does overhead in proof generation makes ORA zkOracle slower?

Finality means the ultimate certainty and correctness of the data. Any use and presentation of the data is only completely secure once the finality is confirmed. This is essential for an oracle.

Finality of zk is when proof generated and verified; and finality of dispute period mechanism like The Graph is when challenge period is passed.

In contrast to the dispute period mechanism like The Graph, zk may shorten the time.

### What is zkPoS exactly?

A component that simply gets valid block header by proving Ethereum consensus with zk.

### What is the relationship between World Supercomputer and ORA?

Simply put, ORA is a key network of the entire World Supercomputer network. In addition, World Supercomputer is also served by Ethereum as the consensus network and Storage Rollup as the storage network.

### What is the difference between World Supercomputer and Rollups?

The main difference between modular blockchain (including L2 Rollup) and world computer architecture lies in their purpose: Modular blockchain is designed for creating a new blockchain by selecting modules (consensus, DA, settlement, and execution) to put together into a modular blockchain; while World Supercomputer is designed to establish a global decentralized computer/network by combining networks (base layer blockchain, storage network, computation network) into a world computer.

### How does opML guarantee consistency, given ML models are non-deterministic?

The model will have to using deterministic inference, either using the [built in Nvidia deterministic feature](https://docs.nvidia.com/clara/clara-train-archive/3.1/nvmidl/additional\_features/determinism.html), or move the model into our deterministic vm (recommended for better support).

### How does AI Oracle handle large responses such as ones to generate videos or images?

The generated content will be stored on decentralized storage network, eg. IPFS.

For IPFS, you can retrieve them with IPFS gateway with the given id from AI Oracle.

### What's the challenge time of opML? 7 days?

Normally, optimistic rollups choose 7 days as their challenge period.&#x20;

For opML the challenge period can be shorter, because it is not a rollup, which involves a lot of financial operations and maintains a public ledger. When optimized, the challenge period can be like [a sovereign rollup](https://modularmedia.substack.com/i/132840875/do-optimistic-sovereign-rollups-make-sense) of [a few minutes](https://twitter.com/nickwh8te/status/1674419952517009409) or [even a few seconds](https://twitter.com/colludingnode/status/1673730479000809473).

### Are fraud proofs "slower" than zk proofs?

As mentioned before, as long as the challenge time of optimistic fraud proof is shorter than proof generation of zk, fraud proofs are faster than zk proofs.

It needs to be noted that zkML for huge AI models are not possible, or the zk proof generation of zkML approach is much slower than opML approach.

### I want to build with ORA's on-chain AI, what can I choose?

You have multiple options for building ORA's on-chain AI:

* zkML of [keras2circom](https://github.com/ora-io/keras2circom) (the most battle-tested and performant zkML framework)
* [opML](https://arxiv.org/abs/2401.17555) of [AI Oracle](../cle/ai-oracle/) (run huge model like LlaMA2-7B and Stable Diffusion now)
* zk+opML with [opp/ai](https://arxiv.org/abs/2402.15006) (futuristic on-chain AI fuses zkML's privacy and opML's scalability)

We recommend you [build with AI Oracle with opML](../cle/ai-oracle/), because it is production-ready and out-of-the-box, with support to LlaMA2-7B and Stable Diffusion.

### What is the limitation of opML?

Privacy, because all models in opML needs to be public and open-source for network participants to challenge.

That is why we came up with [opp/ai](https://arxiv.org/abs/2402.15006) to add privacy feature to opML.

### **What is the proving overhead, performance, and limitations of other zkML frameworks?**

Here are some facts:

* Modulus Labs used zkML to bring GPT2-1B on-chain with [1m+ times overhead (200+ hours for each call), 128-core CPU and 1TB RAM](https://medium.com/@ModulusLabs/chapter-14-the-worlds-1st-on-chain-llm-7e389189f85e).
* The zkML framework EZKL [takes around 80 minutes to generate a proof of a 1M-nanoGPT model](https://hackmd.io/mGwARMgvSeq2nGvQWLL2Ww#Honey-I-SNARKED-the-GPT).
* [According to Modulus Labs](https://medium.com/@ModulusLabs/chapter-8-make-zkml-real-a3a355b2b756), zkML has >>1000 times overhead than pure computation, with [the latest report](https://twitter.com/shumochu/status/1723839817836888365) being 1000 times, and [200 times for tiny model](https://medium.com/@ModulusLabs/chapter-13-scaling-intelligence-637d4a374153).
* According to [EZKL’s benchmark](https://blog.ezkl.xyz/post/benchmarks/), the average proving time of RISC Zero is of 173 seconds for Random Forest Classification.

You can also check out [this Ethereum Foundation granted benchmark](https://hackmd.io/\_vrpMIusSEaROYUU7-Shaw) on our zkML framework with others.

### What does the OAO fee consist of?

OAO fee = Model Fee (for LlaMA2 or Stable Diffusion) + Callback Fee (for node to submit inference result back to on-chain) + Network Fee (aka. transaction fee of networks like Ethereum)

Callback fee and network fee may be higher when network is experiencing higher traffic.

Callback fee may be lower if you are using model such as Stable Diffusion, because the inference result will be shorter (just an IPFS hash, instead of long paragraphs in LLM).

### Why interact with OAO on Ethereum mainnet is expensive?

With OAO fee's structure, callback fee usually takes up major portion of the overall fee, because storing data of inference result on Ethereum is expensive.

You can try use Stable Diffusion model with OAO on Ethereum mainnet (because the callback fee will be lower), or use OAO on other networks, for lower cost.

### ...still got questions?

Reach out in our [Discord](https://discord.gg/MgyYbW9dQj).
