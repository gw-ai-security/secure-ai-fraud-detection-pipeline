## Quickstart (Portfolio Demo)

This repository is a **portfolio project** that simulates a **regulated EU banking environment** for AI-based fraud detection.  
The focus is on **Security-by-Design**, **Privacy-by-Design**, and **audit-ready engineering practices**.

> ⚠️ **Important note:**  
> This project uses **synthetic data only**.  
> No real customer data or personally identifiable information (PII) is processed.

---

### What this project demonstrates

- End-to-end AI fraud detection pipeline (data → features → model → monitoring)
- Secure and privacy-aware ML engineering practices
- Regulatory alignment with **GDPR**, **PSD2**, and the **EU AI Act**
- Reproducible, reviewable artefacts suitable for audits and interviews

---

## Option A: Run in GitHub Codespaces (recommended)

This is the easiest way to explore the project without any local setup.

1. Click **Code** → **Codespaces** → **Create codespace on main**
2. Open the terminal inside Codespaces and run:

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

3. Open and run the notebooks in order:
   - `notebooks/01_data_cleaning.ipynb`
   - `notebooks/02_feature_engineering.ipynb`

---

## Option B: Run locally

### Prerequisites

- Python 3.10+ recommended  
- Git

### Setup

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
# source .venv/bin/activate

pip install --upgrade pip
pip install -r requirements.txt
```

### Run the pipeline

Open and execute the notebooks in this order:

1. `notebooks/01_data_cleaning.ipynb`
2. `notebooks/02_feature_engineering.ipynb`

---

## Expected outputs

After running the notebooks, the following artefacts are generated:

### Cleaned dataset
- `fraud_cleaned.csv`

### Feature datasets
- `features.csv`
- `features.parquet`

### Train/Test splits
- `X_train.parquet`
- `X_test.parquet`

### Feature metadata
- `feature_config.json`
- `feature_names.json`

These artefacts are intentionally versioned to support **traceability and auditability**.

---

## Notes for reviewers and employers

- All datasets are **synthetically generated** for educational and portfolio purposes.
- The project is structured to **rebuild model artefacts from source notebooks** rather than relying on pre-built binaries.
- Pickled artefacts (`.pkl`) may be environment-sensitive and are treated as **derived artefacts**, not the source of truth.
- Design decisions and trade-offs are documented throughout the repository (`docs/`, `security/`, `privacy/`).

---

## Repository structure (high level)

```
secure-ai-fraud-detection-pipeline/
├── data/           # Synthetic datasets only
├── notebooks/      # Step-by-step pipeline notebooks
├── privacy/        # Privacy-enhancing techniques (DP, k-anonymity, encryption)
├── security/       # Threat models, adversarial tests, incident response
├── monitoring/     # Drift detection, logging, alerting
├── docs/           # GDPR / PSD2 / EU AI Act mappings
├── executive/      # Executive summaries and ROI models
└── framework/      # Governance and audit templates
```

---

## Disclaimer

This repository is a **simulation and learning project**.  
It does **not** claim legal compliance or production readiness, but demonstrates **engineering practices that support regulatory requirements** in regulated financial environments.


# Secure-AI-Fraud-Detection-Pipeline
A full-stack AI/ML pipeline for detecting financial fraud in the European banking sector, built with a strong emphasis on Security-by-Design, Privacy-by-Design, and compliance with PSD2, GDPR (Art. 5, 25, 32), and the EU AI Act (Art. 6–15).

```bash
secure-ai-fraud-detection-pipeline/
├── data/
│   ├── raw/
│   ├── processed/
│   └── artifacts/
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_training.ipynb
│   ├── 04_evaluation_metrics.ipynb
│   ├── 05_explainability_shap.ipynb
│   ├── 06_privacy_preserving_pipeline.ipynb
│   └── 07_adversarial_threat_tests.ipynb
│
├── privacy/
│   ├── README.md
│   ├── dp_mechanism_demo.py
│   ├── k_anonymity_demo.py
│   ├── encryption_demo.py
│   └── pseudonymization_demo.py
│
├── security/
│   ├── threat_model.md
│   ├── threat_model_stride.md
│   ├── model_risk_analysis.md
│   ├── adversarial_test_fgsm.py
│   └── incident_response_plan.md
│
├── monitoring/
│   ├── monitoring_concept.md
│   ├── drift_monitor.py
│   ├── logging_strategy.md
│   ├── alert_thresholds.yaml
│   └── incident_response_playbook.md
│
├── docs/
│   ├── project_overview.md
│   ├── business_use_case.md
│   ├── business_impact.md
│   ├── compliance_mapping.md
│   ├── gdpr_mapping_table.md
│   ├── psd2_mapping_table.md
│   ├── ai_act_ce_declaration_draft.md
│   └── faq.md
│
├── executive/
│   ├── executive_summary_phase1.md
│   ├── roi_model.xlsx
│   ├── certification_alignment.md
│   ├── consulting_deck.pdf
│   └── linkedin_post_draft.txt
│
├── thought_leadership/
│   ├── whitepaper_outline.md
│   ├── linkedin_series.md
│   └── conference_pitch_deck.pptx
│
├── framework/
│   ├── audit_report_template.md
│   ├── dpo_interview_guide.md
│   └── stakeholder_comm_playbook.md
│
├── README.md
├── requirements.txt
└── LICENSE

```



