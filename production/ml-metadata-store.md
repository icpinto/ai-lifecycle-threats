---
title: ML Metadata Store
parent: Production (Serving & Operations)
nav_order: 1
---

# ML Metadata Store

The metadata store is a system that tracks the lineage and provenance of models and data in production. It typically logs details like which dataset version and training code commit produced a given model, what hyperparameters were used, evaluation metrics, and environment details. Essentially, it’s an audit trail and catalog for models and experiments, crucial for compliance, governance, and debugging.

## Attack surfaces

- Lineage/metrics tampering (inflate metrics to promote weak/trojaned models).
- Provenance spoofing (fake dataset or code commit IDs linked to a malicious artifact).
- Unauthorized reads (leak of sensitive eval traces, embeddings, or prompts).
- Metadata injection (poisoned notes/config copied by downstream jobs).
