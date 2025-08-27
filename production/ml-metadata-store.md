---
title: ML Metadata Store
parent: Production (Serving & Operations)
nav_order: 1
---

# ML Metadata Store

Tracks lineage and provenance of models/data in production (dataset versions, code commits, hyperparameters, metrics, environment). Crucial for compliance, governance, and debugging.

## Attack surfaces

- Lineage/metrics tampering (inflate metrics to promote weak/trojaned models).
- Provenance spoofing (fake dataset or code commit IDs linked to a malicious artifact).
- Unauthorized reads (leak of sensitive eval traces, embeddings, or prompts).
- Metadata injection (poisoned notes/config copied by downstream jobs).