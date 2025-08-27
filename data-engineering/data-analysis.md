---
title: Data Analysis
parent: Data Engineering
nav_order: 3
---

# Data Analysis

EDA, feature extraction, transformation (e.g., scaling, frequency domain, transcription), labeling (manual/semi-auto/model-assisted), augmentation, and synthesis (statistical or generative) to expand usable signal. EDPB warns that new combinations/features can re-expose privacy risks even after sanitisation; privacy audits should be repeated on derived features.

## Attack surfaces

- **Backdoor Triggers in Features:** Attackers embed rare feature patterns or watermark-like signals during augmentation that later act as triggers.  
> **Ex:** Adversaries insert a specific pixel pattern in training images. The model behaves normally on clean data but always misclassifies images containing the pattern — a classic backdoor attack.

- **Labeling Compromise:** When human annotators or model-assisted labeling is used, attackers introduce systemic errors.  
> **Ex:** On a crowdsourcing platform, malicious annotators mislabel stop signs as yield signs. Models trained on this data make critical traffic errors.

- **Synthetic Data Leakage:** Improperly generated synthetic data recreates sensitive original records, undermining privacy.  
> **Ex:** A generative model trained on patient data outputs synthetic records that include near-identical rare cases, exposing private medical histories.

- **Statistical Manipulation of Feature Selection:** Attackers skew statistical measures to force the selection of weak or spurious features.  
> **Ex:** In a fraud detection system, adversaries flood the dataset with noise so that trivial, attacker-controlled features dominate model importance, making the system blind to real fraud indicators.

- **Shared Notebook / SaaS Exfiltration:** When feature engineering occurs in shared or cloud-hosted environments, attackers can intercept intermediate embeddings or feature sets.  
> **Ex:** A compromised SaaS analytics platform silently exfiltrates word embeddings, allowing adversaries to reverse-engineer models or mount membership inference attacks.
