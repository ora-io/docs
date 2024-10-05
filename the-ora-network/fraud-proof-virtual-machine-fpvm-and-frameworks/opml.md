---
description: Scalable machine learning (ML) inference onchain
---

# opML

## **Introduction**

**opML** (Optimistic Machine Learning) is an innovative framework that enables efficient and scalable machine learning (ML) inference directly on the blockchain. By leveraging an optimistic approach inspired by optimistic rollups (e.g., Optimism and Arbitrum), opML overcomes the computational limitations of blockchains, allowing for the execution of large ML models without sacrificing decentralization or security.

opML is currently available via ORA’s [**AI Oracle**.](../ai-oracle-network/)

The following is a comprehensive overview of opML, including its architecture, technical components, and frequently asked questions.

***

## **Key Features of opML**

* **High Efficiency**: Computations are performed off-chain in optimized environments and only minimal data is processed on-chain during disputes.
* **Cost-Effectiveness**: Reduces computational costs by avoiding the expensive proof generation required in Zero-Knowledge Machine Learning (zkML).
* **Decentralization**: Maintains the decentralized ethos of blockchain by enabling onchain verification without relying on centralized servers.
* **Scalability**: Capable of handling extensive computations that are impractical with traditional onchain methods.
* **Accessibility**: Opens up advanced AI models and capabilities to decentralized applications.

***

## **How opML Works**

opML combines **Optimistic Execution** with a **Fraud-Proof Mechanism**.

#### **Optimistic Execution**

opML operates on the principle of **optimistic execution**, which assumes that the ML computations submitted are correct by default. This approach allows computations to be performed offchain in optimized environments, significantly reducing the computational burden on the blockchain.

* **Assumption of Correctness**: Results are accepted unless proven otherwise.
* **Efficiency**: By not requiring immediate verification, the system avoids unnecessary computational overhead.

#### **Fraud-Proof Mechanism**

To ensure security and correctness, opML incorporates the following fraud-proof mechanism:

1. **Submission of Results**: The service provider (submitter) performs the ML computation offchain and submits the result to the blockchain.
2. **Verification Period**: Validators (or challengers) have a predefined period (challenge period) to verify the correctness of the submitted result.
3. **Dispute Resolution**:
   * If a validator detects an incorrect result, they initiate an **Interactive Dispute Game**.
   * The dispute game efficiently pinpoints the exact computation step where the error occurred.
4. **On-Chain Verification**: Only the disputed computation step is verified on-chain using the **Fraud Proof Virtual Machine (FPVM)**, minimizing resource usage.
5. **Finalization**: If no disputes are raised during the challenge period, or after disputes are resolved, the result is finalized on the blockchain.

***

## **Optimizations in opML**

* **Deterministic ML**: Randomness and variability in floating-point computations results in inconsistency of ML results. To address this, opML fixes the random seed so that outputs can be verified across multiple instances of the model. \*\*\*\*
* **Separated Execution from Proving**: opML compiles the source code twice for native execution and for the fraud-proof VM instructions. This allows for computations to be performed in optimized native environments ensuring fast execution while simultaneously proving based on machine-independent code.
* **Lazy Loading Design**: Loads only necessary data into the FPVM during the dispute phase to overcome memory limitations of the VM.
* **Attention Challenge**: Validators are randomly selected to verify computations. Failing to respond when selected results in penalties, motivating active participation.
* **Economic Security**: Validators and submitters stake tokens to participate. Dishonest behavior results in penalties (loss of stake). By staking tokens, both submitters and validators have economic incentives to behave honestly.

***

## **Architecture**

#### **Fraud Proof Virtual Machine (FPVM)**

The FPVM is a specialized virtual machine designed for opML that can:

* **Execute and Verify Computation Steps**: Capable of performing individual computation steps to resolve disputes.
* **State Management**: Uses Merkle trees to represent and manage computation states efficiently.
* **Onchain Arbitration**: Runs on smart contracts, enabling the on-chain verification of disputed steps.

#### **Machine Learning Engine**

The ML engine in opML is tailored for both native execution and fraud-proof scenarios:

* **Dual Compilation**: ML models are compiled twice:
  * **Native Execution**: Optimized for speed, utilizing multi-threading and GPU acceleration.
  * **Fraud-Proof VM Instructions**: Compiled into a machine-independent code for use in FPVM during disputes.
* **Determinism and Consistency**:
  * **Fixed-Point Arithmetic**: Ensures consistent results across different environments.
  * **Software-Based Floating-Point Libraries**: Guarantees cross-platform determinism.

#### **Interactive Dispute Game**

An efficient protocol for resolving disputes:

* **Bisection Protocol**:
  * Iteratively narrows down the computation steps to find the exact point of disagreement.
  * Reduces the amount of data and computation needed for onchain verification.
* **Onchain Arbitration**:
  * Only the minimal necessary computation (usually a single step) is performed onchain.
  * Ensures disputes are resolved fairly and efficiently.

***

## **Workflow**

1. **Request Initiation**: A user (requester) submits a request for an ML inference task.
2. **Computation and Submission**:
   * The submitter performs the computation off-chain using the optimized ML engine.
   * Results are submitted to the blockchain.
3. **Challenge Period**:
   * Validators verify the correctness of the result.
   * If no disputes are raised within the predefined period, the result is accepted.
4. **Dispute Resolution** (if necessary):
   * A validator initiates the dispute game if an incorrect result is detected.
   * The exact computation step in dispute is identified.
   * On-chain verification is performed using the FPVM.
5. **Finalization**: The result is finalized after successful verification or dispute resolution.

***

## **Security Considerations**

#### **AnyTrust Assumption**

* **Definition**: The system is secure as long as at least one validator is honest.
* **Implications**:
  * Even if multiple validators are malicious, a single honest validator can ensure correctness.
  * Encourages decentralization and wide participation to strengthen security.

#### **Verifier Dilemma and Solution**

* **Verifier Dilemma**:
  * Validators may choose not to verify computations to save resources, potentially allowing incorrect results.
* **Our Solution**:
  * Implementing the Attention Challenge mechanism detailed above encourages validators to participate.
  * Economic incentives ensure that the cost of cheating outweighs potential gains.

***

## **Frequently Asked Questions**

1. **What makes opML different from zkML?**
   * opML focuses on efficiency and scalability by using an optimistic approach without zero-knowledge proofs. zkML provides strong privacy guarantees but is resource-intensive and less practical for large models. The use of [opp/ai ](https://app.gitbook.com/o/rWlGmOlOvnmpt08RvxKm/s/llyHj70MVMOxu2WT7tZv/\~/changes/245/the-ora-network/fraud-proof-virtual-machine-fpvm/opp-ai)enables the use of opML with privacy guarantees.&#x20;
2. **How does opML ensure security without zero-knowledge proofs?**
   * opML relies on a fraud-proof mechanism and the AnyTrust assumption. Validators can challenge incorrect results, and economic incentives discourage dishonest behavior.
3. **What happens if no validators challenge an incorrect result?**
   * The economic incentives and attention challenge mechanism are designed to ensure validators participate. However, if all validators are dishonest or fail to challenge, the system could accept incorrect results, highlighting the importance of validator participation.
4. **Can opML handle private data or proprietary models?**
   * opML assumes that data and models are not sensitive. For applications requiring privacy, consider using opp/ai, which integrates opML with zkML components for privacy preservation.
5. **What are the hardware requirements for running opML?**
   * opML is designed to run on standard PCs with CPU/GPU capabilities. No specialized hardware is required.
6. **How does the dispute resolution process impact performance?**
   * Disputes are rare and only involve verifying minimal computation steps on-chain. The impact on performance is minimal compared to the overall efficiency gains. The dispute resolution process can also be optimized by zkfp.
7. **Is opML open-source?**
   * Yes, opML is open-sourced. You can access the repository at[https://github.com/ora-io/opml](https://github.com/ora-io/opml). New versions will shortly be released.&#x20;

***

## **Resources and Links**

* **opML GitHub Repository**: [https://github.com/ora-io/opml](https://github.com/ora-io/opml)
* **opML Paper**: [https://arxiv.org/pdf/2401.17555](https://arxiv.org/pdf/2401.17555)
* **Community and Support**:
  * **Discussion Forums**:
  * **Issue Tracker**: [https://github.com/ora-io/opml/issues](https://github.com/ora-io/opml/issues)

***

_For any further questions or support, feel free to reach out to the ORA team through the community channels listed above._
