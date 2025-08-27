---
title: Monitoring (Telemetry & Audit)
parent: Production (Serving & Operations)
nav_order: 5
---

# Monitoring (Telemetry & Audit)

Collect application logs, prediction logs, latency/error metrics, drift detection signals, safety checks, and audit logs.

## Attack surfaces

- **Sensitive Data Leakage in Logs:** PII/system prompts/API keys captured.  
  *Example:* Chatbot logs full conversations including passwords.
- **Log Tampering & Gaps:** Disable/manipulate logging to erase traces.  
  *Example:* Malware suppresses logs for adversarial queries.
- **Silent Model Degradation (Drift Exploitation):** Gradual input shifts undermine detection.  
  *Example:* Fraudsters slowly alter patterns until undetected.
- **Alert Fatigue Manipulation:** Flood low‑severity alerts to hide real attacks.  
  *Example:* Malformed input spam overwhelms operators.
- **Log Injection Attacks:** Payloads stored in logs exploit dashboards/SIEMs.  
  *Example:* `<script>alert('XSS')</script>` executes in log UI.
- **Telemetry Poisoning:** Skew monitoring to trigger bad rollbacks/scaling.  
  *Example:* Manipulated logs cause rollback to vulnerable model.