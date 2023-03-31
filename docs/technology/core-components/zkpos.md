---
description: Trustless Block Header Fetching, "Data Source" of Hyper Oracle Network
---

# zkPoS

One crucial step in implementing a zkOracle is to retrieve blockchain data for the data source, specifically block header data. Block header data serves as the essential entry point for obtaining the actual data (the three roots) needed for the zkOracle.

<figure><img src="../../.gitbook/assets/截屏2023-02-18 下午6.22.20.png" alt=""><figcaption><p>Ethereum Block Header</p></figcaption></figure>

There are different methods to acquire a block header, but the simplest and least secure or decentralized way is to obtain it from a trusted source, such as Infura. Another option is to use light clients like [Helios](https://a16zcrypto.com/building-helios-ethereum-light-client/).

zkPoS is a trustless block header fetching solution, which proves Ethereum's consensus with zk. Combining zkPoS and light clients like Helios, we can build a SNARK-based light client that uses off-chain computation to eliminate most of the computation of client verification.

Hyper Oracle zkPoS delivers a zk light client with:

* SNARKifying block attestation and other logics of Ethereum consensus (see graph below)
* Recursive proof for multiple blocks of Ethereum consensus

<figure><img src="../../.gitbook/assets/截屏2023-02-18 下午6.49.44.png" alt=""><figcaption></figcaption></figure>

For more details, please refer to our previous blog post: [zkPoS: End-to-end Trustless](https://mirror.xyz/hyperoracleblog.eth/lAE9erAz5eIlQZ346PG6tfh7Q6xy59bmA\_kFNr-l6dE).

zkPoS will enhance the end-to-end trust minimization of Hyper Oracle zkOracle by providing a trustless data source as the input for the oracle.
