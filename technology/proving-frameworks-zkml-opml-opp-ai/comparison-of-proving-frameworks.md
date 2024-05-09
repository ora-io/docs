# Comparison of Proving Frameworks

### opML vs zkML

ORA leverages opML for Onchain AI Oracle because it’s the most feasible solution on the market for running any-size AI model onchain. The comparison between opML and zkML can be viewed from the following perspectives:

* **Proof system**: opML uses fraud proofs, while zkML uses zk proofs.
* **Performance**: opML is much more performant, while zkML has long proof generation time and extremely high memory consumption ([ref1](https://hackmd.io/mGwARMgvSeq2nGvQWLL2Ww#Honey-I-SNARKED-the-GPT), [ref2](https://medium.com/@ModulusLabs/chapter-8-make-zkml-real-a3a355b2b756), [ref3](https://twitter.com/shumochu/status/1723839817836888365), [ref4](https://blog.ezkl.xyz/post/benchmarks/)).&#x20;
* **Security**: opML uses crypto-economic based security, while zkML uses cryptography based security.
* **Finality**: We can define the finalized point of zkML and opML as follows:
  * zkML: Zero-knowledge proof of ML inference is generated (and verified).
  * opML: Challenge period of ML inference is passed. With additional mechanisms, faster finality can be achieved in much shorter time than the challenge period.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### opp/ai

Opp/AI combines both opML and zkML approaches to achieve scalability and privacy. It preserves privacy while being more efficient than zkML.

Compared to pure zkML, opp/ai has much better performance with the same privacy feature.\


<div data-full-width="true">

<figure><img src="../../.gitbook/assets/image (7).png" alt="" width="375"><figcaption></figcaption></figure>

</div>
