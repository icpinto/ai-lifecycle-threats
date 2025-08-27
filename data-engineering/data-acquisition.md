---
title: Data Acquisition
parent: Data Engineering
nav_order: 1
---

# Data Acquisition

In this initial phase, organizations gather raw data from various sources. This may include first‑party data (from internal systems or users of your product), third‑party data feeds or partnerships, public datasets, web‑scraped content, and user‑generated telemetry. The choices made here determine the foundation of the AI model. It’s important to note that just because data is publicly accessible does not mean it is safe or free to use without scrutiny.

## Attack surface

- **Data Poisoning at Source:** Attackers inject malicious samples or mislabeled data into the original source. This is especially dangerous in crowdsourced datasets, open corpora, or third-party contributions. 
> **Ex:** In a spam detection dataset, an adversary contributes mislabeled spam emails marked as “ham” (non-spam). The resulting model, trained on this corrupted data, fails to detect real spam messages, giving the attacker an advantage.

- **Tampering During Ingestion:** Without secure transport and validation, attackers can manipulate data flows during ETL (Extract, Transform, Load) processes or API pulls. This includes man-in-the-middle (MITM) attacks or modifying files in transit 
> **Ex:**  A financial institution regularly pulls transaction logs via an unsecured API. An attacker intercepts the feed and alters transaction fields, inserting backdoors that later mislead a fraud detection model.

- **Supply‑Chain Dataset Compromise:** Public datasets or mirrored repositories may be poisoned deliberately as a form of data supply-chain attack. Because many ML teams reuse popular benchmarks, these poisoned datasets can infiltrate many downstream models.
> **Ex:** A malicious actor uploads a compromised version of a widely used image dataset. The poisoned subset includes backdoor triggers  small stickers on objects  causing image classifiers trained on this data to mislabel those objects consistently.

- **Tainted Web‑Scraping Streams:**  Adversaries can deliberately plant harmful content on web pages or forums, knowing it will be scraped into AI datasets. These “tainted” records can introduce bias, misinformation, or embedded instructions.
> **Ex:**An attacker publishes misleading medical advice on a high-traffic forum. An AI healthcare assistant trained on scraped data incorporates these poisoned entries, later suggesting harmful treatments to users.

- **Unauthorized Access & Data Exfiltration:**  Raw data lakes, often stored in cloud buckets or shared development storage, are attractive targets. Weak authentication or overly broad permissions can allow unauthorized downloads or manipulations.
> **Ex:**An exposed S3 bucket holding raw facial images for a biometric model is discovered by attackers. They not only steal sensitive personal data but also replace some images with manipulated ones, increasing the risk of future membership inference and backdoor triggers.
