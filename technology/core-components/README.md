# Core Components

Hyper Oracle is a network of zkOracles designed for blockchains. At present, the zkOracle network operates solely for the Ethereum blockchain. It retrieves the data from every block of the blockchain as a data source with zkPoS and processes the data using programmable zkGraphs that run on zkWASM, all in a trustless and secure manner.&#x20;

Here is the zkOracle design for the Ethereum blockchain. This serves as a foundational design for a zkOracle, complete with all of the essential components.

<figure><img src="../../.gitbook/assets/截屏2023-03-13 20.15.58 (1).png" alt=""><figcaption><p>Hyper Oracle zkOracle for Ethereum</p></figcaption></figure>

zkPoS verifies Ethereum consensus with a single zk proof that can be accessed from anywhere. This allows zkOracle to obtain a valid block header as a data source for further processing.

zkWASM (zkVM in the graph) is the runtime of zkGraph, providing the power of zk to any zkGraph in the Hyper Oracle Network. It is similar to the kind of zkEVM used in ZK Rollups.

zkGraph (run in zkWASM) defines customizable and programmable off-chain computation of zkOracle node’s behaviors and Meta Apps. It can be thought of as the smart contract of the Hyper Oracle Network.
