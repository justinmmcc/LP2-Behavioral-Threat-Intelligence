# Project Lost Piglet 2 (LP2)
### *Investigating Human Threat Actors via Cognitive Friction & Machine Learning*

**Author:** Justin McCormick  
**Affiliation:** Penn State Berks — B.S. Cybersecurity Analytics & Operations  
**Role:** Solo Researcher  
**Sensor Deployment:** Cowrie SSH Honeypot · GCP `us-east4` · Feb 11 – Mar 5, 2026

---

## 🔬 Pipeline Orientation
This repository documents the end-to-end ML pipeline for **Project Lost Piglet 2 (LP2)** — an independent cyber-intelligence study testing whether telemetry from a high-interaction SSH honeypot can be machine-scored at scale to separate human threat actors from commodity botnet automation. 

**The Hypothesis:** Deliberately engineered **Cognitive Friction** (password-protected archives, psychologically loaded filenames, non-standard logic puzzles) forces measurable decision latency that becomes the anchoring feature for behavioral classification.

The pipeline ingests raw Cowrie JSONL from a 23-day deployment (**174,963 events**), enriches it with geographic and SSH-client metadata, runs a three-model ensemble (**Isolation Forest + HDBSCAN + Decision Tree**) under EVT/KS dynamic thresholding, and terminates in an audience-specific **Threat Intelligence Report**.

---

## 🗺️ Phase Map
| Phase | Module | Purpose |
| :--- | :--- | :--- |
| **I** | **Data Ingestion** | Merge LP archives into a unified session DataFrame |
| **II** | **Enrichment** | Geolocation, ASN resolution, and metadata normalization |
| **III** | **The ML Ensemble** | Anomaly scoring (Isolation Forest) & Taxonomy Clustering (HDBSCAN) |
| **IV** | **Behavioral Assessment** | MITRE tactic mapping and malware campaign analysis |
| **V** | **Keystroke Analysis** | Execution velocity profiling (Human vs. Bot timing signatures) |
| **VI** | **HASSH Fingerprinting** | SSH client identification and cross-campaign attribution |
| **VII** | **TTP Mapping** | Two-stage semantic classifier (TF-IDF + Keyword hierarchy) |
| **VIII** | **Session Forensics** | Dwell-time forensics on high-value interactive sessions |
| **IX** | **Cross-Session Attribution** | Infrastructure continuity analysis (LP1 → LP2) |
| **X** | **Intel Report** | Final SOC Manager Brief + Strategic Intelligence Product |

---

## 🎯 Headline Findings
* **99.96% Noise Reduction:** 174,963 raw events distilled into **6 high-value human-interactive sessions**.
* **RedTail Campaign Captured:** Identified 6 unique payloads across 49 delivery cycles originating from UK-based infrastructure.
* **Infrastructure Continuity:** Proved 33-day persistent botnet infrastructure identified across two independent deployments (LP1 → LP2).
* **Geographic Profile:** Primary threat origins identified as China (56%), India (15.8%), and Malaysia (6.6%).

---

## 📂 Project Navigation
```text
Project-LP2/
├── .gitignore
├── LICENSE
├── ProjectLostPiglet2_MLPipeline_TIR.html
├── ProjectLostPiglet2_OperationsReport.docx.pdf
├── ProjectLostPiglet2_Poster.pdf
├── README.md
├── index.html
└── requirements.txt
```

---

## 🛠️ Installation & Usage
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/Justin-McCormick/Project-LP2.git](https://github.com/Justin-McCormick/Project-LP2.git)
   cd Project-LP2
   ```
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Execute the pipeline:**
   Open `ProjectLostPiglet2_MLPipeline_TIR.html` or `index.html` in a browser to review the 10-phase analysis and final Threat Intelligence Report.

---

## 🛠️ Tech Stack & Methodology
* **Infrastructure:** Google Cloud Platform (GCP), Cowrie High-Interaction Honeypot
* **Ensemble Modeling:** Isolation Forest (Anomalies) + HDBSCAN (Clustering) + Decision Tree (Explainability)
* **Statistical Rigor:** Extreme Value Theory (EVT) & Kolmogorov-Smirnov (KS) for dynamic thresholding
* **Intelligence Standards:** MITRE ATT&CK Framework, HASSH Client Fingerprinting, TF-IDF NLP
