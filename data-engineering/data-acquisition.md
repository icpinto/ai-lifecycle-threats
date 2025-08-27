---
title: Data Acquisition
parent: Data Engineering
nav_order: 1
---

# Data Acquisition

In this initial phase, organizations gather raw data from various sources. This may include first‑party data (from internal systems or users of your product), third‑party data feeds or partnerships, public datasets, web‑scraped content, and user‑generated telemetry. The choices made here determine the foundation of the AI model. It’s important to note that just because data is publicly accessible does not mean it is safe or free to use without scrutiny.

## Attack surface

- **Data Poisoning at Source:** Attackers inject malicious samples or mislabeled data into the original source (e.g., crowdsourced datasets, open corpora, third‑party contributions).  
  *Example:* In a spam detection dataset, an adversary contributes mislabeled spam emails as “ham,” causing the model to miss real spam.
- **Tampering During Ingestion:** Without secure transport and validation, attackers manipulate data flows during ETL/API pulls (MITM, modified files in transit).  
  *Example:* Intercepted transaction logs via an unsecured API insert backdoors that mislead a fraud model.
- **Supply‑Chain Dataset Compromise:** Poisoned public datasets or mirrors infiltrate downstream models.  
  *Example:* A “popular” image set with backdoor stickers causes consistent mislabels.
- **Tainted Web‑Scraping Streams:** Attackers seed harmful content for scrapers, introducing bias/misinformation/instructions.  
  *Example:* Misleading medical advice planted on a forum is scraped and later suggested by a healthcare assistant.
- **Unauthorized Access & Data Exfiltration:** Raw lakes in cloud buckets/shared storage are targets; weak auth/over‑broad permissions lead to theft/tampering.  
  *Example:* Exposed S3 with facial images is stolen and partially replaced with manipulated ones, raising future membership‑inference/backdoor risks.