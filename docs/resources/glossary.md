# Glossary

#### Programmable

Able to be customized and defined by code.

#### On/Off-chain

On the (specific) blockchain / not on the (specific) blockchain. Usually refers to data or computation.

#### Zero-knowledge Proof

A cryptographic method for proving. Commonly used in blockchain for privacy and scaling solutions.

#### Validity Proof

A type of zero-knowledge proof that does not utilize its privacy feature, but succinctness property.

#### Succinct

Able to be verified easily with less computation resources than re-execution. One important quality of zero-knowledge proof.

#### zkML

Machine learning based on zk for verifiability and optional privacy.

#### Dispute Period

A time window for finalizing disagreement on computation. Usually takes weeks. Used in traditional oracle networks.

#### GraphQL

An approach for querying data. Commonly used in the front-end of DApps.

#### Mapping

An operation that associates input elements with output elements.&#x20;

#### Filtering

An operation that rejects unwanted elements

#### Aggregation

An operation that brings together multiple elements

#### WASM

A binary code format or programming language. Commonly used in Web.

#### Subgraph

Codes that define and configs indexing computation of The Graph's indexer.

#### Proof Generation

A process of producing zero-knowledge proof. Usually takes much longer than execution only.

#### Latency

A delay after outputting execution result caused by proof generation or dispute period.

#### Verification

A computation to check if proof is correct. If verification is passed, it means proven statement is correct and finalized.

#### Verifier

A role that requires prover to convince with proof. Can be a person, a smart contract in other blockchains, a mobile client, or a web client.

#### Verifiable

Able to be checked or proved to be correct.

#### Oracle

A component for processing data in DApp development. Can be input oracle (input off-chain data to on-chain), output oracle (output on-chain data to off-chain), and I/O oracle (output oracle, then input oracle).

#### zk-SNARK

A commonly-used zero-knowledge proof cryptography.

#### Halo2

A high-performance implementation of zk-SNARK by Electric Coin Co.

#### zkOracle

An oracle with zk for verifiability and performance. Can be output zkOracle, and I/O zkOracle.

#### zkOracle Network

A network with zkOracle nodes for decentralization and trustlessness.

#### zkGraph

Codes that define and configs off-chain computation of Hyper Oracle zkOracle, with Subgraph-Equivalence.

#### Subgraph-Equivalence

Complete alignment with the Subgraph specification and syntax.

#### Ethereum PoS

Refers to Ethereum's consensus algorithm.

#### zkPoS

Ethereum's consensus algorithm fully verified with zk.

#### zkVM

A virtual machine with zk that generates zk proofs.

#### zkEVM

A zkVM with EVM instruction set as bytecode.

#### zkWASM

A zkVM with WASM instruction set as bytecode.

#### Staking

A required process that involves the depositing and locking of token for a new-entered node into network.

#### Slashing

A process that involves the burning of staked token for a node with bad behavior.

#### Node

A computer running client.

#### Client

A software for operating a node. Usually developed by the network's core developer team.

#### Fisherman Mechanism

A staking mechanism involves "fisherman" to check integrity of nodes and raise dispute, and "arbitrator" to decide dispute outcome.

#### Trustless

Able to trust without relying on third-party.

#### Trust Model

A model for analyzing trust assumptions and security. See [Vitalk's post trust model](https://vitalik.ca/general/2020/08/20/trust.html).

#### Finality

Reached when zk proof is verified, or dispute period is passed, and data becomes fully immutable and constant.&#x20;

#### Validity

Refers to correctness of computation.

#### Middleware

Services or infrastructure needed in pipeline of development.

#### Indexing

A type of middleware that fetches and organizes data. Commonly used in blockchain due to blockchain data's unique storage model.

#### Automation

A type of middleware that performs operations without human control. Commonly used in blockchain due to smart contracts' inability to trigger automatic functions and DApps' need for periodic calls.

#### Meta Apps

Services provided by Hyper Oracle for DApp developers, including zkIndexing and zkAutomation.

#### zkIndexing

A trustless indexing Meta App with zk.

#### zkAutomation

A trustless automation Meta App with zk.

#### Recursive Proof

A zk proof that verifies other zk proofs, for compressing more knowledge into a single proof.

#### JavaScript

A programming language for Web.

#### TypeScript

A Strongly-typed JavaScript.

#### AssemblyScript

A TypeScript-like language for WebAssembly.
