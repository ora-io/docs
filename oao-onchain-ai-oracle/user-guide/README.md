---
description: Usage Guide for Anyone to Use Onchain AI Directly as User
---

# User Guide

As a user, to interact with AI Oracle, you can:

* Use [AI.ORA.IO](https://ai.ora.io/) frontend.
* Interact with Prompt contract directly on Etherscan

### 1. Use ORA's Frontend Interface

We built an interface for users to interact with Onchain AI Oracle directly.

1. Go to [AI.ORA.IO](https://ai.ora.io/)
2. Enter your prompt
3. Send transaction
4. See AI inference result

Check out the [video tutorial](https://www.youtube.com/watch?v=8fcJbeKN1uM) if you have any question.

### 2. Interact on Etherscan

Here's the guide to use AI Oracle by interacting with Prompt contract using Etherscan:

1. In Prompt contract's `Read Contract` section, call `estimateFee` with specified `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.07.20 (2).png" alt=""><figcaption></figcaption></figure>

2. In Prompt contract's `Write Contract` section, call `calculateAIResult` with fee (converted from wei to ether), `prompt`, and `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.10.10.png" alt=""><figcaption></figcaption></figure>

3. In AIOracle contract, watch for new transaction that fulfills the request you sent.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.17.png" alt=""><figcaption></figcaption></figure>

4. In Prompt contract's `Read Contract` section, call `getAIResult` with previous `modelId` and `prompt` to see the AI inference result.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.57.png" alt=""><figcaption></figcaption></figure>

