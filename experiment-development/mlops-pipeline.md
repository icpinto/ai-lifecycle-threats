---
title: MLOps Pipeline
parent: Experiment / Development Stage
nav_order: 4
---

# MLOps Pipeline

These pipelines orchestrate tasks like retraining models, running validation suites, packaging the model into a deployable format (for example, a Docker image or serialized model file), and deploying it to production environments. Tools and platforms such as Kubeflow, MLflow, Jenkins, GitHub Actions, or custom Airflow pipelines are commonly used to implement this automation.

## Attack surfaces

- **Pipeline Poisoning:** Malicious code injected into CI/CD stages manipulates builds or exfiltrates secrets.  
> **Ex:** A rogue Jenkins plugin injects spyware into every model artifact produced.

- **Model Artifact Swapping:** Trojanized models are substituted during packaging.  
> **Ex:** The clean fraud-detection model is swapped with an attacker-crafted model that approves fraudulent transactions.

- **Insecure Container Images:** Vulnerable base images in training/deployment environments allow RCE.  
> **Ex:** An outdated Docker image includes an unpatched OpenSSL library, exploited during pipeline execution.

- **Secret Leakage:** Sensitive tokens or keys appear in logs or configs.  
> **Ex:** An API key for the model registry is exposed in CI logs and reused by attackers to pull proprietary models.

- **Dependency Confusion & Supply Chain Exploits:** Attackers publish malicious packages mimicking internal dependencies.  
> **Ex:** The pipeline fetches `ml-utils` from PyPI instead of the private repo, executing malicious code.

- **Infrastructure Misconfiguration:** Poorly secured orchestrators expose APIs or dashboards.  
> **Ex:** A misconfigured Kubeflow instance lets attackers inject rogue pipeline steps remotely.
