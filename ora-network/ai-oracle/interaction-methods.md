---
description: Non-developer user guides
---

# Interaction Methods

As a user, to interact with AI Oracle, you can:

* Use the [AI.ORA.IO](https://ai.ora.io/) frontend- view our [video tutorial](https://www.youtube.com/watch?v=8fcJbeKN1uM)
* Directly via the Prompt contract on Etherscan

#### Via Etherscan

1. In Prompt contract's `Read Contract` section, call `estimateFee` with specified `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.07.20 (2).png" alt=""><figcaption></figcaption></figure>

2. In Prompt contract's `Write Contract` section, call `calculateAIResult` with fee (converted from wei to ether), `prompt`, and `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.10.10.png" alt=""><figcaption></figcaption></figure>

3. In the AI Oracle contract, look for the new transaction that fulfills the request you sent.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.17.png" alt=""><figcaption></figcaption></figure>

4. In Prompt contract's `Read Contract` section, call `getAIResult` with previous `modelId` and `prompt` to view the AI inference result.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.57.png" alt=""><figcaption></figcaption></figure>

