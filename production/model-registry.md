---
title: Model Registry
parent: Production (Serving & Operations)
nav_order: 3
---

# Model Registry

A model registry is a specialized repository where trained model artifacts are stored and versioned. It often provides functionalities like promoting models to different stages (e.g., from “staging” to “production”), keeping track of model versions, and storing associated metadata like release notes. Teams use registries to have a single source of truth for which models are available for deployment and to facilitate rollbacks if needed.

## Attack surfaces

- **Registry poisoning:** An attacker replaces or retags a malicious model as the “production” version.  
> **Ex:** An insider retags a backdoored model as the latest “production-ready” version, leading to a trojaned model being served to customers.

- **Improper access control:** Weak permissions allow unauthorized pushes, promotions, or deletions.  
> **Ex:** A low-privilege developer account is compromised and uploads an unreviewed model directly to production.

- **Legacy artifacts not retired:** Old models remain in the registry and can be rolled back to.  
> **Ex:** An outdated fraud-detection model is rolled back automatically after a crash, but attackers already know how to bypass it, enabling fraud at scale.

- **Unsigned or unverifiable downloads:** Models pulled from the registry are not cryptographically verified.  
> **Ex:** A MITM attacker intercepts traffic and swaps the model file with a trojaned version during deployment.
