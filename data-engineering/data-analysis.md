---
title: Data Analysis
parent: Data Engineering
nav_order: 3
---

# Data Analysis

EDA, feature extraction, transformation (e.g., scaling, frequency domain, transcription), labeling (manual/semi‑auto/model‑assisted), augmentation, and synthesis (statistical or generative) to expand usable signal. **Privacy audits should be repeated on derived features.**

## Attack surface

- **Backdoor Triggers in Features:** Rare patterns/watermarks during augmentation become triggers.  
  *Example:* Specific pixel pattern causes consistent misclassification.
- **Labeling Compromise:** Systemic errors via malicious annotators or model‑assist workflows.  
  *Example:* Stop signs mislabeled as yield signs → critical traffic errors.
- **Synthetic Data Leakage:** Poor synthesis recreates sensitive originals.  
  *Example:* “Synthetic” patient records include near‑identical rare cases.
- **Statistical Manipulation of Feature Selection:** Skew measures to force weak/spurious features to dominate.  
  *Example:* Noise flooding elevates trivial attacker‑controlled features.
- **Shared Notebook/SaaS Exfiltration:** Embeddings/feature sets siphoned from shared/cloud tools.  
  *Example:* Analytics platform silently exfiltrates word embeddings.