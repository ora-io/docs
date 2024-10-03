# Non-Developer Guides

### Using AI Oracle

As a user, to interact with AI Oracle, you can:

* **Use the** [**AI.ORA.IO**](https://ai.ora.io/) **frontend- view our** [**video tutorial**](https://www.youtube.com/watch?v=8fcJbeKN1uM)
* **Directly via the Prompt contract on Etherscan**

#### Via Etherscan

1. In Prompt contract's `Read Contract` section, call `estimateFee` with specified `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.07.20 (2).png" alt=""><figcaption></figcaption></figure>

2. In Prompt contract's `Write Contract` section, call `calculateAIResult` with fee (converted from wei to ether), `prompt`, and `modelId`.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.10.10.png" alt=""><figcaption></figcaption></figure>

3. In the AI Oracle contract, look for the new transaction that fulfills the request you sent.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.17.png" alt=""><figcaption></figcaption></figure>

4. In Prompt contract's `Read Contract` section, call `getAIResult` with previous `modelId` and `prompt` to view the AI inference result.

<figure><img src="../../.gitbook/assets/截屏2024-03-19 上午11.16.57.png" alt=""><figcaption></figcaption></figure>

### Retrieve Historical AI Inference

If you want to retrieve your historical AI inference (eg. AIGC image), you can find them on blockchain explorer:

1. **Find your transaction for sending AI request, and enter the "Logs" tab.**\
   Example tx: [https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog](https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog)
2. **Access your `requestId` in "Logs" tab**\
   Example's case: "1928".
3. **In** [**OAO's smart contract**](references/)**, look for the `Invoke Callback` transaction with the same `requestId`.**\
   Normally, this transaction will be around the same time as the one in step 1. To filter transactions by date, click "Advanced Filter" and then the button near "Age".
4. **Find the transaction for AI inference result, and enter the "Logs" tab.**\
   Example tx: [https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog](https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog)
5. **Access output data.**\
   Example's case: "QmecBGR7dD7pRtY48FEKoeLVsmBTLwvdicWRkX9xz2NVvC" which is the IPFS hash that can be [accessed with IPFS gateway](https://ipfs.io/ipfs/QmecBGR7dD7pRtY48FEKoeLVsmBTLwvdicWRkX9xz2NVvC))
