---
title: Versioned Data
parent: Experiment / Development Stage
nav_order: 1
---

# Versioned Data

It’s a best practice to version‑control the datasets used for training and evaluation. Teams use data versioning systems or model registries (like DVC, Delta Lake, or cloud data catalogs) to keep track of dataset versions, ensure reproducibility, and maintain lineage from raw data through to training sets. This component acts as a bridge between the data engineering phase and model training.

- **Dataset Poisoning Across Versions:** Adversaries incrementally inject corrupted records across successive versions, making the attack harder to detect.  
> **Ex:** Each dataset release for a content moderation model includes a few mislabeled “toxic” posts as “safe.” Over multiple versions, the model increasingly fails to catch hate speech.

- **Registry Compromise:** Attackers overwrite or replace datasets in object stores or registries.  
> **Ex:** A cloud dataset registry is breached, and the latest training set for a medical AI is replaced with tainted records that subtly bias diagnoses.

- **Weak Integrity Checks & Hash Collisions:** If dataset snapshots lack cryptographic signing, silent tampering can persist.  
> **Ex:** An attacker modifies a CSV file, recalculates a non‑cryptographic checksum, and the pipeline ingests it as valid.

- **Access Control Gaps:** Improper RBAC/ACL configurations allow unauthorized read/write access.  
> **Ex:** A junior contractor with broad write permissions uploads a dataset variant from their local machine containing poisoned samples.

- **Data Lineage Forgery:** Attackers manipulate dataset metadata (provenance, commit IDs, or version tags) to misrepresent data origins.  
> **Ex:** Poisoned data is tagged as “gold‑standard v3” in the registry, making it indistinguishable from trusted sets.

- **Data Exfiltration & IP Theft:** Insiders or attackers with read access may clone sensitive proprietary datasets.  
> **Ex:** A competitor exfiltrates versioned speech datasets to train a substitute model, bypassing costly data collection.
