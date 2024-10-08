---
description: Staking to earn points
---

# Staking

### Introduction

Staking is designed to ensure the security of the fully decentralized AI Oracle network in the future. Our point system is being used reward early adopters.&#x20;

| Pool (Asset)                  | Total Cap                | Points Per Day\*                        | Locking  |
| ----------------------------- | ------------------------ | --------------------------------------- | -------- |
| ETH & LST (ETH, stETH, STONE) | 10,000 in ETH & LST      | 8n Points per n ETH / LST Staked        | None     |
| OLM Flexible (OLM)            | 300,000,000 in OLM       | 24n Points per 10,000n OLM Staked       | None     |
| OLM Locked (OLM)              | 300,000,000 in OLM       | 48n Points per 10,000n OLM Staked       | 6 Months |
| Stablecoin (USDT & USDC)      | 1,000,000 in USDT & USDC | 3n Points per 3,000n USDT / USDC Staked | None     |

\*: Points are proportional to your staked amount.

#### Supported Assets

{% hint style="info" %}
You will still be able to participate in OLM's revenue sharing if OLM is staked.
{% endhint %}

Currently, ORA Points Program Staking supports these assets to be staked in:

* [ETH](https://www.coingecko.com/en/coins/ethereum) (Native ETH)
* [stETH](https://www.coingecko.com/en/coins/lido-staked-ether) (Lido)
* [STONE](https://www.coingecko.com/en/coins/stakestone-ether) (StakeStone)
* [OLM](https://www.coingecko.com/en/coins/openlm-revshare-token) (OpenLM)
* [USDT](https://www.coingecko.com/en/coins/tether) (Tether)
* [USDC](https://www.coingecko.com/en/coins/usdc) (USDC)

#### Total Staking Cap

At the first phase, ORA Points Program Staking is having a cap / limit on the total staked assets.

* **ETH & LST Pool (ETH, stETH, STONE)**: 10,000 in ETH & LST
* **OLM Flexible Pool (OLM)**: 300,000,000 in OLM
* **OLM Locked Pool (OLM)**: 300,000,000 in OLM
* **Stablecoin Pool (USDT & USDC)**: 1,000,000 in USDT & USDC

### Staking Guide

#### Stake

1\) Go to ORA Staking Page: [https://ora.io/app/stake](https://ora.io/app/stake).

2\) Choose the pool you want to stake, click on the arrow to open staking page.

<figure><img src="../.gitbook/assets/截屏2024-08-10 上午4.08.30.png" alt=""><figcaption></figcaption></figure>

3\) Select the token you want to stake, and enter amount.

<figure><img src="../.gitbook/assets/截屏2024-08-10 上午4.10.35.png" alt=""><figcaption></figcaption></figure>

4\) Press "CONFIRM", and sign the transaction in your wallet. Points are received once the transaction is confirmed on blockchain.

5\) See your points in dashboard: [https://ora.io/app/tasks/dashboard](https://ora.io/app/tasks/dashboard).&#x20;

#### Migrate from OLM (Flexible) to OLM (Locked)

If you have already staked into OLM (Flexible), and want to migrate these staked tokens to OLM (Locked), you do not need to withdraw then re-stake. You may directly migrate from OLM (Flexible) to OLM (Locked).

1\) Go to ORA Staking Page: [https://ora.io/app/stake](https://ora.io/app/stake).

2\) Choose OLM (Flexible) which you've already staked, click on the arrow to open staking page.

<figure><img src="../.gitbook/assets/截屏2024-08-11 下午3.17.45.png" alt=""><figcaption></figcaption></figure>

3\) Switch to "CHANGE POOL" tab. Select the staked token you want to migrate, and enter amount.

<figure><img src="../.gitbook/assets/截屏2024-08-11 下午3.24.12 (1).png" alt=""><figcaption></figcaption></figure>

4\) Press "CHANGE POOL", and sign the transaction in your wallet. You will migrate your asset to OLM (Locked) once transaction is confirmed on blockchain.

#### Withdraw

1\) Go to ORA Staking Page: [https://ora.io/app/stake](https://ora.io/app/stake).

2\) Choose the pool you staked, or start from the dashboard page ([https://www.ora.io/app/tasks/dashboard](https://www.ora.io/app/tasks/dashboard)), click on the arrow to open staking page.

<figure><img src="../.gitbook/assets/截屏2024-08-10 上午4.08.30 (1).png" alt=""><figcaption></figcaption></figure>

3\) Switch to "WITHDRAW" tab. Select the staked token you want to withdraw, and enter amount.

<figure><img src="../.gitbook/assets/截屏2024-08-10 上午4.21.01 (1).png" alt=""><figcaption></figcaption></figure>

4\) Press "INITIATE UNSTAKE", and sign the transaction in your wallet. You initiate unstake once transaction is confirmed on blockchain.

{% hint style="info" %}
For ensuring the security of ORA Points Program Staking, all funds will go through 1 day before being eligible to be fully withdrawn.
{% endhint %}

5\) Switch to the second window of "WITHDRAW" tab by clicking the "WITHDRAW" button at the top right.

<figure><img src="../.gitbook/assets/截屏2024-08-10 上午4.23.38.png" alt=""><figcaption></figcaption></figure>

6\) Press "CLAIM WITHDRAW" when the assets are eligible to be fully withdrawn at given time, and sign the transaction in your wallet. You complete withdraw once transaction is confirmed on blockchain.

<figure><img src="../.gitbook/assets/截屏2024-08-10 上午4.24.36.png" alt=""><figcaption></figcaption></figure>

### Staking Points

Staking Points is measured based on the time-integrated amount staked in units of TOKEN \* days.

Here's the formula for points of one asset being staked, with `p` as total points awarded, `t` as the staking time if you stake for `n` days, `c` as the constant of staking points for different assets, `m` as the amount of staked asset.

$$
f(p) = \sum_{t=0}^{n} c_t*m
$$

The constant of staking points (equals to the points you get if you stake 1 unit of asset for 1 day):

* **ETH & LST Pool (ETH, stETH, STONE)**: 8. You will receive 8n points per n ETH / LST staked every 24 hours.
* **OLM Flexible Pool (OLM)**: 0.0024. You will receive 24n points per 10,000n OLM staked every 24 hours.
* **OLM Locked Pool (OLM)**: 0.0048. You will receive 48n points per 10,000n OLM staked every 24 hours.
* **Stablecoin Pool (OLM)**: 0.001. You will receive 3n points per 3,000n USDT / USDC staked every 24 hours.

Note:

* Points are updated and awarded every day.
* You may stake multiple assets to earn points.

### Audit

Here is the audit report of ORA Staking: [Salus Security 2024-07-13](https://github.com/ora-io/audit-report-staking/blob/main/ORA\_staking-contract\_audit\_report\_2024-07-13.pdf).
