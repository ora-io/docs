---
description: https://arxiv.org/abs/2401.17555
---

# opML

Some pioneers are trying to implement onchain ML using zkML. The idea is to generate a cryptographic proof for ML computations that is succinct enough to be verified on the blockchain.

However, this approach is not really practical given the restraints of current computing power, here are some examples:

* The zkML framework EZKL [takes around 80 minutes to generate a proof of a 1M-nanoGPT model](https://hackmd.io/mGwARMgvSeq2nGvQWLL2Ww#Honey-I-SNARKED-the-GPT).
* [According to Modulus Labs](https://medium.com/@ModulusLabs/chapter-8-make-zkml-real-a3a355b2b756), zkML has >>1000 times overhead than pure computation, with [the latest report](https://twitter.com/shumochu/status/1723839817836888365) being 1000 times.
* According to [EZKL’s benchmark](https://blog.ezkl.xyz/post/benchmarks/), the average proving time of RISC Zero is of 173 seconds for Random Forest Classification.

In the blockchain field, there is another commonly used form of proof: the fault/fraud proof, that is commonly deployed in optimistic rollups, and that can serve as a more practical solution to realize onchain ML.

As [the inventor of opML](https://ethresear.ch/t/opml-optimistic-machine-learning-on-blockchain/16234) and its[ first open source implementation](https://github.com/ora-io/opml), we are thrilled to see the growing adoption of opML. After ORA's release of its [Onchain AI Oracle (OAO)](https://www.ora.io/app/opml/sd), opML can [run Stable Diffusion and LLaMA 2 directly on Ethereum](https://www.hyperoracle.io/app/opml/sd).

Compared to zkML, **opML is all you need**.

Learn more here: [https://arxiv.org/abs/2401.17555](https://arxiv.org/abs/2401.17555).
