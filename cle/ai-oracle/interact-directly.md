---
description: Usage Guide for Anyone to Use On-chain AI Directly on Etherscan
---

# Interact Directly

As a user, to interact with the On-chain AI Oracle, you can:

* Use our [AI.ORA.IO](https://ai.ora.io/) frontend.
* Interact with the Prompt contract directly on Etherscan

Here's the guide to using the AI Oracle by interacting with the Prompt contract using Etherscan:

1. In Prompt contract's `Read Contract` section, call `estimateFee` with specified `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.07.20 (2).png" alt=""><figcaption></figcaption></figure>

2. In Prompt contract's `Write Contract` section, call `calculateAIResult` with the fee (converted from wei to ether), `prompt`, and `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.10.10.png" alt=""><figcaption></figcaption></figure>

3. In the AIOracle contract, watch for a new transaction that fulfills the request you sent.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.17.png" alt=""><figcaption></figcaption></figure>

4. In Prompt contract's `Read Contract` section, call `getAIResult` with the previous `modelId` and `prompt` to see the AI inference result.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.57.png" alt=""><figcaption></figcaption></figure>
