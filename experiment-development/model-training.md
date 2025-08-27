---
title: Model Training
parent: Experiment / Development Stage
nav_order: 2
---

# Model Training

Core training on GPUs/TPUs/CPUs (TensorFlow/PyTorch). Output is a learned model artifact (weights/parameters) capturing patterns in data.

## Attack surfaces

- **Data Poisoning Exploitation:** Corrupted inputs embed backdoors in weights.  
  *Example:* Sticker triggers on stop signs cause “speed‑limit” predictions.
- **Gradient Manipulation & Training Process Tampering:** Loss/optimizer altered to subvert convergence.  
  *Example:* Compromised optimizer suppresses minority‑class learning.
- **Malicious Frameworks & Libraries:** Trojanized packages execute code or exfiltrate data.  
  *Example:* Poisoned PyPI dependency siphons gradients.
- **Resource Hijacking:** Training jobs abused for crypto‑mining; partial checkpoint exfiltration.  
  *Example:* Compromised Kubernetes pod mines cryptocurrency.
- **Adversarial Initialization (Trojaned Pre‑trained Models):** Hidden triggers persist after fine‑tuning.  
  *Example:* Tampered embeddings leak system prompts on triggers.
- **Model Exfiltration via Gradients:** Distributed/federated setups leak sensitive data.  
  *Example:* Malicious participant reconstructs private user data.
- **Insider Manipulation:** Subtle backdoor lines inserted into training loops.  
  *Example:* Forces “approved” for a specific account ID.