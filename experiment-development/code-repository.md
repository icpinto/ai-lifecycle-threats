---
title: Code Repository
parent: Experiment / Development Stage
nav_order: 5
---

# Code Repository

Source of truth for training, data processing, deployment (IaC), configs, and sometimes small datasets/weights used for tests.

## Attack surfaces

- **Malicious Commits / Pull Requests:** Subtle backdoors added to code.  
  *Example:* Preprocessing skips normalization on a secret trigger value.
- **Credential Theft:** Secrets committed in code/configs.  
  *Example:* Dataset URL with embedded credentials pushed to Git.
- **Git History Poisoning:** Malicious scripts hide in old branches.  
  *Example:* Dormant code re‑enters during a hotfix merge.
- **Repo Supply Chain Attacks:** Compromised dependencies in requirements.  
  *Example:* Tainted library downloads malware during build.
- **Information Leakage in Comments/Configs:** Sensitive details exposed unintentionally.  
  *Example:* Config comments reveal production registry location.
- **Model Stealing via Repository Exposure:** Weights/test datasets cloned.  
  *Example:* Committed `.pth` weights replicate a proprietary model.