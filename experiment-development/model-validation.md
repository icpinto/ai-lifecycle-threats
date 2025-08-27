---
title: Model Validation
parent: Experiment / Development Stage
nav_order: 3
---

# Model Validation

After training a model, it must be evaluated to ensure it performs well and is robust. This stage involves testing the model on the validation set (and possibly a separate test set) to measure metrics like accuracy, precision/recall, as well as performing checks for overfitting. Increasingly, teams also perform robustness evaluations here – such as adversarial testing (checking how the model handles perturbed inputs) or fairness assessments.

## Attack surfaces

- **Validation-Set Poisoning:** Adversaries corrupt samples in validation/test sets, skewing evaluation.  
> **Ex:** A malicious sample causes a backdoored model to outperform a clean one during validation, leading to its promotion.

- **Overfitting Leakage in Reports:** Improper logging may expose sensitive training data.  
> **Ex:** Debug outputs include verbatim text from the training set, leaking PII into validation logs.

- **Skipped Adversarial Testing:** Absence of adversarial robustness checks leaves blind spots.  
> **Ex:** The model performs well on clean test data but collapses under simple FGSM perturbations, which attackers later exploit in production.

- **Tampered Metrics Pipeline:** Evaluation scripts are altered to inflate reported accuracy.  
> **Ex:** An insider modifies the metrics script so that 10% of validation failures are silently ignored.

- **Advanced Adversarial Stress Tests:** Models may be vulnerable to gradient-based or black-box adversarial attacks.  
> **Ex:** During testing, Projected Gradient Descent (PGD) attacks reveal that 90% of adversarial samples are misclassified — a clear red flag if ignored

- **Fairness & Bias Exploits:** Attackers can exploit untested bias in decision systems.  
> **Ex:** A facial recognition model that passes basic accuracy checks is later revealed to have poor accuracy on darker skin tones, enabling adversarial impersonation attacks.
