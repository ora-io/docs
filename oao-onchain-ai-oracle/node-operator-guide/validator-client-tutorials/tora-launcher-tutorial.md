# Tora Launcher - Tutorial

### Introduction

Tora Launcher is a multi-platform Tora client running as a desktop application.

Users with any level of experience can use it to start up and run their own Tora node, just like running a desktop wallet.

Currently, Tora Launcher supports MacOS, Linux, and Windows.

Releases can be found here: [Download Tora Launcher](https://github.com/ora-io/tora-electron-releases/releases/).

### Guide for MacOS

{% hint style="info" %}
This is the guide for MacOS version. If you are using other operating systems, please note there may be changes.
{% endhint %}

#### 1) Download

Go to [releases page](https://github.com/ora-io/tora-electron-releases/releases/), find the release tagged with "Latest", and download the file ending with .dmg.

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午1.54.30.png" alt=""><figcaption></figcaption></figure>

#### 2) Install App

{% hint style="info" %}
If you encounter issues when starting up the app, please follow [this guide](https://www.easeus.com/mac-file-recovery/cant-open-from-unidentified-developer.html) to verify the app on your device.
{% endhint %}

Double click the .dmg file you just downloaded, and follow the guide on your device to install.

#### 3) Install Tora Docker Image

After opening up the app, you will need to install the Tora docker image that includes the OpenLM model.

Click on "INSTALL TORA".

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午2.01.08.png" alt=""><figcaption></figcaption></figure>

It is required to keep [docker app](https://docs.docker.com/engine/install/) open when installing. If you don't have docker open when going into this step, you will need to restart Tora app.

#### 4) Configure Node

After installation, you will see the app's main screen.

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午2.10.53.png" alt=""><figcaption></figcaption></figure>

Click on "SETTING".

Enter configurations to all required fields:

* PRIVATE KEY: the private key that you use for the node that pays gas with sufficient balance for node operations on blockchain. Please note: it is recommended to use a separate wallet other than your daily used wallet.
* MODEL: the AI model in Onchain AI Oracle that you want to run in your node.
* NETWORK: the network that you submit validation results.
* WEBSOCKET URL and JSON-RPC URL: the RPC endpoints that you use for getting blockchain data. Default RPCs are provided.

Scroll down and click on "START" to start your node.

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午2.24.04.png" alt=""><figcaption></figcaption></figure>

If you are starting the node for the first time, you are required to set up password.

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午2.18.31.png" alt=""><figcaption></figcaption></figure>

#### 5) Running the node

When node is running, you will be see the status on the top-right corner and "NODE" page.

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午2.25.41.png" alt=""><figcaption></figcaption></figure>

You can also check out logs in "LOG" page.

<figure><img src="../../../.gitbook/assets/截屏2024-09-09 上午2.24.54.png" alt=""><figcaption></figcaption></figure>

For any question, please join [our discord](https://discord.gg/ora-io).
