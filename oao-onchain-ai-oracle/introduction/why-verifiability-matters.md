# Why Verifiability Matters?



### Evolution of Blockchain

Blockchain technology provides a robust decentralized infrastructure that can be applied to different use cases. Bitcoin introduced the idea of borderless money and permissionless p2p network for asset transfer. Then Ethereum showed up and introduced an idea of smart contracts and decentralized applications. The technology keeps evolving, and with it, existing dApps and use-cases change and improve. At the same time, the industry faces constant threat from infrastructural vulnerabilities and the attention of malicious actors attracted to attack and manipulate these applications by the massive capital at stake.

Rapid advancements in Artificial Intelligence have significantly enhanced human performance and transformed many businesses. Recognizing this, many blockchain companies have started integrating AI into their products. AI can analyze vast amounts of data to detect fraud, predict market trends, and enhance security protocols. It can also optimize smart contract performance, automate complex trading strategies, and personalize user experiences in decentralized applications. The synergy between AI and blockchain holds great promise for the future, driving innovation and efficiency in various sectors. As these technologies converge, we can expect to see even more sophisticated solutions that leverage the strengths of both AI and blockchain, paving the way for a more secure and efficient digital economy.

### Issues with Centralized AI

Many traditional AI powered applications use centralized APIs. For most of the use cases this is good enough. But for end-to-end trustless, decentralized applications, we don't want to rely on AI inference provided by a centralized servers, hosted by single authority. Instead, we should be able to prove that certain AI model generated results, and also be able to differentiate between different models. This will ensure that the benefits of AI can enter the blockchain landscape securely, and without increasing attack vectors and uncertainty.

### OAO Provides Verifiable AI

With the introduction of ORA's Onchain AI Oracle (OAO), dapps can now use the power of AI in a verifiable way, thus avoiding any trust assumptions. ORA introduced Optimistic Machine Learning ([opML](../../technology/proving-frameworks-zkml-opml-opp-ai/opml.md)), which serves as a verifiability layer of AI oracle. The oracle system consist of the network of oracle nodes and a set of smart contracts. Any dapp can request AI inference from the oracle by interacting with OAO smart contracts. Once inference request is initiated, oracle network generates verifiable results and send them back to the caller. To start building with ORA's AI Oracle, you can check [Interaction with OAO - Tutorial](../develop-guide/tutorials/interaction-with-oao-tutorial.md).

### Use Cases

To better understand the value of verifiability when using onchain AI, let's examine some use cases. Onchain AI Oracle could be useful across different domains:

**Governance:** Sifting through extensive forum conversations and governance proposals can be daunting. Llama3 and OpenLM are capable of rapidly parsing massive data sets, and can make governance more efficient. Adding verifiability to these AI models guarantees to the users that the proposal summaries are actually coming from these models.

**Social:** Neutral, verifiable AI to review content for illegal, malicious or bot activity. AI can setup a strike or block system, while still being decentralized and ‘anti-censorship enough’ to combat bots, scams etc. Verifiability in this case can guarantee neutral, unbiased censorship executed by AI.

**Security/Audits:** An auditing protocol that uses verifiable AI to audit smart contracts. A user submits their smart contracts to the protocol. Onchain AI Oracle returns generated evaluation report back to the user. The evaluation could be done by multiple different AI engines and users could differentiate these reports due to verifiable nature of the results.

**DeFi:** Sophisticated decentralized agents that can react dynamically to market conditions to adjust their strategies. Can perform strategies like copy-trading, managing MEV, expected value of points and aidrops etc. In all of these cases, certain actions should be justified and OAO can provide proofs of these actions to end users.

You can check existing AI powered dapps at [awesome-ora](https://github.com/ora-io/awesome-ora) github repository. There is also a section with build ideas.
