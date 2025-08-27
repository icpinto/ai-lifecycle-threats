---
title: Threats Across the AI Lifecycle
layout: default
nav_order: 1
---

# Threats Across the AI Lifecycle

## Introduction

Machine Learning Operations (MLOps) pipelines extend traditional DevOps practices into the realm of machine learning, bringing new threat landscapes that differ from those in classic software development. While DevOps and MLOps share goals of rapid, reliable deployment, the risks faced in ML pipelines diverge from traditional software risks in important ways. MLOps workflows introduce data‑centric stages and model‑centric artifacts that are not present in standard software delivery. This means that in addition to application code and infrastructure, data and models become first‑class attack surfaces. Threats such as data poisoning, model theft, or adversarial manipulation of model inputs have no direct analogue in a pure DevOps setting. At the same time, all the familiar DevOps security issues (like vulnerable code dependencies, CI/CD pipeline compromises, or misconfiguration) still apply to MLOps but now they are compounded by ML‑specific vulnerabilities.

For example, consider the **Data Engineering** stage: in an MLOps pipeline, the training data that is collected and processed can itself be a target of attack. An adversary might inject malicious data into the dataset (known as **data poisoning**) to subtly corrupt the model’s learning process. Biases or backdoors introduced at this stage will carry through to the model. In a traditional DevOps pipeline, there is no equivalent process where external data directly determines a software artifact’s behavior; the focus is on code written by developers. Thus, the integrity of data is a much greater concern in MLOps. Similar contrasts appear at other stages of the lifecycle, from how models are tested to how they handle inputs in production.

---

## The Three Major Sections

- **Data Engineering** — Data Acquisition; Data Pre‑processing; Data Analysis; Data Preparation  
- **Experiment / Development Stage** — Versioned Data; Model Training; Model Validation; MLOps Pipeline; Code Repository  
- **Production (Serving & Operations)** — ML Metadata Store; Model Export; Model Registry; AI System (Serving/Inference); Monitoring (Telemetry & Audit); Input Data; Output Data

Use the sidebar to navigate.
