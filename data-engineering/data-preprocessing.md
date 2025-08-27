---
title: Data Pre‑processing
parent: Data Engineering
nav_order: 2
---

# Data Pre‑processing

Cleaning/normalization, deduplication, imputation, encoding, and data sanitisation of personal data (generalization, suppression, perturbation of identifiers/quasi‑identifiers) to reduce re‑identification risk before downstream use.

## Attack surface

- **Label‑Flipping Attacks:** Hidden targeted re‑labeling in cleaning scripts or PRs alters meaning of training examples.  
  *Example:* “Benign tumor” flipped to “malignant” skews diagnoses.
- **Adversarial Noise Injection:** Perturbations disguised as normalization/denoising later trigger misclassifications.  
  *Example:* Tiny perturbations in speech data cause consistent phrase mis‑ID.
- **Pipeline Code Exploitation:** Insecure ETL/notebooks/deserialization leads to RCE or data exfiltration.  
  *Example:* Unsafe `pickle.load` leaks sensitive training data.
- **Privacy Regression During Sanitisation:** Poor anonymization leaves quasi‑identifiers for re‑ID.  
  *Example:* Names removed, but unique admission dates + rare treatments re‑identify patients.
- **Feature‑Scale Tampering:** Manipulated outliers distort scaling stats to hide fraud.  
  *Example:* Outliers make fraudulent transactions appear “normal.”