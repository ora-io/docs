---
description: "[zkOracle: ORA's decentralized, verifiable computation oracle](https://ethresear.ch/t/defining-zkoracle-for-ethereum/15131)"
---

# zkOracle

CLE in zkOracle defines the computation of ORA zkOracle nodes, including data-related behaviors and ZK proof generation, much like how smart contracts define the EVM computation of Ethereum nodes.

<figure><img src="../../.gitbook/assets/图2.png" alt=""><figcaption></figcaption></figure>

Smart contract developers can build both the smart contract and the CLE. Users can interact with both.

To utilize the infrastructure of ORA CLE Standards, developers must configure and code their CLEs to specify how they want the data to be handled. ORA nodes then process the data and generate zero-knowledge proof based on the specified definitions.

### Structure

A CLE in zkOracle is customizable and programmable, and consists of three main components:

* Manifest (cle.yaml): The data source, used to configure information such as the CLE Standards used, the target blockchain network, and the target smart contract.
* Mapping (mapping.ts): The data mapping (Off-chain Computation), used to compute blockchain data into other forms.

The core of a CLE is the mapping (mapping.ts) file. The code defines the Off-chain computation program.
