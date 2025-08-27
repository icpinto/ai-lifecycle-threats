---
title: Model Export
parent: Production (Serving & Operations)
nav_order: 2
---

# Model Export

Serialize models for storage/deployment/sharing (Pickle, Joblib, ONNX, TorchScript, TensorFlow SavedModel, PMML, proprietary). Securing this step is critical.

## Attack surfaces

### Risks of Serialization Libraries
- **Arbitrary Code Execution:** Deserializing untrusted `.pkl`/Joblib can execute code.
- **Tampering & Hidden Logic:** Altered weights behave normally except under triggers (backdoors).
- **Lack of Integrity Checks:** Formats like Pickle lack built‑in cryptographic verification.

### Model Format‑Specific Exploits
- **ONNX/SavedModel Graph Manipulation:** Malicious ops injected; bypass safety constraints.
- **TorchScript/TFLite Attacks:** Hidden operators/payloads executed on load (e.g., edge/mobile).

### Supply Chain Poisoning via Model Repositories
- **Malicious Pre‑Trained Models:** Poisoned uploads on public hubs are downloaded and deployed.
- **Model Substitution in Registry:** Genuine artifact swapped for a trojan before deploy.

### Metadata & Config Tampering
- **Label Maps/Preprocessing Mismatch:** Systematic misclassification (e.g., “cat” ↔ “dog”).
- **LLM‑Specific:** Altered prompts/instructions bias responses post‑deployment.

### File Format & Deserialization Vulnerabilities
- **Zip Bombs/Oversized Exports:** Crash loaders or exhaust resources.
- **Framework Loader Bugs:** DoS or RCE via TF/PyTorch loading functions.

### Insider & Unauthorized Access Risks
- **Unsecured Object Stores:** Theft/replacement of artifacts.
- **No Signing/ACLs:** Silent swaps with trojanized versions.