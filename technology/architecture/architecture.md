# ZK Oracle

Here is the conceptual architecture for a running zkOracle node in the Ora network.

The design at the start of this section is similar to the previous one, with a few changes made to highlight certain details.

<figure><img src="../../.gitbook/assets/litepaper.001 (5).png" alt=""><figcaption></figcaption></figure>

To discuss the design, let's move from left to right and top to bottom:

1. Ethereum blockchain serves as the original on-chain data source for zkOracles, but in the future, any network can be used.
2. The Ora zkOracle node consists of two main components: zkPoS and zkWASM.
   * zkPoS fetches the block header and data roots of the Ethereum blockchain by proving Ethereum's consensus with zk. The zk proof generation process can be outsourced to a decentralized prover network. zkPoS works as the foreign circuit of zkWASM.
   * zkPoS feeds the block header and data roots to zkWASM. zkWASM takes this data as essential inputs for running CLEs.
   * zkWASM runs customized data mappings defined by CLEs and generates zk proofs of those operations. The operator of the zkOracle node can choose the number of CLEs they wish to run (from one to all deployed CLEs). The zk proof generation process can be outsourced to a decentralized prover network.
3. The output of a zkOracle is off-chain data that developers can use through Ora CLE Standards. The data also comes with zk proofs that demonstrate the validity and computation of the data.

Only one zkOracle node is necessary to maintain network security. In the Ora network, there can still be multiple zkOracle nodes targeting zkPoS as well as each CLE. This enables parallel generation of zk proofs, which can significantly enhance performance.

Here is a more detailed technical architecture with data flow for a zkOracle:

<figure><img src="../../.gitbook/assets/截屏2023-10-08 下午7.43.04.png" alt=""><figcaption><p>zkOracle Technical Architecture</p></figcaption></figure>
