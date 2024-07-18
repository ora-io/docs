---
description: https://ora.io/app/stake
---

# Staking

### Introduction

ORA Points Program Staking is designed to ensure the security of the upcoming fully decentralized AI Oracle network.

You can stake your assets, and receive ORA Points as reward by contributing to the decentralization of AI Oracle network secured by opML.

| Asset                        | Total Cap           | Points Per Day\*                   |
| ---------------------------- | ------------------- | ---------------------------------- |
| ETH Pool (ETH, stETH, STONE) | 10,000 in ETH & LST | 8n Points with n ETH & LST Staked  |
| OLM Pool (OLM)               | 300,000,000 in OLM  | 24n Points with 10,000n OLM Staked |

\*: Points are proportional to your staked amount. You will be getting points if you stake any amount.

#### Supported Assets

{% hint style="info" %}
You will still be able to participate in OLM's revenue sharing if OLM staked.
{% endhint %}

Currently, ORA Points Program Staking supports these assets to be staked in:

* [ETH](https://www.coingecko.com/en/coins/ethereum) (Native ETH)
* [stETH](https://www.coingecko.com/en/coins/lido-staked-ether) (Lido)
* [STONE](https://www.coingecko.com/en/coins/stakestone-ether) (StakeStone)
* [OLM](https://www.coingecko.com/en/coins/openlm-revshare-token) (OpenLM)

#### Total Staking Cap

At the first phase, ORA Points Program Staking is having a cap / limit on the total staked assets.

* **ETH & LST Pool (ETH, stETH, STONE)**: 10,000 in ETH & LST
* **OLM Pool (OLM)**: 300,000,000 in OLM

### Staking Guide

#### Stake

1\) Go to ORA Staking Page: [https://ora.io/app/stake](https://ora.io/app/stake).

2\) Select the token you want to stake, and enter amount.

<figure><img src="../.gitbook/assets/截屏2024-06-26 下午9.19.54.png" alt=""><figcaption></figcaption></figure>

3\) Press "CONFIRM", and sign the transaction in your wallet. You are receiving points once transaction is confirmed on blockchain.

4\) See your points in dashboard: [https://ora.io/app/tasks/dashboard](https://ora.io/app/tasks/dashboard). Please note your points will be distributed every day, instead of every hour.

#### Withdraw

{% hint style="info" %}
Withdraw will be enabled 1 month after the genesis of ORA Points Program Staking for effectively securing the AI Oracle network.
{% endhint %}

1\) Go to ORA Staking Page: [https://ora.io/app/stake](https://ora.io/app/stake).

2\) Switch to "WITHDRAW" tab.

<figure><img src="../.gitbook/assets/截屏2024-06-26 下午9.26.44.png" alt=""><figcaption></figcaption></figure>

3\) Select the staked token you want to withdraw, and enter amount.

4\) Press "INITIATE WITHDRAW", and sign the transaction in your wallet. You initiate withdraw once transaction is confirmed on blockchain.

{% hint style="info" %}
For ensuring the security of ORA Points Program Staking, all funds will go through 1 day before being eligible to be fully withdrawn.
{% endhint %}

5\) Switch to the second window of "WITHDRAW" tab by clicking the arrow button at the bottom right.

<figure><img src="../.gitbook/assets/截屏2024-06-26 下午9.34.25.png" alt=""><figcaption></figcaption></figure>

6\) Press "COMPLETE WITHDRAW" when the assets are eligible to be fully withdrawn, and sign the transaction in your wallet. You complete withdraw once transaction is confirmed on blockchain.

<figure><img src="../.gitbook/assets/截屏2024-06-26 下午9.36.07.png" alt=""><figcaption></figcaption></figure>

### Staking Points

Staking Points is measured based on the time-integrated amount staked in units of TOKEN \* days.

Here's the formula for points of one asset being staked, with `p` as total points awarded, `t` as the staking time if you stake for `n` days, `c` as the constant of staking points for different assets, `m` as the amount of staked asset.

$$
f(p) = \sum_{t=0}^{n} c_t*m
$$

The constant of staking points (equals to the points you get if you stake 1 unit of asset for 1 day):

* **ETH & LST Pool (ETH, stETH, STONE)**: 8. You will receive 8m points per m ETH staked every 24 hours.
* **OLM Pool (OLM)**: 0.0024. You will receive 24m points per 10,000m OLM staked every 24 hours.

In simpler words:

* You accumulate points over time when you stake into ORA Points Program Staking.
* Points are updated and awarded every day.
* You can stake multiple assets and earn points for all of them.

### Audit

Here is the audit report of ORA Staking: [Salus Security 2024-07-13](https://github.com/ora-io/audit-report-staking/blob/main/ORA\_staking-contract\_audit\_report\_2024-07-13.pdf).
