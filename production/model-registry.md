---
title: Model Registry
parent: Production (Serving & Operations)
nav_order: 3
---

# Model Registry

Central repository to store/version models, promote across stages (staging → production), and support rollbacks.

## Attack surfaces

- Registry poisoning (replace/retag so “Production” points to a backdoored model).
- Improper access control (over‑permissive push/promote/delete).
- Legacy artifacts not retired (shadow models resurrected via rollback).
- Unsigned downloads (MITM or mirror swap).