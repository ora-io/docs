---
description: Power zkGraph with ZK
---

# zkWASM

Since zkGraph is fully customizable and programmable, it requires a general runtime environment to execute. Similar to how EVM runs smart contracts, zkWASM (zkVM of WebAssembly) runs zkGraphs.

As a part of the Subgraph-Equivalence, zkGraph also employs WASM-based mappings. It is "translated" into AssemblyScript, a language designed to be run in a WebAssembly runtime environment.

The Graph uses wasmtime as the WebAssembly runtime for Subgraph, while Hyper Oracle uses zkWASM as the WebAssembly runtime for zkGraph. This difference in execution engines makes zkGraph zk, without sacrificing any general computation ability. Replacing wasmtime with zkWASM is like replacing EVM with zkEVM. Any program run in zkWASM has the superpower of ZK, including verifiability, trustlessness, decentralization, and computational integrity.

<figure><img src="../../.gitbook/assets/截屏2023-02-19 上午3.13.43.png" alt=""><figcaption><p>Hyper Oracle zkWASM and The Graph WASM</p></figcaption></figure>

Hyper Oracle zkGraph are not limited to be running exclusively in zkWASM. We value the decentralization of prover/client diversity and are constantly exploring new ways to power zkGraph with zk.

To learn more about zkWASM, please take a look at our previous blog post: [zkWASM, The Next Chapter of ZK and zkVM](https://mirror.xyz/hyperoracleblog.eth/abKqUB4iEJ4kRsGqq8baIFUnhV\_eY-lblmhCrwRm31E). For further technical details, you can refer to the paper titled [ZAWA: A ZKSNARK WASM Emulator](https://jhc.sjtu.edu.cn/\~hongfeifu/manuscriptb.pdf).

zkWASM will enable Hyper Oracle zkGraph to achieve programmable configuration, general computation, subgraph equivalence, and the superpower of zero-knowledge proofs.
