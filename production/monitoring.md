---
title: Monitoring (Telemetry & Audit)
parent: Production (Serving & Operations)
nav_order: 5
---
# Monitoring (Telemetry & Audit)

Monitoring is the practice of collecting telemetry from the AI system and its surrounding pipeline in production. This includes application logs, model prediction logs, performance metrics (latency, error rates), drift detection signals (to see if input data distribution is shifting over time), and alerts from any safety or quality checks. Audit logs are also maintained to record who deployed what model when, and which inputs were received (especially important for regulated industries or debugging incidents).

## Attack surfaces

- **Sensitive Data Leakage in Logs:** Logs may inadvertently capture PII, system prompts, or API keys.  
> **Ex:** An LLM-based chatbot logs full conversation histories, including user-entered passwords, which are later exfiltrated through a log breach.

- **Log Tampering & Gaps:** Attackers disable or manipulate logging to erase traces of malicious activity.  
> **Ex:** Malware injected into the model server suppresses logs for adversarial queries, leaving investigators blind to ongoing extraction attempts.

- **Silent Model Degradation (Drift Exploitation):** Attackers exploit natural drift by introducing gradual input shifts.  
> **Ex:** Fraudsters slightly alter transaction patterns daily until the drifted model stops detecting their fraud.

- **Alert Fatigue Manipulation:** Flooding the system with spurious anomalies to mask real attacks.  
> **Ex:** Attackers spam malformed inputs to trigger low-severity drift alerts, overwhelming operators so that a real poisoning campaign goes unnoticed.

- **Log Injection Attacks:** Malicious payloads are inserted into log messages to exploit downstream log viewers or SIEM systems.  
> **Ex:** A model response containing ""<script>alert('XSS')</script>"" is stored in monitoring logs and later executed in a web-based log dashboard.

- **Telemetry Poisoning:** Attackers tamper with monitoring data to skew retraining or automated scaling.  
> **Ex:** Manipulated performance logs suggest that the current model is underperforming, triggering an automatic rollback to an older exploitable model.
