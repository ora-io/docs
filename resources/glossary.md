---
icon: a
---

# Glossary

### Aggregation

An operation that brings together multiple elements

### AssemblyScript

A TypeScript-like language for WebAssembly.

### Automation

A type of middleware that performs operations without human control. Commonly used in blockchain due to smart contracts' inability to trigger automatic functions and DApps' need for periodic calls.

### CLE

Computational Entity. The customizable and programmable software defined by developers and the underlying oracle network running those software.

### Client

A software for operating a node. Usually developed by the network's core developer team.

### Dispute Period

A time window for finalizing disagreement on computation. Usually takes weeks. Used in traditional oracle networks.

### Ethereum PoS

Refers to Ethereum's consensus algorithm.

### Filtering

An operation that rejects unwanted elements

### Finality

Reached when zk proof is verified, or dispute period is passed, and data becomes fully immutable and constant. See [L2Beat's definition](https://medium.com/l2beat/tracking-time-to-finality-of-l2-transactions-051d32f5d5ba).

### Fisherman Mechanism

A staking mechanism involves "fisherman" to check integrity of nodes and raise dispute, and "arbitrator" to decide dispute outcome.

### GraphQL

An approach for querying data. Commonly used in the front-end of DApps.

### Halo2

A high-performance implementation of zk-SNARK by Electric Coin Co.

### Hyper Oracle

The former naming format of HyperOracle. Use HyperOracle.

### Indexing

A type of middleware that fetches and organizes data. Commonly used in blockchain due to blockchain data's unique storage model.

### IMO

Initial Model Offering (IMO) is a mechanism for tokenizing an open-source AI model. Through its revenue sharing model, IMO fosters transparent and long-term contributions to any AI model.

The process works as follows:

1. IMO launches an ERC-20 token (more specifically, ERC-7641 Intrinsic RevShare Token) of any AI model to capture its long-term value.
2. Anyone who purchases the token becomes one of the owners of this AI model.
3. Token holders share revenue generated from onchain usage of the tokenized AI model.

More information can be found on [Initial Model Offering](https://docs.ora.io/doc/imo/introduction) page.

### JavaScript

A programming language for Web.

### Latency

A delay after outputting execution result caused by proof generation or dispute period.

### Mapping

An operation that associates input elements with output elements.

### Middleware

Services or infrastructure needed in pipeline of development.

### Node

A computer running client.

### OAO

Onchain AI Oracle (OAO) is an oracle system which provides verifiable AI inference to smart contracts.

**The system consists of 2 parts:**

* Network of nodes - Nodes execute AI inference and return results back to the blockchain. Validity of the result is proven through one of the proving frameworks: [zkML](glossary.md#zkml), [opML](glossary.md#opml), [opp/ai](glossary.md#opp-ai).
* Set of smart contracts - Any dapp can request AI inference by calling OAO smart contracts. Oracle nodes listen to the events emitted by the OAO smart contracts and execute AI inference. Upon the successful execution, the results are returned in the callback function.

For more information check [OAO introduction](broken-reference) page.

### On/Off-chain

On the (specific) blockchain / not on the (specific) blockchain. Usually refers to data or computation.

### opML

Optimistic Machine Learning (opML) is a machine learning proving framework. In uses game-theory to ensure the validity of AI inference results. The proving mechanism works similar to optimistic rollups approach.

For more information check [opML](../technology/proving-frameworks-zkml-opml-opp-ai/opml.md) page.

### opp/ai

Optimistic Privacy Preserving AI (opp/ai) is a machine learning proving framework. It combines cryptography and game-theory to ensure the validity of AI inference results.

For more information check [opp/ai](../technology/proving-frameworks-zkml-opml-opp-ai/opp-ai.md) page.

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

A process that involves the burning of staked token for a node with bad behavior.

### Staking

A required process that involves the depositing and locking of token for a new-entered node into network.

### Subgraph

Codes that define and configs indexing computation of The Graph's indexer.

### Subgraph-Equivalence

Complete alignment with the Subgraph specification and syntax.

### Succinct

Able to be verified easily with less computation resources than re-execution. One important quality of zero-knowledge proof.

### Trust Model

A model for analyzing trust assumptions and security. See Vitalk's post trust model.

### Trustless

Able to trust without relying on third-party.

### TypeScript

A Strongly-typed JavaScript.

### Validity

Refers to correctness of computation.

### Validity Proof

A type of zero-knowledge proof that does not utilize its privacy feature, but succinctness property.

### Verifiable

Able to be checked or proved to be correct.

### Verification

A computation to check if proof is correct. If verification is passed, it means proven statement is correct and finalized.

### Verifier

A role that requires prover to convince with proof. Can be a person, a smart contract in other blockchains, a mobile client, or a web client.

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

### zkML

Zero-Knowledge Machine Learning (zkML) is a machine learning proving framework. In uses cryptography to ensure the validity of AI inference results.

For more information check [zkML](../technology/proving-frameworks-zkml-opml-opp-ai/keras2circom-zkml.md) page.

### zkVM

A virtual machine with zk that generates zk proofs.
