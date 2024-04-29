# Glossary

### Aggregation

An operation that brings together multiple elements

### AssemblyScript

A TypeScript-like language for WebAssembly.

### Automation

A type of middleware that performs operations without human control. Commonly used in blockchain due to smart contracts' inability to trigger automatic functions and DApps' need for periodic calls.

### CLE

Computational Entity. The customizable and programmable software defined by developers, and the underlying oracle network that runs this software

### Client

A software for operating a node. Usually developed by the network's core developer team.

### Dispute Period

A time window for finalizing disagreement on computation. Usually taking weeks. Used in traditional oracle networks.

### Ethereum PoS

Refers to Ethereum's consensus algorithm.

### Filtering

An operation that rejects unwanted elements

### Finality

Reached when zk proof is verified, or dispute period is passed, and data becomes fully immutable and constant. See [L2Beat's definition](https://medium.com/l2beat/tracking-time-to-finality-of-l2-transactions-051d32f5d5ba).

### Fisherman Mechanism

A staking mechanism that involves a "fisherman" to check integrity of nodes and raise disputes, and an "arbitrator" to decide outcome of disputes.

### GraphQL

An approach for querying data. Commonly used in the front-end of DApps.

### Halo2

A high-performance implementation of zk-SNARK by Electric Coin Co.

### Hyper Oracle

The former naming format of HyperOracle. Use HyperOracle.

### Indexing

A type of middleware that fetches and organizes data. Commonly used in blockchain due to blockchain data's unique storage model.

### JavaScript

A programming language for Web.

### Latency

A delay in outputting execution results caused by proof generation or a dispute period.

### Mapping

An operation that associates input elements with output elements.

### Middleware

Services or infrastructure needed in the development pipeline.

### Node

A computer running client.

### OAO

On-chain AI Oracle.

### On/Off-chain

On the (specific) blockchain / not on the (specific) blockchain. Usually refers to data or computation.

### opML

[Optimistic machine learning](https://arxiv.org/pdf/2401.17555.pdf).

### ORA

Name of our project. Previously HyperOracle.

### Oracle

A component for processing data in DApp development. Can be input oracle (input off-chain data to on-chain), output oracle (output on-chain data to off-chain), and I/O oracle (output oracle, then input oracle).

### Programmable

Able to be customized and defined by code.

### Proof Generation

A process of producing zero-knowledge proof. Usually takes much longer than execution only.

### Recursive Proof

A ZK proof that verifies other ZK proofs, for compressing more knowledge into a single proof.

### Slashing

A process that involves burning of staked token for a node with bad behavior.

### Staking

A required process that involves depositing and locking tokens for a newly-entered node into the network.

### Subgraph

Codes that define and configure indexing computations for The Graph's indexer.

### Subgraph-Equivalence

Complete alignment with the Subgraph specification and syntax.

### Succinct

Able to be verified easily with less computation resources than re-execution. One important quality of zero-knowledge proof.

### Trust Model

A model for analyzing trust assumptions and security. See Vitalk's post trust model.

### Trustless

Able to be trusted without relying on a third party.

### TypeScript

A strongly-typed JavaScript.

### Validity

Refers to the correctness of computation.

### Validity Proof

A type of zero-knowledge proof that does not utilize its privacy feature, but succinctness property.

### Verifiable

Able to be checked or proved to be correct.

### Verification

A computation to check if a proof is correct. If verification is passed, it means the proven statement is correct and finalized.

### Verifier

A role that requires the prover to convince with proof. Can be a person, a smart contract in other blockchains, a mobile client, or a web client.

### WASM

A binary code format or programming language. Commonly used in Web.

### World Supercomputer

A global P2P network linking three topologically heterogeneous networks (Ethereum, ORA, Storage Rollup) with zero-knowledge proof.

### Zero-knowledge Proof

A cryptographic method for proving. Commonly used in blockchain for privacy and scaling solutions. Commonly misused for succinctness property only.

### zk-SNARK

A commonly-used zero-knowledge proof cryptography.

### zkAutomation

A trustless automation CLE Standard with zk. Aka. ZK Automation

### zkEVM

A zkVM with EVM instruction set as bytecode.

### zkGraph

Codes that define and configure off-chain computation for HyperOracle's zkOracle, with Subgraph-Equivalence. Now called "CLE".

### zkGraph Standards

Standardized services provided by HyperOracle for DApp developers, including zkIndexing and zkAutomation. Previously called "Meta Apps". Now called "CLE Standards".

### zkIndexing

A trustless indexing CLE Standard with zk. Aka. ZK Indexing.

### zkML

Machine learning based on zk for verifiability and optional privacy.

### zkOracle

An oracle with zk for verifiability and performance. Can be output zkOracle, and I/O zkOracle. Aka. ZK Oracle.

### zkOracle Network

A network with zkOracle nodes for decentralization and trustlessness.

### zkPoS

Ethereum's consensus algorithm fully verified with zk.

### zkVM

A virtual machine with zk that generates zk proofs.

### zkWASM

A zkVM with WASM instruction set as bytecode.
