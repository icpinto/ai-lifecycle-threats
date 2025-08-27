---
title: Data Pre‑processing
parent: Data Engineering
nav_order: 2
---

# Data Pre‑processing

Cleaning/normalization, deduplication, imputation, encoding, and data sanitisation of personal data (generalization, suppression, perturbation of identifiers/quasi‑identifiers) to reduce re‑identification risk before downstream use.

## Attack surfaces

- **Label‑Flipping Attacks:**  Adversaries hide targeted re-labeling within cleaning scripts or pull requests, altering the meaning of training examples. 
 > *Ex:* In a medical dataset, attackers flip “benign tumor” labels to “malignant.” A cancer-detection model trained on this poisoned dataset produces dangerously skewed diagnoses.

- **Adversarial Noise Injection:** Malicious actors conceal adversarial perturbations under the guise of normalization or denoising. These perturbations later trigger model misclassifications. 
 > *Ex:* A poisoned speech dataset includes tiny perturbations masked as background noise. The resulting voice-recognition model consistently misidentifies attacker-chosen phrases.

- **Pipeline Code Exploitation:** Insecure ETL scripts, notebooks, or deserialization routines can be hijacked to execute arbitrary code or exfiltrate data.
 > *Ex:*A malicious update to a Python preprocessing script uses unsafe pickle.load calls, leading to remote code execution and leakage of sensitive training data.
- **Privacy Regression During Sanitisation:** Poorly designed anonymization fails to suppress quasi-identifiers, allowing re-identification.  
 > *Ex:* A healthcare dataset anonymizes names but leaves unique patient admission dates and rare combinations of treatments, enabling re-identification of individuals.

- **Feature‑Scale Tampering:** Attackers manipulate summary statistics used for scaling or normalization, biasing downstream model behavior.  
 > *Ex:* By injecting outliers into financial data, attackers distort normalization so that fraudulent transactions appear statistically “normal” to the fraud detection model.
