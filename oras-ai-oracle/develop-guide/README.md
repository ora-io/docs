# Develop Guide

## Pre-requisites

#### Required

* Basic knowledge of Ethereum smart contract development ([tutorials](https://ethereum.org/en/developers/tutorials/))

#### Optional

* AI development experience

## Resources

Source code of OAO: [https://github.com/ora-io/OAO](https://github.com/ora-io/OAO)

For supported models in OAO and deployment addresses, see [Reference](../reference.md) page.

For example integrations and ideas to build, see [awesome-ora](https://github.com/ora-io/awesome-ora#-ai-oracle-cle-ecosystem).

Check out [video tutorial on interacting and building with OAO](https://www.youtube.com/watch?v=8fcJbeKN1uM).

{% embed url="https://www.youtube.com/watch?v=8fcJbeKN1uM" %}
Interact and build with OAO
{% endembed %}

## Workflow

OAO is a pull-based oracle, meaning user will get one response (AI inference result) on one request (AI prompt) in an on-demand basis.

1. The user contract sends the AI request to OAO on chain, by calling `requestCallback` function on the OAO contract.
2. Each AI request will initiate an opML request.
3. OAO will emit a `requestCallback` event which will be collected by opML node.
4. opML node will run the AI inference, and then upload the result on chain, waiting for the challenge period.
   1. During the challenge period, the opML validators will check the result, and challenge it if the submitted result is incorrect.
   2. If the submitted result is successfully challenged by one of the validators, the submitted result will be updated on chain.
   3. After the challenge period, the submitted result on chain is finalized.
5. When the result is uploaded or updated on chain, the provided result in opML will be dispatched to the user's smart contract via its specific callback function.

## Integration

### Overview

To interact with OAO, you will need to write your own contract.

To build with AI models of OAO, we provided an example of interaction to Llama model: [Prompt](https://github.com/ora-io/OAO/blob/main/contracts/Prompt.sol).

### Smart Contract Integration

1.  Inherit `AIOracleCallbackReceiver` in your contract and bind with a specific OAO address:

    ```solidity
    constructor(IAIOracle _aiOracle) AIOracleCallbackReceiver(_aiOracle) {}
    ```
2.  Write your callback function to handle the AI result from OAO. Note that only OAO can call this function:

    ```solidity
    function aiOracleCallback(uint256 requestId, bytes calldata output, bytes calldata callbackData) external override onlyAIOracleCallback()
    ```
3.  When you want to initiate an AI inference request, call OAO as follows:

    ```solidity
    aiOracle.requestCallback(modelId, input, address(this), gas_limit, callbackData);
    ```

### Application Integration with OAO Fee

Usage of OAO requires fee for each request.

It is required to obtain the current fee by calling `estimateFee` in OAO or your integrated contract with specific model id, then proceed to send request.

Flow of getting and setting fee is:

1. Call to read `estimateFee` (on OAO or your contract if implemented) for inference with certain model
2. Get estimated fee in wei (eg. [21300788080000000](https://sepolia.etherscan.io/unitconverter?wei=21300788080000000))
3. Call to write and request AI inference on your contract, and fill in estimated fee in ether (eg. [0.02130078808](https://sepolia.etherscan.io/unitconverter?wei=21300788080000000))
