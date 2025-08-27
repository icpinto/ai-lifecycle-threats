---
title: Output Data
parent: Production (Serving & Operations)
nav_order: 7
---

# Output Data

The outputs of AI systems include predictions, classifications, explanations, and generated content. These may be stored for analytics, re-ingested for retraining, or consumed by downstream applications. Improperly managed, outputs can leak sensitive information, amplify bias, or become vectors for injection attacks.

## Attack surfaces

- **Sensitive Information Leakage:** Models may regurgitate memorized training data or system prompts.  
> **Ex:** An LLM outputs fragments of its training set, accidentally revealing private medical records.

- **Toxic or Non-Compliant Content:** Adversaries manipulate inputs to elicit harmful or policy-violating outputs.  
> **Ex:** A chatbot jailbreak produces extremist propaganda or disallowed financial advice.

- **Stored-Output Poisoning:** Malicious outputs saved in logs or analytics later poison retraining.  
> **Ex:** Attackers repeatedly trigger biased responses, which are logged and later re-used in model fine-tuning, amplifying the bias.

- **Output Injection:** Outputs contain malicious instructions that exploit downstream systems.  
> **Ex:** An LLM produces HTML with embedded `<script>` tags. When displayed on a web dashboard, it executes an XSS attack.

- **Data Exfiltration via Outputs:** Attackers encode sensitive information in model outputs to smuggle data out.  
> **Ex:** A compromised model embeds API keys inside subtle variations of generated responses (e.g., capital letter patterns).

- **Watermark/Attribution Removal Attacks:** Attackers alter generated outputs to bypass provenance tracking.  
> **Ex:** AI-generated text is paraphrased by another model to strip watermarks, then redistributed without attribution.

- **Malicious Fine-Tuning via Outputs:** Outputs captured and fed into future fine-tuning cycles carry attacker bias.  
> **Ex:** Attackers trick an AI assistant into repeatedly outputting toxic completions. These completions are logged, used in reinforcement learning updates, and reinforce the toxicity.
