---
title: Data Preparation
parent: Data Engineering
nav_order: 4
---

# Data Preparation

Final packaging of engineered data into training, validation, and test sets; stratified/time-aware splitting to preserve representativeness; this is the last stop before training.

## Attack surface

- **Validation/Test-Set Poisoning:** Attackers insert crafted examples into evaluation datasets to distort metrics or guide hyperparameter selection.  
> **Ex:** A malicious sample is inserted into the validation set, making a backdoored model appear more accurate than a clean alternative.

- **Train–Test Leakage or Contamination:** Mixing data between sets inflates performance metrics and masks overfitting.  
> **Ex:** Attackers duplicate specific training records into the test set. The model memorizes these records, artificially boosting accuracy scores and passing QA checks.

- **Class-Balance Skewing:** Adversaries manipulate dataset splits to bias decision boundaries.  
> **Ex:** In credit scoring data, attackers reduce representation of “risky” loan applicants in the training set. The resulting model over-approves fraudulent loans.

- **Packaging and Registry Attacks:** Final data shards (e.g., TFRecords, Parquet files) may be tampered with in object stores or CI/CD systems.  
> **Ex:** An attacker swaps out one shard in cloud storage with a poisoned version, embedding triggers just before model training.

- **Embedded Exfiltration Risks:** If identifiable traces remain in the prepared sets, they create future privacy risks.  
> **Ex:** A prepared dataset inadvertently retains unique patient identifiers. Later, adversaries run membership inference on the deployed model, confirming specific patients were part of training.
