---
title: Input Data
parent: Production (Serving & Operations)
nav_order: 6
---

# Input Data

Live user inputs, events, files, or upstream integrations consumed by the AI system; distributions evolve (drift) and inputs can be adversarial.

## Attack surfaces

- **Streaming Data Poisoning:** Malicious inputs bias future model updates.  
  *Example:* Fake ratings push attacker‑owned products.
- **Concept Drift Attacks:** Gradual shifts undermine performance.  
  *Example:* Network traffic altered to look benign.
- **Adversarial Payload Attacks:** Crafted images/text exploit model or preprocessing.  
  *Example:* Adversarial patch hides a person on CCTV; crafted LLM prompt leaks system data.
- **Schema Smuggling:** Unexpected fields trigger unsafe agent actions.  
  *Example:* Hidden `command: "rm -rf /"` field executed by agent.
- **Multi‑Stage Payload Chaining:** Benign‑looking fragments combine into malicious inputs downstream.  
  *Example:* Separate inputs concatenate into SQL injection.
- **Input Watermark Stripping:** Perturb outputs to evade watermark‑based detection.  
  *Example:* Slight edits remove embedded watermarks.