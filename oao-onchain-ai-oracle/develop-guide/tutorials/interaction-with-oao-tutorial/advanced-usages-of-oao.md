# Advanced Usages of OAO

In this tutorial, we are providing advanced usages on Interaction with OAO including Nested Inference.

## Prerequisites

* Good understanding of [.](./ "mention")

### 1. Nested Inference

We'll modify [Prompt](https://github.com/ora-io/Interaction\_With\_OAO\_Template/blob/main/src/Prompt.sol) contract to support nested inference request. NestedCallback contract should execute multiple inference requests in 1 transaction. In our example, it will call Llama3 model first, then use inference result as the prompt to another request to StableDiffusion model.

The main goal of this tutorial is to understand what changes we need to make to Prompt contract in order to implement logic for various use cases.

#### Use Cases

Some of the use cases for nested inference call could be:

* generate the prompt with LLM for AIGC (AI Generated Content) NFT
* extract data from the data set then visual data with different models
* add transcript to video, then translate it to different languages with different models

💡 This is executed within a single transaction, which simplifies user experience when interacting with your AI dapp.

#### Implementation Steps

1. modify `CalculateAIResult` method to support multiple requests
2. modify `aiOracleCallback` with the logic to handle second inference request

💡 When estimating gas cost for the callback, we should take both models into the consideration.

#### CalculateAIResult

As we now have additional function parameter for second model id. Not that we encode and forward `model2Id` as a callback data in `aiOracle.requestCallback` call.

```solidity
 function calculateAIResult(uint256 model1Id, uint256 model2Id, string calldata model1Prompt) payable external returns (uint256) {
    bytes memory input = bytes(model1Prompt);
    uint256 model1Fee = estimateFee(model1Id);
    uint256 requestId = aiOracle.requestCallback{value: model1Fee}(
        model1Id, input, address(this), callbackGasLimit[model1Id], abi.encode(model2Id)
    );
    AIOracleRequest storage request = requests[requestId];
    request.input = input;
    request.sender = msg.sender;
    request.modelId = model1Id;
    emit promptRequest(requestId, msg.sender, model1Id, model1Prompt);
    return requestId;
}
```

#### aiOracleCallback

The main change here is the within "if" block. If the callback data (`model2Id`) is returned, we want to execute second inference request to OAO.&#x20;

Output from the first inference call, will be passed to second one. This allows for interesting use cases, where you can combine text-to-text (eg. Llama3) and text-to-image (eg. Stable-Diffusion) models.&#x20;

If nested inference call is not successful the whole function will revert.

💡 When interacting with the contract from the client side, we need to pass cumulative fee (for both models), then for each inference call we need to pass part of that cumulative fee. This is why we are calling `estimateFee` for `model2Id`.

```solidity
function aiOracleCallback(uint256 requestId, bytes calldata output, bytes calldata callbackData) external payable override onlyAIOracleCallback() {
    AIOracleRequest storage request = requests[requestId];
    require(request.sender != address(0), "request does not exist");
    request.output = output;
    prompts[request.modelId][string(request.input)] = string(output);

    //if callbackData is not empty decode it and call another inference
    if(callbackData.length != 0){
        (uint256 model2Id) = abi.decode(callbackData, (uint256));
        uint256 model2Fee = estimateFee(model2Id);

        (bool success, bytes memory data) = address(aiOracle).call{value: model2Fee}(abi.encodeWithSignature("requestCallback(uint256,bytes,address,uint64,bytes)", model2Id, output, address(this), callbackGasLimit[model2Id], ""));
        require(success, "failed to call nested inference");

        (uint256 rid) = abi.decode(data, (uint256));
        AIOracleRequest storage recursiveRequest = requests[rid];
        recursiveRequest.input = output;
        recursiveRequest.sender = msg.sender;
        recursiveRequest.modelId = model2Id;
        emit promptRequest(rid, msg.sender, model2Id, "");
    }

    emit promptsUpdated(requestId, request.modelId, string(request.input), string(output), callbackData);
}
```

#### Interaction with Contract

This is an example of contract interaction from Foundry testing environment. Note that we're estimating fee for both models and passing cumulative amount during the function call (we're passing slightly more to ensure that the call will execute if the gas price changes).&#x20;

```solidity
PromptNestedInference prompt = new PromptNestedInference(IAIOracle(OAO_PROXY));

uint256 stableDiffusionFee = prompt.estimateFee(STABLE_DIFFUSION_ID);
uint256 llamaFee = prompt.estimateFee(LLAMA_ID);

uint256 requestId = prompt.calculateAIResult{value: ((stableDiffusionFee + llamaFee)*11/10)}(STABLE_DIFFUSION_ID, LLAMA_ID, SD_PROMPT);
```

#### Conclusion

In this tutorial we explained what functions need to be changed to implement different logic in your Prompt contract. Depending on the use case, new state variables and events could be defined as well.

You can also check the full implementation of [PromptNestedInference](https://github.com/ora-io/Interaction\_With\_OAO\_Template/blob/main/src/PromptNestedInference.sol).
