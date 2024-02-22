# ZK Oracle

Here is the conceptual architecture for a running ZK Oracle node in the ORA network.

The design at the start of this section is similar to the previous one, with a few changes made to highlight certain details.

<figure><img src="../../.gitbook/assets/litepaper.001 (9).png" alt=""><figcaption></figcaption></figure>

To discuss the design, let's move from left to right and top to bottom:

1. Ethereum blockchain serves as the original on-chain data source for ZK Oracle, but in the future, any network can be used.
2. The ORA ZK Oracle node consists of two main components: zkPoS and zkWASM.
   * zkPoS fetches the block header and data roots of the Ethereum blockchain by proving Ethereum's consensus with zk. The zk proof generation process can be outsourced to a decentralized prover network. zkPoS works as the foreign circuit of zkWASM.
   * zkPoS feeds the block header and data roots to zkWASM. zkWASM takes this data as essential inputs for running CLEs.
   * zkWASM runs customized data mappings defined by CLEs and generates zk proofs of those operations. The operator of the ZK Oracle node can choose the number of CLEs they wish to run (from one to all deployed CLEs). The zk proof generation process can be outsourced to a decentralized prover network.
3. The output of a ZK Oracle is off-chain data that developers can use through ORA CLE Standards. The data also comes with zk proofs that demonstrate the validity and computation of the data.

Only one ZK Oracle node is necessary to maintain network security. In the ORA network, there can still be multiple ZK Oracle nodes targeting zkPoS as well as each CLE. This enables parallel generation of zk proofs, which can significantly enhance performance.

Here is a more detailed technical architecture with data flow for a ZK Oracle:

<figure><img src="../../.gitbook/assets/litepaper.001 (1).png" alt=""><figcaption></figcaption></figure>
