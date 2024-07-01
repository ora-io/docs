# opp/ai

[opp/ai (Optimistic Privacy-Preserving AI)](https://arxiv.org/abs/2402.15006), invented by ORA, represents an endgame onchain AI framework and an innovative approach to addressing the challenges of privacy and computational efficiency in blockchain-based machine learning systems. Opp/ai integrates Zero-Knowledge Machine Learning (zkML) for privacy with Optimistic Machine Learning (opML) for efficiency, creating a hybrid model tailored for onchain AI.

Opp/ai, as the latest fusion of zkML and opML, can include any zkML approach. It means that advances in zkML will be directly reflected in opp/ai.

### Onchain Fine-tuned Model with Privacy

Opp/ai can be utilized to conceal the fine-tuning weights of models where the majority of the weights are already publicly available. This is particularly relevant for open-source models that have been fine-tuned for specialized tasks. For instance, the LoRA weights in the attention layers of the Stable Diffusion model can be protected using opp/ai framework.

This capability is crucial for preserving the proprietary enhancements made to publicly shared models, ensuring that while the base model remains accessible, the unique adaptations that provide competitive advantage remain confidential.

### Use-cases

**Individual voice tuning in text-to-voice models:** Text-to-voice service providers may offer personalized voice models that are tailored to the individual's voice characteristics. These personalized models are sensitive and contain valuable data. The opp/ai framework can ensure that the personalized voice model's parameters remain confidential while still offering the service to end-users verifiably.

**Financial sector:** Trading algorithms are developed to predict market movements and execute trades automatically. These algorithms are highly valuable and contain sensitive strategies that firms wish to protect. A financial institution could use the opp/ai framework to conceal the weights of a model that has been specifically tuned to its trading strategy.

**Gaming industry:** AI models are used to create challenging and engaging non-player characters (NPCs). Game developers may fine-tune these models to create unique behaviors or strategies that are specific to their game. By using the opp/ai framework, developers can hide the fine-tuned weights that contribute to the NPCs' competitive edge, preventing other developers from copying these features while still providing an immersive gaming experience.

### Further readings:

* Research paper on [opp/ai](https://arxiv.org/abs/2402.15006).
