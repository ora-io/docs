---
description: ZK Circuits for Chainstate Proofs
---

# Specialized Circuit

zkGraphs represent programmable logic, as a Turing-complete program in zkWASM; Chainstate Proofs are fixed components of the overall zkOracle circuit architecture, and are usually not subject to major changes.

Since Chainstate Proofs do not need to be changed frequently, developing them as specialized circuits can optimize the performance by a lot.

Chainstate Proofs include:

* State Proof
* Event Proof
* Transaction Proof

Each of these proofs has a specialized circuit that handles the state root, receipt root, and transaction root in the block header.

We will open source all of these Specialized Circuits in the future.
