---
title: Versioned Data
parent: Experiment / Development Stage
nav_order: 1
---

# Versioned Data

Version‑control datasets for training and evaluation (e.g., DVC, Delta Lake, data catalogs) to ensure reproducibility and lineage from raw data to training sets.

## Attack surfaces

- **Dataset Poisoning Across Versions:** Malicious records added incrementally across releases.  
  *Example:* A few mislabeled “toxic” posts per release erode moderation.
- **Registry Compromise:** Datasets overwritten/replaced in object stores/registries.  
  *Example:* Breached registry swaps in tainted medical training set.
- **Weak Integrity Checks & Hash Collisions:** Lacking cryptographic signing enables silent tampering.  
  *Example:* Modified CSV passes weak checksum.
- **Access Control Gaps:** RBAC/ACL misconfig allows unauthorized read/write.  
  *Example:* Broad write permissions let contractors upload poisoned data.
- **Data Lineage Forgery:** Metadata/commit IDs/version tags manipulated.  
  *Example:* Poisoned data tagged “gold‑standard v3.”
- **Data Exfiltration & IP Theft:** Insiders/attackers clone proprietary datasets.  
  *Example:* Competitor exfiltrates speech datasets to train a substitute.