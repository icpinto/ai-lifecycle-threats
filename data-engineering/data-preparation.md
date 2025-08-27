---
title: Data Preparation
parent: Data Engineering
nav_order: 4
---

# Data Preparation

Final packaging of engineered data into training, validation, and test sets; stratified/time‑aware splitting to preserve representativeness; the last stop before training.

## Attack surface

- **Validation/Test‑Set Poisoning:** Crafted examples distort metrics or guide hyperparameter selection.  
  *Example:* Backdoored model looks “more accurate” than clean.
- **Train–Test Leakage/Contamination:** Mixing sets inflates metrics and hides overfitting.  
  *Example:* Duplicates from training appear in test, boosting scores.
- **Class‑Balance Skewing:** Manipulated splits bias decision boundaries.  
  *Example:* Under‑represent “risky” applicants → over‑approve fraud.
- **Packaging & Registry Attacks:** Tampered TFRecords/Parquet in object stores/CI.  
  *Example:* One shard swapped with poisoned data just before training.
- **Embedded Exfiltration Risks:** Identifiable traces in prepared sets enable future privacy attacks.  
  *Example:* Retained identifiers later enable membership inference.