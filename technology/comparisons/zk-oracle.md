# ZK Oracle

### ZK Oracle Network vs. Other Oracle Network

When creating a decentralized oracle, the ZK Oracle network has notable differences compared to traditional ones.

To start, the workflow and architecture are distinct. The ZK Oracle network is more streamlined since all intensive computation is carried out securely and trustlessly off-chain using ZK. In contrast, traditional oracles are restricted to trustless aggregation and "trusted" computation by a smart contract's limited computing capability.

<figure><img src="../../.gitbook/assets/litepaper.001 (8).png" alt=""><figcaption></figcaption></figure>

Based on the graph shown above, we can compare the advantages of ZK Oracle network to traditional oracle networks:

**Decentralization (Trustlessness, Security, and Censorship-Resistence)**

The ZK Oracle network, ORA, operates without requiring external trust in third parties, making it a trustless network. In contrast, traditional oracle networks rely on trusted third parties and networks. The ZK Oracle network follows the 1-of-N trust model, as defined in Vitalik Buterin's article on [trust models](https://vitalik.ca/general/2020/08/20/trust.html), which only requires one node to maintain the network's health and uptime. Traditional oracle networks, on the other hand, are only considered decentralized when they reach an extremely large number of nodes. The security of the ZK Oracle network is fully based on mathematics and cryptography and it inherits its security from Ethereum, which serves as its data source.

**Performance and Finality**

Finality is achieved at the end of the challenge period, according to [a widely-accepted definition of finality for rollups](https://twitter.com/norswap/status/1613329330410504193). Traditional oracle and ZK Oracle networks can be compared to Optimistic and ZK Rollups respectively, so we can use this definition for performance comparison. Input oracles, such as Chainlink Price Feeds, and output oracles, such as The Graph Protocol, rely on the slashing or challenge period, which can take days or even weeks. However, zkOracle networks, like ORA, are based on the zk proof generation time. While zk proof generation has overheads compared to pure computation, the oracle's performance still improves from days or weeks of challenge period down to minutes or seconds even without considering parallel proving. Due to the nature of zk, adding more nodes to the ZK Oracle network can nearly [linearly boost](https://twitter.com/toghrulmaharram/status/1629356500555628546) its performance with parallel proving, instead of only creating redundancy in the network.

**Cost**

The ZK Oracle network follows a 1-of-N trust model, which means that only one honest node is needed to create a secure network. This eliminates the redundancy found in traditional oracle networks, making it a more secure option. Despite the added cost of zk proving (in the case of zkEVM, proving cost for a large batch of transactions is only $0.06), the ZK Oracle network generates lower fees than traditional oracle networks.

**Mechanism and Architecture**

Traditional oracle networks have complex architectures that involve multiple components with different mechanisms. They involve many dependencies, such as complex tokenomics, and uncertain third-party reputation. In comparison, the ZK Oracle network has a simpler architecture and more straightforward mechanism. As long as there is one honest ZK Oracle node and the zk proofs are verified, all associated data is correct.

### ZK Automation vs. Other Automation Protocols

ZK Automation offers all the advantages of ZK Oracle network, along with specific benefits when compared to other automation protocols like Keep3r Network, Chainlink Automation, and Gelato Network. In addition to having all the features of these automation protocols, ZK Automation also provides:

**Trustless Offchain Source**

ZK Automation provides trustless automation based on off-chain source with programmable CLEs. This allows for flexible automation that triggers based on off-chain computation results while maintaining a secure mechanism.

**Verifiability and Security with ZKP**

ZK Automation's zk proofs enable full verifiability. Other automation protocols usually rely on DAO, "social consensus", or even legal documents to restrict bad behaviors, which can create uncertainty and additional time or power burden for protecting the network's health. In contrast, ZK Automation's network is autonomous and automated with pure cryptography-based proof generation and verification without human intervention.

### ZK Indexing vs. Other Indexing Protocols

ZK Indexing offers all the benefits of the ZK Oracle network, as well as several advantages over other indexing protocols like The Graph. These include:

**Improved Performance with Trustlessness**

Performance is a key metric for an indexing and querying service, with latency of request and response largely dependent on the geographic distance between the node and requester. Traditional decentralized indexing networks struggle with this due to the honest majority assumption. While requesters can trust the outcome from the entire network, they cannot trust a single node, which can affect performance. ZK Indexing solves this with zk proofs. Developers can request data trustlessly from only one ORA ZK Oracle node, which is geographically closest and fastest.

**Verifiability and Security with ZKP**

Traditional indexing networks currently only serve certain types of decentralized applications that do not consider data correctness as a critical component, such as dashboards. This is not due to a lack of desire on the part of developers to integrate these indexing services as core components, but rather because these networks are not yet secure enough through multi-sig controlled dispute council. ZK Indexing addresses this issue with verifiability and security backed by the mathematics and cryptography of zk proofs. Developers can build any type of decentralized application with ZK Indexing.
