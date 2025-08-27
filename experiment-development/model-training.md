---
title: Model Training
parent: Experiment / Development Stage
nav_order: 2
---

# Model Training

This is the core stage where the model is actually trained. Using the prepared training dataset, the team runs training jobs on compute infrastructure (GPUs, TPUs, or CPU clusters), typically using machine learning frameworks like TensorFlow or PyTorch. The output of this process is a learned model artifact (the model weights/parameters) that captures the patterns in the training data. Model training may involve training from scratch or fine-tuning a pre-trained model.

## Attack surfaces

- **Data Poisoning Exploitation:** Previously injected malicious inputs corrupt learned weights.  
> **Ex:** Backdoor triggers (special pixel patterns in stop signs) are embedded in training data, causing the traffic model to misclassify them as speed-limit signs at inference.

- **Gradient Manipulation & Training Process Tampering:** Attackers alter the loss function or optimizer to subvert convergence.  
> **Ex:** A compromised optimizer silently prevents convergence on minority-class samples, introducing bias into a hiring algorithm.

- **Malicious Frameworks & Libraries:** Trojanized ML packages execute code or alter training.  
> **Ex:** A poisoned PyPI dependency siphons gradient data to an attacker’s server during training.

- **Resource Hijacking:** Training jobs are abused for unintended purposes like crypto-mining.  
> **Ex:** A compromised Kubernetes training pod mines cryptocurrency while also exfiltrating partial model checkpoints.

- **Adversarial Initialization (Trojaned Pre-trained Models):** Poisoned pre-trained embeddings retain hidden triggers after fine-tuning.  
> **Ex:** A tampered language embedding downloaded from a public model hub causes the final chatbot to leak system prompts when given certain trigger words.

- **Model Exfiltration via Gradients:** If training is distributed, gradient sharing can leak sensitive data.  
> **Ex:** In federated learning, a malicious participant reconstructs private user data from exchanged gradients.

- **Insider Manipulation:** An internal developer inserts subtle backdoor code into the training loop.  
> **Ex:** A single line ensures that the model always predicts “approved” for a specific account ID, benefiting the insider.
