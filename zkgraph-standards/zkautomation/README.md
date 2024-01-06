---
description: Trustless Automation for Smart Contracts
---

# zkAutomation

[The blockchain world is driven by automation, bots, and keepers](https://mirror.xyz/hyperoracleblog.eth/UYI8mpq6zJ8L2Hbqrliss0mg92v7dNAqz0UhO41d\_dM). Automated programs are required to call smart contracts at certain intervals to maintain the optimal price flow of the Automated Market Maker (AMM) or to keep lending protocols healthy by avoiding bad debt.

[Sometimes, these automation calls are too complex for on-chain calculation, too frequent for governance voting, and too critical for permissionless system](https://twitter.com/0xSacha/status/1624102663557087247). In such cases, developers require automation protocols to provide these services, so they don't have to build and run their own automation.

However, having a universal protocol for automation and keeper functions is insufficient. The automation's execution and off-chain data source computations must be secure. If these computations are invalid, the operator nodes must be flagged and punished on the automation network.

zkAutomation is the only automation infrastructure in the market that can execute both with zero knowledge proofs. zkAutomation is not just an output zkOracle meta app, but it is also an I/O zkOracle, because the data flows from on-chain (original data) to off-chain (zkGraph source) to on-chain (automation triggered).

zkAutomation is HyperOracle’s trustless automation protocol based on zero knowledge proofs. zkAutomation's automation execution is entirely secured by zk, and the automation sources (data sources of the automation) and trigger conditions (when to trigger the automation) are fully customizable using zkGraphs. Developers can build bots, such as arbitrage bots, to perform on-chain trading for profit, keepers like liquidation keepers to safeguard their protocol health, or even automated protocols like on-chain ETFs or on-chain stable coins to achieve fully decentralized financial applications.

<figure><img src="../../.gitbook/assets/zkAutomation Graph.png" alt=""><figcaption></figcaption></figure>
