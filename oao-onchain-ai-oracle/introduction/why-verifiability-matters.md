# Why Verifiability Matters?



### Evolution of Blockchain

Blockchain technology provides a robust decentralized infrastructure that can be applied to different use cases. Bitcoin introduced the idea of borderless money and permissionless p2p network for asset transfer. Then Ethereum showed up and introduced an idea of smart contracts and decentralized applications. Ever since, the technology kept evolving, solving different problems. Nowadays there are many L2 solutions solving scalability issues, cross-chain bridges solving liquidity fragmentation, even complex DeFi protocols introducing the whole new world of finance. The technology keeps evolving and changing existing dapps and use cases.

On the other hand rapid advancements in Artifical Inteligence significantly enhanced human performance and changed many businesses. Many blockchain companies realized that and strated using AI in their products.

### Issues with Centralized AI

Many traditional AI powered applications use centralized APIs. For most of the use cases this is good enough. But for end-to-end trustless, decentralized applications, we don't want to rely on AI inference provided by a centralized servers, hosted by single authority. Instead, we should be able to prove that certain AI model generated results, and also be able to differentiate between different models.

### OAO provides verifiable AI

With the introduction of ORA's Onchain AI Oracle (OAO), dapps can now use the power of AI in a verifiable way, thus avoiding any trust assumptions. ORA introduced Optimistic Machine Learning ([opML](../../technology/proving-frameworks-zkml-opml-opp-ai/opml.md)), which serves as a verifiability layer of AI oracle.

### Use Cases

To better understand the value of verifiability when using onchain AI, let's examine some use cases. Onchain AI Oracle could be useful across different domains:

**Governance:** Sifting through extensive forum conversations and governance proposals can be daunting. Llama3 and OpenLM are capable of rapidly parsing massive data sets, and can make governance more efficient. Adding verifiability to these AI models guarantees to the users that the proposal summaries are actually coming from these models.

**Social:** Neutral, verifiable AI to review content for illegal, malicious or bot activity. AI can setup a strike or block system, while still being decentralized and ‘anti-censorship enough’ to combat bots, scams etc. Verifiability in this case can guarantee neutral, unbiased censorship executed by AI.

**Security/Audits:** An auditing protocol that uses verifiable AI to audit smart contracts. A user submits their smart contracts to the protocol. Onchain AI Oracle returns generated evaluation report back to the user. The evaluation could be done by multiple different AI engines and users could differentiate these reports due to verifiable nature of the results.

**DeFi:** Sophisticated decentralized agents that can react dynamically to market conditions to adjust their strategies. Can perform strategies like copy-trading, managing MEV, expected value of points and aidrops etc. In all of these cases, certain actions should be justified and OAO can provide proofs of these actions to end users.

You can check existing AI powered dapps at [awesome-ora](https://github.com/ora-io/awesome-ora) github repository. There is also a section with build ideas.
