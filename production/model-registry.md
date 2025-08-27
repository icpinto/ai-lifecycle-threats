---
title: Model Registry
parent: Production (Serving & Operations)
nav_order: 3
---

# Model Registry

A model registry is a specialized repository where trained model artifacts are stored and versioned. It often provides functionalities like promoting models to different stages (e.g., from “staging” to “production”), keeping track of model versions, and storing associated metadata like release notes. Teams use registries to have a single source of truth for which models are available for deployment and to facilitate rollbacks if needed.

## Attack surfaces

- Registry poisoning (replace/retag so “Production” points to a backdoored model).
- Improper access control (over‑permissive push/promote/delete).
- Legacy artifacts not retired (shadow models resurrected via rollback).
- Unsigned downloads (MITM or mirror swap).
