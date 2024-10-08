---
description: An AI Oracle powered Optimistic Machine Learning (opML)
---

# AI Oracle Network



<table data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td></td><td><p><a href="build-with-ai-oracle.md">Build Using ORA's AI Oracle</a></p><p><a href="./#components">🔮</a></p></td><td></td></tr><tr><td></td><td><p><a href="../node-operator-guide/tora-validator-client.md">Operate a Node:</a></p><p><a href="../node-operator-guide/tora-validator-client.md">TORA  Client </a></p><p><a href="./#components">💻</a></p></td><td></td></tr><tr><td></td><td><a href="../fraud-proof-virtual-machine-fpvm-and-frameworks/">Learn: Fraud Proof Virtual Machine (FPVM) </a>⚙️</td><td></td></tr></tbody></table>



**ORA's AI Oracle** is a verifiable oracle protocol that allows developers to create smart contracts and applications that ingest verifiable machine learning (ML) inferences directly on the blockchain.

<figure><img src="../../.gitbook/assets/Group 1000006228.png" alt=""><figcaption></figcaption></figure>

AI Oracle is powered by **Optimistic Machine Learning (opML)**, offering a verifiable, transparent, and decentralized way to integrate advanced ML models like LLaMA 3 and Stable Diffusion into smart contracts.

AI Oracle offers:

* **Scalability:** Can run any ML model onchain without prohibitive overhead.
* **Efficiency:** Reduces computational time and cost compared to zkML methods.
* **Practicality:** Easily integrates into applications by using existing blockchain infrastructure.
* **Verifiability:** Leverages fraud proofs to provide applications and users with assurances about computational integrity.

## Components

AI Oracle comprises a set of smart contracts and off-chain components:

1. **opML Contract**: Handles fraud proofs and challenges to ensure on-chain verifiability of ML computations.
2. **AIOracle Contract**: Connects the opML node with on-chain callers to process ML requests and integrates various ML models.
3. **User Contract**: Customizable contracts that initiate AI inference requests and receive results from directly from AI Oracle.
4. **ORA Nodes**: Machines that run the **Tora Client** that interact with the ORA network. Nodes currently perform two functions: submit or validate inference results.

<figure><img src="../../.gitbook/assets/图1.png" alt=""><figcaption></figcaption></figure>
