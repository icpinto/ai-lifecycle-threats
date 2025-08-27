---
title: AI System (Serving/Inference)
parent: Production (Serving & Operations)
nav_order: 4
---

# AI System (Serving/Inference)

The live AI system that receives input (from users or upstream systems) and produces outputs (predictions, decisions, content). It could be an online API endpoint for a machine learning model, a real-time streaming inference service, an edge device running a model, or an interactive AI assistant (like an LLM-based chatbot). The serving system includes the model loaded in memory, the runtime (e.g., a Flask app, FastAPI, gRPC server, or specialized inference server), and often integration with other services (like databases or tool APIs if it’s an agent).

## Attack surfaces

- **Model Theft and Extraction Attacks:** These aim to duplicate a proprietary model by exploiting its public interface.  
  - *API-Based Extraction:* Attackers can train a substitute model by repeatedly querying a target model and recording outputs. Even without parameter knowledge, the substitute can achieve near-perfect fidelity.  
  - *Knowledge Distillation Attacks:* A more efficient variant, where attackers collect soft-label outputs (e.g., probabilities) to train a high-fidelity student model. By leveraging explanations or confidence scores, the substitute model can be trained with significantly fewer queries.

- **Inference-Time Privacy Attacks:** Models may inadvertently memorize and leak training data.  
  - *Model Inversion Attacks:* Attackers reconstruct sensitive training data from outputs. For example, facial recognition models have been shown to regenerate blurred or hidden facial features from probability vectors.  
  - *Membership Inference Attacks:* Attackers determine whether a specific data record was included in training. This has severe privacy implications in domains like healthcare (revealing a patient’s presence in a dataset).

- **Adversarial Evasion Attacks:** Adversaries craft inputs to cause intentional misclassifications.  
> **Ex:** Adding imperceptible pixel noise (FGSM or PGD perturbations) to an image of a “stop” sign can cause an autonomous vehicle’s model to classify it as a “speed-limit” sign.  
> **Ex:** LLM jailbreaks where prompts like “ignore previous instructions” cause the model to produce restricted outputs.

- **Denial of Service (DoS) and Resource Exhaustion:** Attackers exploit the computational cost of inference.  
> **Ex:** An adversary submits oversized prompts or adversarial token storms to an LLM API, consuming GPUs and spiking costs, effectively denying access to legitimate users.

- **RAG & Vector Store Poisoning:** In Retrieval-Augmented Generation (RAG) setups, attackers tamper with the external knowledge base or embeddings.  
> **Ex:** Poisoning a corporate vector database so that every query about “compliance” retrieves manipulated documents suggesting unsafe practices.

- **Output Injection Attacks:** Maliciously crafted outputs exploit downstream systems.  
> **Ex:** An LLM integrated into a workflow produces SQL statements that, if executed unvalidated, perform destructive queries — a form of AI-enabled SQL injection.

- **Side-Channel Exploits in Shared Environments:** On multi-tenant GPUs or TPUs, attackers may extract information about co-located models.  
> **Ex:** By measuring memory timing on shared hardware, adversaries can infer details of another tenant’s neural network architecture.
