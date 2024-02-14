---
description: Power CLE with ZK, "VM" of Ora zkOracle
---

# zkWASM VM

Since a CLE is fully customizable and programmable, it requires a general runtime environment to execute. Similar to how EVM runs smart contracts, zkWASM (zkVM of WebAssembly) runs CLEs.

As a part of the Subgraph-Equivalence, CLE also employs WASM-based mappings. It is "translated" into AssemblyScript, a language designed to be run in a WebAssembly runtime environment.

The Graph uses wasmtime as the WebAssembly runtime for Subgraph, while Ora uses zkWASM as the WebAssembly runtime for a CLE. This difference in execution engines makes CLE zk, without sacrificing any general computation ability. Replacing wasmtime with zkWASM is like replacing EVM with zkEVM. Any program run in zkWASM has the superpower of ZK, including verifiability, trustlessness, decentralization, and computational integrity.

Ora CLEs are not limited to be running exclusively in zkWASM. We value the decentralization of prover/client diversity and are constantly exploring new ways to power CLEs with zk.

To learn more about zkWASM, please take a look at our previous blog post: [zkWASM, The Next Chapter of ZK and zkVM](https://mirror.xyz/hyperoracleblog.eth/abKqUB4iEJ4kRsGqq8baIFUnhV\_eY-lblmhCrwRm31E). For further technical details, you can refer to the paper titled [ZAWA: A ZKSNARK WASM Emulator](https://jhc.sjtu.edu.cn/\~hongfeifu/manuscriptb.pdf).

zkWASM will enable Ora CLEs to achieve programmable configuration, general computation, subgraph equivalence, and the superpower of zero-knowledge proofs.
