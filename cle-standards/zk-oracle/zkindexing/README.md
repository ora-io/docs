---
description: Trustless Indexing, Querying, and Accessing of Blockchain Data
---

# zkIndexing (WIP)

Accessing most on-chain data directly can be a challenge for developers. One potential solution is for developers to run their own indexer to organize the data into a more easily searchable format. However, this can be a [difficult and time-consuming](https://twitter.com/DennisonBertram/status/1621657835334402050) process as it involves rebuilding the entire blockchain state and indexing events from smart contracts. This is where indexing protocols like The Graph come in handy.

As mentioned in [a blog post](https://a16zcrypto.com/content/article/building-helios-ethereum-light-client/) about Helios, blockchains are used for their trustlessness, allowing self-sovereign access to wealth and data. Ethereum has delivered on this promise, but there are concessions for convenience, such as centralized RPC servers like Alchemy. These providers run high-performance nodes on cloud servers so users can easily access chain data, but users must trust them and can't verify the correctness of their queries.

Having a centralized RPC, or a universal indexing and querying protocol is not enough. It is also important to ensure that the [indexed data is accurate and reliable](https://twitter.com/DennisonBertram/status/1621665717274775557) since incorrect data can be even more problematic [than not having an indexer at all](https://twitter.com/0xngmi/status/1567594375357546496). In other words, it is crucial to guarantee the computational integrity and security of the indexing process.

zkIndexing is a unique indexing infrastructure that excels in both accuracy and security using zero knowledge proofs. zkIndexing is a typical output zkOracle meta app, with the data flowing from on-chain (original blockchain data) to off-chain (CLE indexed data).

zkIndexing is Ora's trustless indexing protocol based on zero knowledge proofs. zkIndexing’s indexing and querying schema are fully customizable with CLEs. Developers can build any end-to-end decentralized application with zkIndexing.
