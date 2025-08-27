---
title: AI System (Serving/Inference)
parent: Production (Serving & Operations)
nav_order: 4
---

# AI System (Serving/Inference)

Online APIs, streaming inference, edge devices, or interactive assistants/agents.

## Attack surfaces

- **Model Theft & Extraction Attacks:** Train substitutes via API output harvesting; knowledge distillation using soft labels/confidences.
- **Inference‑Time Privacy Attacks:** Model inversion; membership inference reveals training presence (e.g., in healthcare).
- **Adversarial Evasion Attacks:** Perturbations (FGSM/PGD) cause misclassification; LLM jailbreaks (“ignore previous instructions”).
- **DoS & Resource Exhaustion:** Oversized prompts/adversarial token storms spike GPU costs; denial of service.
- **RAG & Vector Store Poisoning:** Tampered external knowledge/embeddings skew retrieval and answers.
- **Output Injection Attacks:** Generated SQL/HTML commands executed by downstream systems (AI‑enabled injection).
- **Side‑Channel Exploits:** Multi‑tenant GPU/TPU timing leaks architecture or data of co‑located models.