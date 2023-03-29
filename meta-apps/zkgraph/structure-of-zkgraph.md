# Structure of zkGraph

A zkGraph is customizable and programmable, consisting of three main components:

* Manifest (zkgraph.yaml): The data source, used to configure information such as the Meta Apps used, the target blockchain network, and the target smart contract.
* Schema (schema.graphql): The data structure, used to define how data is stored and accessed.
* Mapping (mapping.ts): The data mapping (Off-chain Computation), used to compute blockchain data into other forms.

<figure><img src="../../.gitbook/assets/截屏2023-03-14 07.24.03.png" alt=""><figcaption><p>zkGraph Components</p></figcaption></figure>

The core of a zkGraph is the mapping (mapping.ts) file. The code defines the off-chain computation program.

The mapping file usually defines handlers for filtering on-chain events or setting up calldata of smart contract automation. The filters are run in zkWASM (details in the next section), and the zk proofs are generated to ensure computational integrity and validity.

For deployment, all code files for zkGraph will be stored in EthStorage, which is a storage scaling layer supported by Ethereum ESP. This will guarantee that development pipeline for zkGraph is fully decentralized.

Below is the sample code of a zkGraph (for illustrative purposes only):

<figure><img src="../../.gitbook/assets/截屏2023-02-05 下午5.43.10.png" alt=""><figcaption></figcaption></figure>
