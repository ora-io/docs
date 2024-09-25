---
description: Optimistic Privacy-Preserving AI onchain
---

# opp/ai

## **Introduction**

**opp/ai** (Optimistic Privacy-Preserving AI on Blockchain) is a novel framework that combines the efficiency of opML (Optimistic Machine Learning) with the privacy guarantees of zkML (Zero-Knowledge Machine Learning). By strategically partitioning machine learning (ML) models, opp/ai balances computational efficiency and data privacy, enabling secure and efficient AI services onchain.

The following is a comprehensive overview of opp/ai, including its architecture, technical components, and use cases.

***

## **Key Features of opp/ai**

* **Privacy Preservation**: Protects sensitive data and proprietary models by leveraging Zero-Knowledge Proofs (ZKPs) for critical components.
* **Balanced Efficiency**: Reduces zkML overhead by limiting its use to essential parts of the model while running the rest in opML.
* **Flexibility**: Allows customization of the model partitioning to tailor privacy and efficiency based on application requirements.
* **Security**: Combines cryptographic security from zkML with the economic security model of opML.

***

## **How opp/ai Works**

### **Model Partitioning Strategy**

opp/ai divides the ML model into submodels based on privacy requirements:

* **zkML Submodels**:
  * Components that handle sensitive data or proprietary algorithms.
  * Executed using Zero-Knowledge Proofs to ensure data and model confidentiality.
* **opML Submodels**:
  * Components where efficiency is prioritized over privacy.
  * Executed using the optimistic approach of opML for maximum efficiency.

**Example Partitioning**:

An ML model M is partitioned into:

* M\_zk (zkML Submodel): Handles sensitive computations.
* M\_op (opML Submodel): Handles non-sensitive computations.

### **Hybrid Execution**

* **Zero-Knowledge Proofs for zkML Submodels**:
  * The prover generates ZKPs for M\_zk without revealing sensitive data.
  * Proofs are submitted to the blockchain and verified by validators.
* **Optimistic Execution for opML Submodels**:
  * M\_op is executed efficiently off-chain.
  * Results are submitted to the blockchain by decentralized service providers and are assumed correct unless challenged.
* **Integration Mechanism**:
  * Outputs from M\_zk are used as inputs for M\_op and vice versa as necessary.
  * Ensures seamless integration of zkML and opML components.

***

## **Architecture**

opp/ai relies on the three major components of opML for opML submodels:

### **Fraud Proof Virtual Machine (FPVM)**

The FPVM is a specialized virtual machine designed for opML that can:

* **Execute and Verify Computation Steps**: Capable of performing individual computation steps to resolve disputes.
* **State Management**: Uses Merkle trees to represent and manage computation states efficiently.
* **Onchain Arbitration**: Runs on smart contracts, enabling the on-chain verification of disputed steps.

### **Machine Learning Engine**

The ML engine in opML is tailored for both native execution and fraud-proof scenarios:

* **Dual Compilation**: ML models are compiled twice:
  * **Native Execution**: Optimized for speed, utilizing multi-threading and GPU acceleration.
  * **Fraud-Proof VM Instructions**: Compiled into a machine-independent code for use in FPVM during disputes.
* **Determinism and Consistency**:
  * **Fixed-Point Arithmetic**: Ensures consistent results across different environments.
  * **Software-Based Floating-Point Libraries**: Guarantees cross-platform determinism.

### **Interactive Dispute Game**

An efficient protocol for resolving disputes:

* **Bisection Protocol**:
  * Iteratively narrows down the computation steps to find the exact point of disagreement.
  * Reduces the amount of data and computation needed for onchain verification.
* **Onchain Arbitration**:
  * Only the minimal necessary computation (usually a single step) is performed onchain.
  * Ensures disputes are resolved fairly and efficiently.

In addition to the opML components above, opp/ai incorporates the following zkML components:

### **Prover**

The prover generates ZKPs, such as zk-SNARKs, to demonstrate the validity of the ML inference.

### **On-chain Verifier**

The verifier smart contract efficiently validates the zero-knowledge proofs provided by the prover.

***

## **Workflow**

To achieve model privacy, the proofs of all zkML submodels should have their model inputs set as public inputs, while the model parameters or weights should be kept private or hashed. The workflow is as follows:

1. **Model Partitioning**:
   * The ML model is partitioned into zkML and opML submodels.
   * All submodels running in opML are published as a public model available to all potential submitters and challengers.
2. **Request Initiation**:
   * A user (requester) submits a request for an ML inference task.
3. **Computation and Submission**:
   * The prover receives the model input and computes the proof the zkML submodels, submitting them onchain for verifiers while also requesting to initiate opML service tasks for the opML submodels.
   * The submitter performs the opML service task, taking the result from the zkML submodels as input to the opML model and commits the results onchain.
4. **Dispute Resolution**:
   * The challengers validate the results and will start a dispute process with the submitter if they find any of them inaccurate. The dispute process will only apply to the specific opML submodel being challenged.
   * For opML submodels, disputes are resolved via the interactive dispute game using the FPVM.
   * For zkML submodels, the correctness is ensured by the cryptographic proofs.
5. **Finalization**:
   * Upon successful verification and resolution of disputes, the final result is confirmed on the blockchain.

***

## **Security Considerations**

### **Single Prover Trust Assumption**

In the context of preserving model privacy, the single prover trust assumption posits that only one trusted entity, the prover, has access to the model weights. All end users interact with this prover to generate zkML proofs without direct access to the model weights themselves.

This approach is designed to protect the confidentiality of the model while still enabling users to benefit from its predictive capabilities.

### **Model Extraction Attacks**

opp/ai acknowledges that attackers could attempt to reconstruct models through extensive queries due to the single prover trust assumption inherent to zkML.

In order to mitigate this, opp/ai can limit the number of allowed inferences or adjust the cost per inference to deter attacks.

### **Input Privacy vs. Model Privacy**

In order to ensure user input privacy, zkML proof generation should occur on local devices where model weights are distributed. However, this lends the model to reverse engineering attacks.

Given this limitation of zkML, the opp/ai framework instead focuses on model parameter privacy rather than input privacy.

***

## **Frequently Asked Questions**

1. **How does opp/ai differ from opML and zkML individually?**
   * opp/ai integrates both opML and zkML to provide a balance between efficiency and privacy. It uses zkML for sensitive computations and opML for the rest, whereas opML focuses on efficiency without privacy, and zkML provides privacy but with higher computational costs.
2. **What types of models are suitable for opp/ai?**
   * Models that can be partitioned based on privacy requirements. This includes models where certain layers or components handle sensitive data or proprietary algorithms.
3. **How do I decide which parts of my model should run in zkML vs. opML?**
   * Analyze the model to identify components that require privacy (e.g., layers with proprietary weights or handling sensitive data). These should run in zkML. Components where privacy is not a concern can run in opML for efficiency.
4. **What are the hardware requirements for opp/ai?**
   * **zkML Components**: May require machines with substantial resources for proof generation, especially for larger models.
   * **opML Components**: Can run on standard PCs with CPU/GPU capabilities.
5. **Is opp/ai practical for large-scale models?**
   * While zkML components can be resource-intensive, opp/ai reduces the overhead by only applying zkML to critical parts of the model. This makes it more practical than using zkML for the entire model.
6. **How does opp/ai handle input privacy?**
   * Input privacy is challenging due to potential reverse-engineering attacks. opp/ai focuses on model privacy and acknowledges limitations in input privacy with current zkML technologies.
7. **Can opp/ai be integrated with existing blockchain applications?**
   * Yes, opp/ai is designed to be flexible and can be integrated into existing applications that require both efficient and privacy-preserving AI capabilities.

***

### **Resources and Links**

* **opML Documentation**: [https://app.gitbook.com/o/rWlGmOlOvnmpt08RvxKm/s/llyHj70MVMOxu2WT7tZv/\~/changes/245/the-ora-network/fraud-proof-virtual-machine-fpvm/opml](https://app.gitbook.com/o/rWlGmOlOvnmpt08RvxKm/s/llyHj70MVMOxu2WT7tZv/\~/changes/245/the-ora-network/fraud-proof-virtual-machine-fpvm/opml)
* **Community and Support**:
  * **Discussion Forums**: [https://discord.gg/ora-io](https://discord.gg/ora-io)
* **Related Papers and Research**:
  * _opML: Optimistic Machine Learning on Blockchain:_ [https://arxiv.org/pdf/2401.17555](https://arxiv.org/pdf/2401.17555)
  * _opp/ai: Optimistic Privacy-Preserving AI on Blockchain:_ [https://arxiv.org/pdf/2402.15006](https://arxiv.org/pdf/2402.15006)

***

_For further questions or support, please reach out to the ORA team through the community channels listed above._
