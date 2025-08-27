---
title: Output Data
parent: Production (Serving & Operations)
nav_order: 7
---

# Output Data

Predictions, classifications, explanations, and generated content; often stored for analytics, re‑ingested for retraining, or consumed by downstream apps.

## Attack surfaces

- **Sensitive Information Leakage:** Memorized training data/system prompts regurgitated.  
  *Example:* LLM reveals fragments of private medical records.
- **Toxic or Non‑Compliant Content:** Jailbreaks elicit harmful or policy‑violating outputs.  
  *Example:* Extremist propaganda or disallowed financial advice.
- **Stored‑Output Poisoning:** Malicious generations saved and later used for fine‑tuning.  
  *Example:* Biased responses amplify bias in RL updates.
- **Output Injection:** Malicious instructions executed by downstream systems.  
  *Example:* Generated HTML with `<script>` triggers XSS.
- **Data Exfiltration via Outputs:** Sensitive info encoded in subtle response patterns.  
  *Example:* Capitalization pattern hides API keys.
- **Watermark/Attribution Removal Attacks:** Edits strip provenance.  
  *Example:* AI‑generated text paraphrased to remove watermarks.
- **Malicious Fine‑Tuning via Outputs:** Captured outputs carry attacker bias into future models.