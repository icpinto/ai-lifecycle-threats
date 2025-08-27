---
title: MLOps Pipeline
parent: Experiment / Development Stage
nav_order: 4
---

# MLOps Pipeline

Pipelines orchestrate retraining, validation suites, packaging, and deployment (Kubeflow, MLflow, Jenkins, GitHub Actions, Airflow).

## Attack surfaces

- **Pipeline Poisoning:** Malicious CI/CD stages manipulate builds or exfiltrate secrets.  
  *Example:* Rogue Jenkins plugin injects spyware into all artifacts.
- **Model Artifact Swapping:** Trojanized models substituted during packaging.  
  *Example:* Clean fraud detector swapped to auto‑approve fraud.
- **Insecure Container Images:** Vulnerable base images enable RCE.  
  *Example:* Unpatched OpenSSL exploited during pipeline execution.
- **Secret Leakage:** Keys/tokens exposed in logs/configs.  
  *Example:* Model registry API key in CI logs.
- **Dependency Confusion & Supply Chain Exploits:** Public package wins over internal name.  
  *Example:* Pipeline fetches `ml-utils` from PyPI, runs attacker code.
- **Infrastructure Misconfiguration:** Orchestrators expose APIs/dashboards.  
  *Example:* Misconfigured Kubeflow allows rogue steps injection.