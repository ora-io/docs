---
description: AI Oracle is a pull-based oracle built on opML
---

# AI Oracle Overview

## Introduction

AI Oracle is a pull-based oracle. This means users will get one response (an AI inference result) from one request (one prompt) on-demand. Our new batch mint feature enables one request to return multiple AI inference results in one response.

### Workflow

1. **Initiate Request**: The user contract sends an inference request to AI Oracle by calling the `requestCallback` function.
2. **opML Request**: AI Oracle creates an opML request based on the user contract request.
3. **Event Emission**: AI Oracle emits a `requestCallback` event collected by the opML node.
4. **ML Inference**: The opML node performs the AI model computation.
5. **Result Submission**: The opML node uploads the result on-chain.
6. **Callback Execution**: The result is dispatched to the user's smart contract via a callback function.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>AI Oracle and opML Architecture</p></figcaption></figure>

### Challenge Process

1. **Challenge Window**: Begins after the result is submitted on-chain (step 5 above).
2. **Verification**: opML validators or any network participant can check the results and challenge the output if it is incorrect.
3. **Result Update**: If a challenge is successful, the incorrect result is updated on-chain.
4. **Finality**: After the challenge period, the result is finalized onchain and made immutable.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## Simple Smart Contract Integration

To connect your smart contract with AI Oracle:

* Inherit `AIOracleCallbackReceiver` in your contract and bind with a specific AI Oracle address:

```solidity
constructor(IAIOracle _aiOracle) AIOracleCallbackReceiver(_aiOracle) {}
```

* Write your callback function to handle the inference result from AI Oracle. Note that only the AI Oracle can call this function:

```solidity
function aiOracleCallback(uint256 requestId, bytes calldata output, bytes calldata callbackData) external override onlyAIOracleCallback()
```

* When you want to initiate an AI inference request, call AI Oracle as follows:

```solidity
aiOracle.requestCallback(modelId, input, address(this), gas_limit, callbackData);
```

Usage of AI Oracle requires a fee for each request. You can request the current fee by:

1. Call to read `estimateFee` in AI Oracle or your integrated contract with the specific model ID
2. You’ll receive back the estimated fee in wei
3. Call to write and request the AI inference on your contract, filling in the estimated fee in ether

{% embed url="https://www.youtube.com/watch?v=8fcJbeKN1uM" %}
Interact and build with AI oracle
{% endembed %}

## Resources

Source code of AI Oracle: [https://github.com/ora-io/OAO](https://github.com/ora-io/OAO)

For supported models and deployment addresses, see [Reference](references/) page.

For example integrations and ideas to build, see [awesome-ora](https://github.com/ora-io/awesome-ora#-ai-oracle-cle-ecosystem).

Check out [video tutorial on interacting and building with ](https://www.youtube.com/watch?v=8fcJbeKN1uM)AI oracle.
