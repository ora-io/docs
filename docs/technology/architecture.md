# Architecture

Here is the conceptual architecture for a running zkOracle node in the HyperOracle network.

The design at the start of this section is similar to the previous one, with a few changes made to highlight certain details.

<figure><img src="../.gitbook/assets/截屏2023-02-20 上午2.58.21.png" alt=""><figcaption><p>zkOracle Node Structure</p></figcaption></figure>

To discuss the design, let's move from left to right and top to bottom:

1. Ethereum blockchain serves as the original on-chain data source for zkOracles, but in the future, any network can be used.
2. The HyperOracle zkOracle node consists of two main components: zkPoS and zkWASM.
   * zkPoS fetches the block header and data roots of the Ethereum blockchain by proving Ethereum's consensus with zk. The zk proof generation process can be outsourced to a decentralized prover network. zkPoS works as the foreign circuit of zkWASM.
   * zkPoS feeds the block header and data roots to zkWASM. zkWASM takes this data as essential inputs for running zkGraphs.
   * zkWASM runs customized data mappings defined by zkGraphs and generates zk proofs of those operations. The operator of the zkOracle node can choose the number of zkGraphs they wish to run (from one to all deployed zkGraphs). The zk proof generation process can be outsourced to a decentralized prover network.
3. The output of a zkOracle is off-chain data that developers can use through HyperOracle zkGraph Standards. The data also comes with zk proofs that demonstrate the validity and computation of the data.

Only one zkOracle node is necessary to maintain network security. In the HyperOracle network, there can still be multiple zkOracle nodes targeting zkPoS as well as each zkGraph. This enables parallel generation of zk proofs, which can significantly enhance performance.

Here is a more detailed technical architecture with data flow for a zkOracle:

<figure><img src="../.gitbook/assets/截屏2023-10-08 下午7.43.04.png" alt=""><figcaption><p>zkOracle Technical Architecture</p></figcaption></figure>
