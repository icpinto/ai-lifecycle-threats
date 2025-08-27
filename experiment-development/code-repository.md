---
title: Code Repository
parent: Experiment / Development Stage
nav_order: 5
---

# Code Repository

All code related to model training, data processing, and deployment (infrastructure-as-code, configuration files, etc.) is typically stored in a source code repository (like Git). This is the single source of truth for how models are built and how the pipeline runs. It often includes not just model code, but also scripts for data preprocessing, experiment configuration, and sometimes even small datasets or model weight files checked in for tests.

## Attack surfaces

- **Malicious Commits / Pull Requests:** Attackers or insiders introduce subtle backdoors.  
> **Ex:** A seemingly harmless PR modifies preprocessing to skip normalization when a secret trigger value is present, creating a backdoor.

- **Credential Theft:** Secrets are accidentally committed in code or configs.  
> **Ex:** A dataset URL with embedded credentials is pushed to Git, allowing external attackers to exfiltrate sensitive data.

- **Git History Poisoning:** Malicious scripts are hidden in old branches or commits.  
> **Ex:** During a hotfix merge, dormant malicious code from a historical branch re-enters the main pipeline.

- **Repo Supply Chain Attacks:** Dependencies declared in requirements files are poisoned.  
> **Ex:** Attackers compromise a library version specified in `requirements.txt`, which silently downloads malware during builds.

- **Information Leakage in Comments/Configs:** Developers expose sensitive details unintentionally.  
> **Ex:** Comments in config files reveal the location of the production model registry, guiding attackers in targeting it.

- **Model Stealing via Repository Exposure:** If model weights or test datasets are stored in repos, adversaries can clone them.  
> **Ex:** A mistakenly committed `.pth` weight file is downloaded by attackers, enabling them to replicate a proprietary vision model.
