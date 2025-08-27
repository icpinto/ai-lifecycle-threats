---
title: Model Validation
parent: Experiment / Development Stage
nav_order: 3
---

# Model Validation

Evaluate models on validation/test sets, check overfitting, run adversarial robustness and fairness assessments.

## Attack surfaces

- **Validation‑Set Poisoning:** Corrupted samples skew evaluation and model selection.  
  *Example:* Backdoored model appears to outperform clean model.
- **Overfitting Leakage in Reports:** Debug logs spill sensitive training text/PII.  
  *Example:* Verbatim training data in validation logs.
- **Skipped Adversarial Testing:** Blind spots for simple FGSM/PGD that later sink production.  
  *Example:* Model collapses under FGSM perturbations.
- **Tampered Metrics Pipeline:** Altered scripts inflate reported accuracy.  
  *Example:* 10% of validation failures silently ignored.
- **Advanced Adversarial Stress Tests:** Gradient‑based/black‑box attacks reveal fragility.  
  *Example:* PGD shows 90% adversarial misclassification.
- **Fairness & Bias Exploits:** Untested bias enables exploitation.  
  *Example:* Poor accuracy on darker skin tones → impersonation attacks.