# Retrieve Historical AI Inference

If you want to retrieve your historical AI inference (eg. AIGC image), you can find them on blockchain explorer:

1. **Find your transaction for sending AI request, and enter the "Logs" tab.**\
   Example tx: [https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog](https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog)
2. **Access your `requestId` in "Logs" tab**\
   Example's case: "1928".
3. **In** [**OAO's smart contract**](./)**, look for the `Invoke Callback` transaction with the same `requestId`.**\
   Normally, this transaction will be around the same time as the one in step 1. To filter transactions by date, click "Advanced Filter" and then the button near "Age".
4. **Find the transaction for AI inference result, and enter the "Logs" tab.**\
   Example tx: [https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog](https://etherscan.io/tx/0xfbfdb2efcee23197c5ea8487368a905385c84afdc465cab43bc1ad01da773404#eventlog)
5. **Access output data.**\
   Example's case: "QmecBGR7dD7pRtY48FEKoeLVsmBTLwvdicWRkX9xz2NVvC" which is the IPFS hash that can be [accessed with IPFS gateway](https://ipfs.io/ipfs/QmecBGR7dD7pRtY48FEKoeLVsmBTLwvdicWRkX9xz2NVvC))
