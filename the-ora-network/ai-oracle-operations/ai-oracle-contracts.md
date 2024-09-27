---
description: Quick Overview
---

# AI Oracle Contracts

## Workflow

AI Oracle is a pull-based oracle, meaning users will get one response (i.e. an AI inference result) from one request (i.e. a prompt) on-demand. Our batch mint feature enables one request to return multiple AI inference results in one response.

### Usage

1. **Initiate Request**: The user contract sends an inference request to AI Oracle by calling the `requestCallback` function.
2. **opML Request**: AI Oracle creates an opML request based on the user contract request.
3. **Event Emission**: AI Oracle emits a `requestCallback` event collected by the opML node.
4. **ML Inference**: The opML node performs the AI computation.
5. **Result Submission**: The opML node uploads the result on-chain.
6. **Callback Execution**: The result is dispatched to the user's smart contract via a callback function.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### Challenge Process

1. **Challenge Window**: Begins after the result is submitted on-chain (step 5 above).
2. **Verification**: opML validators or any network participant can check the results and challenge the output if it is incorrect.
3. **Result Update**: If a challenge is successful, the incorrect result is updated on-chain.
4. **Finalization**: After the challenge period, the result is finalized and immutable.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## Deployments

#### Deployed Contracts

* **AIOracle Contract**: [0xb880D47D3894D99157B52A7F869aB3B1E2D4349d](https://sepolia.etherscan.io/address/0xb880D47D3894D99157B52A7F869aB3B1E2D4349d)
* **Prompt Contract**: [0x5d6963003Ad172Fd1D2A2fD18bB3967eA7Aef1a2](https://sepolia.etherscan.io/address/0x5d6963003Ad172Fd1D2A2fD18bB3967eA7Aef1a2)

#### Available Models

* **LLaMA 3-8B**: Large Language Model (LLM) for text-based tasks.
* **Stable Diffusion**: Image generation model.

For more information refer to this page [https://docs.ora.io/doc/ora-network/references](https://docs.ora.io/doc/ora-network/references)

## Smart Contract Integration

To connect your smart contract with AI Oracle:

1. Inherit `AIOracleCallbackReceiver` in your contract and bind with a specific AI Oracle address:

```solidity
constructor(IAIOracle _aiOracle) AIOracleCallbackReceiver(_aiOracle) {}
```

1.  Write your callback function to handle the inference result from AI Oracle. Note that only AI Oracle can call this function:

    ```solidity
    function aiOracleCallback(uint256 requestId, bytes calldata output, bytes calldata callbackData) external override onlyAIOracleCallback()
    ```
2.  When you want to initiate an AI inference request, call AI Oracle as follows:

    ```solidity
    aiOracle.requestCallback(modelId, input, address(this), gas_limit, callbackData);
    ```

Usage of AI Oracle requires a fee for each request. You can request the current fee by:

1. Call to read `estimateFee` in AI Oracle or your integrated contract with the specific model ID
2. You’ll receive back the estimated fee in wei
3. Call to write and request the AI inference on your contract, filling in the estimated fee in ether

{% embed url="https://www.youtube.com/watch?v=8fcJbeKN1uM" %}
Interact and build with OAO
{% endembed %}

## Resources

Source code of OAO: [https://github.com/ora-io/OAO](https://github.com/ora-io/OAO)

For supported models in OAO and deployment addresses, see [Reference](references/) page.

For example integrations and ideas to build, see [awesome-ora](https://github.com/ora-io/awesome-ora#-ai-oracle-cle-ecosystem).

Check out [video tutorial on interacting and building with OAO](https://www.youtube.com/watch?v=8fcJbeKN1uM).
