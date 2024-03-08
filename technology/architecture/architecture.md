# zkOracle

Here is the conceptual architecture for a running zkOracle node in the ORA network.

The design at the start of this section is similar to the previous one, with a few changes made to highlight certain details.

<figure><img src="../../.gitbook/assets/litepaper.001 (9).png" alt=""><figcaption></figcaption></figure>

To discuss the design, let's move from left to right and top to bottom:

1. Ethereum blockchain serves as the original on-chain data source for zkOracle, but in the future, any network can be used.
2. The ORA zkOracle node consists of two main components: zkPoS and zkWASM.
   * zkPoS fetches the block header and data roots of the Ethereum blockchain by proving Ethereum's consensus with zk. The zk proof generation process can be outsourced to a decentralized prover network. zkPoS works as the foreign circuit of zkWASM.
   * zkPoS feeds the block header and data roots to zkWASM. zkWASM takes this data as essential inputs for running CLEs.
   * zkWASM runs customized data mappings defined by CLEs and generates zk proofs of those operations. The operator of the zkOracle node can choose the number of CLEs they wish to run (from one to all deployed CLEs). The ZK proof generation process can be outsourced to a decentralized prover network.
3. The output of a zkOracle is off-chain data that developers can use through ORA CLE Standards. The data also comes with ZK proofs that demonstrate the validity and computation of the data.

Only one zkOracle node is necessary to maintain network security. In the ORA network, there can still be multiple zkOracle nodes targeting zkPoS as well as each CLE. This enables parallel generation of ZK proofs, which can significantly enhance performance.

Here is a more detailed technical architecture with data flow for a zkOracle:

<figure><img src="../../.gitbook/assets/litepaper.001 (1).png" alt=""><figcaption></figcaption></figure>
