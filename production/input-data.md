---
title: Input Data
parent: Production (Serving & Operations)
nav_order: 6
---

# Input Data

Live user inputs, events, files, or upstream integrations consumed by the AI system. This production input data is often different from training data and can evolve over time (the phenomenon of data drift). It’s also typically uncurated and potentially adversarial, since anyone or any external system providing input might not be trusted.

## Attack surfaces

- **Streaming Data Poisoning:** Injected malicious inputs into live feeds bias future model updates.  
> **Ex:** Attackers flood a recommendation engine with fake user ratings to push attacker-owned products to the top.

- **Concept Drift Attacks:** Gradual changes in input distribution undermine model performance.  
> **Ex:** Intruders slowly modify network traffic patterns so an intrusion detection model adapts to accept malicious flows as benign.

- **Adversarial Payload Attacks:** Inputs are crafted to exploit model or preprocessing vulnerabilities.  
> **Ex:** An adversarial image patch confuses a vision model into ignoring a person on CCTV.  
> **Ex:** A crafted text prompt jailbreaks an LLM, forcing it to output sensitive system data.

- **Schema Smuggling:** Unexpected fields or structures in input trigger unsafe actions in agents.  
> **Ex:** JSON sent to an AI agent includes a hidden "command": "rm -rf /" field, which the agent mistakenly executes.

- **Multi-Stage Payload Chaining:** Attackers combine benign-looking inputs that only reveal malicious behavior when processed together.  
> **Ex:** Two separate inputs carry harmless fragments, but when concatenated by the model’s preprocessing step, they form a malicious SQL injection query.

- **Input Watermark Stripping:** Adversaries modify inputs to evade watermark-based detection.  
> **Ex:** Attackers slightly perturb AI-generated text to remove embedded watermarks, making it indistinguishable from human-authored input.
