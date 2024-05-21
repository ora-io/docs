---
description: Frequently Asked Questions
---

# FAQ

### Is ORA a rollup or layer 2?

Neither.

ORA is verifiable oracle protocol. ORA network looks like a "layer 2" on a typical blockchain network. However, it doesn't scale smart contracts' computation, but extends smart contracts' features. An actual rollup requires [a bridge](https://drive.google.com/file/d/1KOEKNDGLBiLbaUDnIxCV6L1aBJblGPJs/view) or [an aggregator](https://www.youtube.com/watch?v=NKQz9jU0ftg).

### Is ORA "adding new features" to existing oracles, or "rebuilding and replacing"?

Rebuilding and replacing.

We are the first and your last oracle.

### Is ORA an oracle?

Yes.

ORA is the verifiable oracle protocol.

### Will all codes of ORA be open-sourced?

Yes.

### Why is ORA trustless, not trust-minimized/trustful?

Strictly speaking, nothing is trustless because you still have to trust some fundamental rules like Math or Cryptography. But we still use the term of trustless to demonstrate the trustworthiness, security, verifiability, and decentralization of our network. [Trust-minimized](https://twitter.com/toghrulmaharram/status/1643739327128829955) is still a good word that describes ORA.

### What is the relationship between World Supercomputer and ORA?

Simply put, ORA is a key network of the entire World Supercomputer network. In addition, World Supercomputer is also served by Ethereum as the consensus network and Storage Rollup as the storage network.

### What is the difference between World Supercomputer and Rollups?

The main difference between modular blockchain (including L2 Rollup) and world computer architecture lies in their purpose: Modular blockchain is designed for creating a new blockchain by selecting modules (consensus, DA, settlement, and execution) to put together into a modular blockchain; while World Supercomputer is designed to establish a global decentralized computer/network by combining networks (base layer blockchain, storage network, computation network) into a world computer.

### How does opML guarantee consistency, given ML models are non-deterministic?

The model will have to using deterministic inference (learn more from [this talk on determinism on ML](https://www.youtube.com/watch?v=ghU\_-ADHBaw)), either using the [built in Nvidia deterministic feature](https://docs.nvidia.com/clara/clara-train-archive/3.1/nvmidl/additional\_features/determinism.html), or move the model into our deterministic vm (recommended for better support).

### How does AI Oracle handle large responses such as ones to generate videos or images?

The generated content will be stored on decentralized storage network, eg. IPFS.

For IPFS, you can retrieve them with IPFS gateway with the given id from AI Oracle.

### What's the challenge time of opML? 7 days?

Normally, optimistic rollups choose 7 days as their challenge period.&#x20;

For opML the challenge period can be shorter, because it is not a rollup, which involves a lot of financial operations and maintains a public ledger. When optimized, the challenge period can be like [a sovereign rollup](https://modularmedia.substack.com/i/132840875/do-optimistic-sovereign-rollups-make-sense) of [a few minutes](https://twitter.com/nickwh8te/status/1674419952517009409) or [even a few seconds](https://twitter.com/colludingnode/status/1673730479000809473).

### Are fraud proofs "slower" than zk proofs?

As mentioned before, as long as the challenge time of optimistic fraud proof is shorter than proof generation of zk, fraud proofs are faster than zk proofs.

It needs to be noted that zkML for huge AI models are not possible, or the zk proof generation of zkML approach is much slower than opML approach.

### I want to build with ORA's onchain AI, what can I choose?

You have multiple options for building ORA's onchain AI:

* zkML of [keras2circom](https://github.com/ora-io/keras2circom) (the most battle-tested and performant zkML framework)
* [opML](https://arxiv.org/abs/2401.17555) of [AI Oracle](../oao-onchain-ai-oracle/introduction/) (run huge model like LlaMA2-7B and Stable Diffusion now)
* zk+opML with [opp/ai](https://arxiv.org/abs/2402.15006) (futuristic onchain AI fuses zkML's privacy and opML's scalability)

We recommend you [build with AI Oracle with opML](../oao-onchain-ai-oracle/introduction/), because it is production-ready and out-of-the-box, with support to LlaMA2-7B and Stable Diffusion.

### What is the limitation of opML?

Privacy, because all models in opML needs to be public and open-source for network participants to challenge.

That is why we came up with [opp/ai](https://arxiv.org/abs/2402.15006) to add privacy feature to opML.

### **What is the proving overhead, performance, and limitations of other zkML frameworks?**

Here are some facts:

* Modulus Labs used zkML to bring GPT2-1B onchain with [1m+ times overhead (200+ hours for each call), 128-core CPU and 1TB RAM](https://medium.com/@ModulusLabs/chapter-14-the-worlds-1st-on-chain-llm-7e389189f85e).
* The zkML framework EZKL [takes around 80 minutes to generate a proof of a 1M-nanoGPT model](https://hackmd.io/mGwARMgvSeq2nGvQWLL2Ww#Honey-I-SNARKED-the-GPT).
* [According to Modulus Labs](https://medium.com/@ModulusLabs/chapter-8-make-zkml-real-a3a355b2b756), zkML has >>1000 times overhead than pure computation, with [the latest report](https://twitter.com/shumochu/status/1723839817836888365) being 1000 times, and [200 times for tiny model](https://medium.com/@ModulusLabs/chapter-13-scaling-intelligence-637d4a374153).
* According to [EZKL’s benchmark](https://blog.ezkl.xyz/post/benchmarks/), the average proving time of RISC Zero is of 173 seconds for Random Forest Classification.

You can also check out [this Ethereum Foundation granted benchmark](https://hackmd.io/\_vrpMIusSEaROYUU7-Shaw) on our zkML framework with others.

### What does the OAO fee consist of?

OAO fee = Model Fee (for LlaMA2 or Stable Diffusion) + Callback Fee (for node to submit inference result back to onchain) + Network Fee (aka. transaction fee of networks like Ethereum)

Callback fee and network fee may be higher when network is experiencing higher traffic.

Callback fee may be lower if you are using model such as Stable Diffusion, because the inference result will be shorter (just an IPFS hash, instead of long paragraphs in LLM).

### Why interact with OAO on Ethereum mainnet is expensive?

With OAO fee's structure, callback fee usually takes up major portion of the overall fee, because storing data of inference result on Ethereum is expensive.

You can try use Stable Diffusion model with OAO on Ethereum mainnet (because the callback fee will be lower), or use OAO on other networks, for lower cost.

### ...still got questions?

Reach out in our [Discord](https://discord.gg/MgyYbW9dQj).
