---
description: Running ORA nodes with the Tora Validator Client
---

# Tora Validator Client

### Introduction

**Tora Validator** is a validator client of the AI Oracle network, written in TypeScript.

As the first released version of ORA node, it validates AI inference results submitted by AI Oracle nodes.

To enhance client diversity and further decentralize the network, future updates will introduce additional types of nodes.

<figure><img src="../../.gitbook/assets/tora fig thumbnail.png" alt=""><figcaption></figcaption></figure>

### What It Does

Tora Validator Node performs two main functions:

* **Validation**: It validates AI inference results by executing AI computations within the opML framework.
* **Blockchain Interaction**: The node interacts with the Onchain AI Oracle's smart contracts by monitoring AI requests and confirming validated inference results.

### Technical Details

Currently, Tora Validator supports the OpenLM model (model ID: 13) on the Ethereum mainnet. The node runs this model and confirms its AI inference results on-chain, contributing to the overall security and trustworthiness of the network.

### Tutorials

To encourage participation, Tora offers two options of client software for running the node:

* **Desktop App (Tora Launcher)**: A beginner-friendly approach for users who prefer a graphical interface.
* **CLI**: An advanced option for those comfortable with command-line operations, offering more control and flexibility.
