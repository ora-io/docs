---
description: Frequently Asked Questions
icon: question
---

# FAQ

## Contents

* [Staking](faq.md#staking)
* [Tora Node](faq.md#tora-node)
* [ORA](faq.md#ora)
* [AI Oracle](faq.md#ai-oracle)
* [OPML](faq.md#opml)
* [Other Questions](faq.md#other-questions)

## Staking

💡All relevant information for staking can be found on [Staking page](../points/staking.md)

### How many points are earned from staking?

8N per N ETH (If you stake 1 ETH, you get 8 points every day). \
N represents the amount of ETH or other assets you staked.

You can find more information on the ORA Points Program by checking the following link – [https://docs.ora.io/doc/points/staking#staking-points](https://docs.ora.io/doc/points/staking#staking-points)

### Is there a minimum stake period?

In Phase 1, there is no lock up period. It takes 24 hours to take to initiate your withdrawal before you are able to claim it.

After you initiate the withdraw, you will need to submit another transaction to “claim” your withdraw. (Two transactions in total)

In Phase 2, there are 2 options, locked and flexible staking. Locked staking is subject to a 6 month locking period.  With flexible staking you may withdraw at any time. Participants for locked staking will earn more points.&#x20;

Read more here: [https://docs.ora.io/doc/points/staking#withdraw](https://docs.ora.io/doc/points/staking#withdraw)

### Have staking contracts been audited?&#x20;

The contracts were audited by Salus. Reference here: [https://x.com/salus\_sec/status/1811658734998811005](https://x.com/salus\_sec/status/1811658734998811005)



## Tora Client

Information about running Tora Client can be found under our [Node Operator Guide](../oao-onchain-ai-oracle/node-operator-guide/).

### How to run Tora Client?

Currently there are 2 options for running a Tora client, Tora Launcher and CLI option.&#x20;

### Are there incentives for running a Tora Client?

The incentive is in form of ORA points. Read more on [Points page](broken-reference).

Each validated transaction will earn 3 points. Read more here: [https://docs.ora.io/doc/points/tasks#task-4-running-validator-node](https://docs.ora.io/doc/points/tasks#task-4-running-validator-node)

### How can I monitor Node network health?

You can check the logs in the running docker containers.&#x20;



## ORA Network

### Is ORA  network a rollup or layer 2?

Neither.

ORA is a verifiable AI oracle network.  It contains a set of smart contracts capable of making calls to a network of nodes computing AI inference, secured by opML.&#x20;



## AI Oracle

### How does AI Oracle handle large responses to generate videos or images?

The generated content can be stored on a decentralized storage network, eg. IPFS.

Files can be retrieved via the IPFS gateway with the given ID from ORA's AI Oracle.

### I want to build with ORA's AI Oracle, what options do I have?

* zkML of [keras2circom](https://github.com/ora-io/keras2circom) (the most battle-tested and performant zkML framework)
* [opML](https://arxiv.org/abs/2401.17555) of [AI Oracle](../oao-onchain-ai-oracle/introduction/) (run huge model like LlaMA2-7B and Stable Diffusion now)
* zk+opML with [opp/ai](https://arxiv.org/abs/2402.15006) (futuristic onchain AI fuses zkML's privacy and opML's scalability)

We recommend you [build with Ora's AI Oracle secured by opML](../oao-onchain-ai-oracle/introduction/). It is production-ready and an out-of-the-box solution, with support to LlaMA2-7B and Stable Diffusion.

### What does the AI Oracle fee consist of?

AI Oracle fee = Model Fee (for LlaMA2 or Stable Diffusion) + Callback Fee (for node to submit a inference result back to onchain) + Network Fee (gas)

Callback fee and network fees may be higher when network is experiencing congestion.&#x20;

Callback fees may be lower if you are using model such as Stable Diffusion, because the inference result will be shorter (just an IPFS hash, instead of long paragraphs in LLM).



## OPML

### How does opML guarantee consistency, given ML models are non-deterministic?

The model uses deterministic inference (learn more from [this talk on determinism on ML](https://www.youtube.com/watch?v=ghU\_-ADHBaw)), there are [built using Nvidia's deterministic feature](https://docs.nvidia.com/clara/clara-train-archive/3.1/nvmidl/additional\_features/determinism.html) or are moved into our deterministic vm (this is recommended for better support).

### What's the challenge time of opML? 7 days?

Similar to Optimistic rollups, opML has a 7 day challenge period. It is possible that this may be reduced in the future.  When optimized, the challenge period can operate similarly to [a sovereign rollup](https://modularmedia.substack.com/i/132840875/do-optimistic-sovereign-rollups-make-sense), with this period reduced to  [a few minutes](https://twitter.com/nickwh8te/status/1674419952517009409) or [even a few seconds](https://twitter.com/colludingnode/status/1673730479000809473).

### What is the limitation of opML?

Privacy, because all models in opML needs to be public and open-source for network participants to challenge. This can be mitigated with [opp/ai](https://arxiv.org/abs/2402.15006).

### **What is the proving overhead, performance, and limitations of zkML frameworks?**

* Modulus Labs zkML bringing GPT2-1B onchain resulted in a  [1m+ times overhead (200+ hours for each call), 128-core CPU and 1TB RAM](https://medium.com/@ModulusLabs/chapter-14-the-worlds-1st-on-chain-llm-7e389189f85e).
* The zkML framework with EZKL [takes around 80 minutes to generate a proof of a 1M-nanoGPT model](https://hackmd.io/mGwARMgvSeq2nGvQWLL2Ww#Honey-I-SNARKED-the-GPT).
* [According to Modulus Labs](https://medium.com/@ModulusLabs/chapter-8-make-zkml-real-a3a355b2b756), zkML has >>1000 times overhead than pure computation, with [the latest report](https://twitter.com/shumochu/status/1723839817836888365) being 1000 times, and [200 times for small model](https://medium.com/@ModulusLabs/chapter-13-scaling-intelligence-637d4a374153)s.
* According to [EZKL’s benchmark](https://blog.ezkl.xyz/post/benchmarks/), the average proving time of RISC Zero is of 173 seconds for Random Forest Classification.

For more information reference [this Ethereum Foundation granted benchmark](https://hackmd.io/\_vrpMIusSEaROYUU7-Shaw) on our zkML framework with others.

## Other Questions

### How can I be a OG on discord?

Unfortunately, the OG role was a limited-time opportunity exclusively for our first 100 Discord community members, and that window has closed. However, we appreciate your interest and look forward to having you as part of our community!



More questions? Reach out in our [Discord](https://discord.gg/MgyYbW9dQj).
