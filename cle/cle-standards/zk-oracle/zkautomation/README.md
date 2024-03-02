---
description: Trustless Automation for Smart Contracts
---

# ZK Automation

[The blockchain world is driven by automation, bots, and keepers](https://mirror.xyz/orablog.eth/UYI8mpq6zJ8L2Hbqrliss0mg92v7dNAqz0UhO41d\_dM). Automated programs are required to call smart contracts at certain intervals to maintain the optimal price flow of the Automated Market Maker (AMM) or to keep lending protocols healthy by avoiding bad debt.

[Sometimes, these automation calls are too complex for onchain calculation, too frequent for governance voting, and too critical for permissionless system](https://twitter.com/0xSacha/status/1624102663557087247). In such cases, developers require automation protocols to provide these services, so they don't have to build and run their own automation.

However, having a universal protocol for automation and keeper functions is insufficient. The automation's execution and off-chain data source computations must be secure. If these computations are invalid, the operator nodes must be flagged and punished on the automation network.

ZK Automation is the only automation infrastructure in the market that can execute both with zero knowledge proofs. ZK Automation is not just an output ZK Oracle meta app, but it is also an I/O ZK Oracle, because the data flows from onchain (original data) to off-chain (CLE source) to onchain (automation triggered).

ZK Automation is ORA's trustless automation protocol based on zero knowledge proofs. ZK Automation's automation execution is entirely secured by zk, and the automation sources (data sources of the automation) and trigger conditions (when to trigger the automation) are fully customizable using CLEs. Developers can build bots, such as arbitrage bots, to perform onchain trading for profit, keepers like liquidation keepers to safeguard their protocol health, or even automated protocols like onchain ETFs or onchain stable coins to achieve fully decentralized financial applications.
