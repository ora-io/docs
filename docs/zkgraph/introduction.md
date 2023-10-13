---
description: zkGraphs are similar to Customizable "Smart Contracts"
---

# Introduction

zkGraph defines the computation of Hyper Oracle nodes, including data-related behaviors and zk proof generation, much like how smart contracts define the EVM computation of Ethereum nodes.

<figure><img src="../.gitbook/assets/截屏2023-03-11 下午11.56.32.png" alt=""><figcaption></figcaption></figure>

Smart contract developers can build both the smart contract and the zkGraph. Users can then interact with both.

To utilize the infrastructure of Hyper Oracle zkGraph Standards, developers must configure and code their zkGraph to specify how they want the data to be handled. The Hyper Oracle nodes then process the data and generate a zero-knowledge proof based on the specified definitions.

### Structure

A zkGraph is customizable and programmable, consisting of three main components:

* Manifest (zkgraph.yaml): The data source, used to configure information such as the Meta Apps used, the target blockchain network, and the target smart contract.
* Mapping (mapping.ts): The data mapping (Off-chain Computation), used to compute blockchain data into other forms.
* (Optional) Schema (schema.graphql): The data structure, used to define how data is stored and accessed.

<figure><img src="../.gitbook/assets/截屏2023-03-14 07.24.03.png" alt=""><figcaption><p>zkGraph Components</p></figcaption></figure>

The core of a zkGraph is the mapping (mapping.ts) file. The code defines the off-chain computation program.

The mapping file usually defines handlers for filtering on-chain events or setting up calldata of smart contract automation. The filters are run in zkWASM (details in the next section), and the zk proofs are generated to ensure computational integrity and validity.

For deployment, all code files for zkGraph will be stored in EthStorage, which is a storage scaling layer supported by Ethereum ESP. This will guarantee that development pipeline for zkGraph is fully decentralized.

### Features

#### **Subgraph-Equivalence**

zkGraph is equivalent to The Graph's Subgraph.

Migrating existing Subgraphs to zkGraph requires just 10 lines of configuration difference. Implementations such as [Standardized Subgraph](https://github.com/messari/subgraphs) and ecosystem tooling like [Instant Subgraph](https://docs.goldsky.com/indexing/instant-subgraphs) and [Subgraph Uncrashable](https://thegraph.academy/developers/subgraph-uncrashable/) can be used for developing zkGraph.

#### zkAssemblyScript

We built [zkAssemblyScript](zkgraph-assemblyscript-lib.md), a highly efficient provable AssemblyScript library, for zkGraph development.

As a library of data structures and interfaces, zkAssemblyScript guarantees zkGraph code execution and proof generation performance through low-level optimizations.
