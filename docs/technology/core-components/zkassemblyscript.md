---
description: Highly Efficient Provable AssemblyScript Library
---

# zkAssemblyScript

We built [zkAssemblyScript](../../zkgraph/develop-guide/zkgraph-assemblyscript-lib.md), a highly efficient provable AssemblyScript library, because:

* zkGraph is AssemblyScript-based program.
* zkGraph development requires many Ethereum-related data structures and special operations.
* The environment of zkWASM is quite special compared with that of general WASM.
* The performance of proof generation of zkGraphs in zkWASM can be optimized with the standardized library.

In zkAssemblyScript, we have optimized many common data structures (Bytes, BigInt) at the instruction set level to ensure that:

* WASM binary is provable in zkWASM
* Proof generation performance is excellent
* Size of the generated WASM binary is manageable

Developers can also use other AssemblyScript libraries or AssemblyScript native functionality, but there may be issues such as:

* The Graph's [graph-ts](https://github.com/graphprotocol/graph-tooling/tree/main/packages/ts) will not run directly outside of the node's environment.
* Native AssemblyScript Math-related functions are not friendly to zkWASM.
