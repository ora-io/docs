# Develop Guide

## Workflow

1. The user contract sends the AI request to OAO on chain, by calling `requestCallback` function on the OAO contract.
2. Each AI request will initiate an opML request.
3. OAO will emit a `requestCallback` event which will be collected by opML node.
4. opML node will run the AI inference, and then upload the result on chain, waiting for the challenge period.
   1. During the challenge period, the opML validators will check the result, and challenge it if the submitted result is incorrect.
   2. If the submitted result is successfully challenged by one of the validators, the submitted result will be updated on chain.
   3. After the challenge period, the submitted result on chain is finalized.
5. When the result is uploaded or updated on chain, the provided result in opML will be dispatched to the user's smart contract via its specific callback function.

## Integration

To integrate with OAO, you will need to write your own contract.

You can take a look at this example ([Prompt.sol](https://sepolia.etherscan.io/address/0x5d6963003Ad172Fd1D2A2fD18bB3967eA7Aef1a2#code#F3#L1)) we created to build your own.

```solidity
contract Prompt is AIOracleCallbackReceiver {
    event promptsUpdated(
        uint256 modelId,
        string input,
        string output
    );

    event promptRequest(
        address sender, 
        uint256 modelId,
        string prompt
    );

    /// @notice Initialize the contract, binding it to a specified AIOracle.
    constructor(IAIOracle _aiOracle) AIOracleCallbackReceiver(_aiOracle) {}

    /// @notice Gas limit set on the callback from AIOracle.
    /// @dev Should be set to the maximum amount of gas your callback might reasonably consume.
    uint64 private constant AIORACLE_CALLBACK_GAS_LIMIT = 5000000;

    // uint256: modelID, 0 for Llama, 1 for stable diffusion
    // 1.string => 2.string: 1.string: prompt, 2.string: text (for llama), cid (for sd) 
    mapping(uint256 => mapping(string => string)) public prompts;

    function getAIResult(uint256 modelId, string calldata prompt) external view returns (string memory) {
        return prompts[modelId][prompt];
    }

    // only the AI Oracle can call this function
    function storeAIResult(uint256 modelId, bytes calldata input, bytes calldata output) external onlyAIOracleCallback() {
        prompts[modelId][string(input)] = string(output);
        emit promptsUpdated(modelId, string(input), string(output));
    }

    function calculateAIResult(uint256 modelId, string calldata prompt) external {
        bytes memory input = bytes(prompt);
        aiOracle.requestCallback(
            modelId, input, address(this), this.storeAIResult.selector, AIORACLE_CALLBACK_GAS_LIMIT
        );
        emit promptRequest(msg.sender, modelId, prompt);
    }
}
```
