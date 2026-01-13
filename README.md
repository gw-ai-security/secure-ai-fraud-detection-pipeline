# Secure AI Fraud Detection Pipeline

Portfolio and learning project that simulates an EU banking fraud detection pipeline with Security-by-Design, Privacy-by-Design, and audit-ready documentation.

Important: This project uses synthetic data only. No real customer data or PII is processed.

## What this project demonstrates
- End-to-end ML pipeline flow (data -> features -> model -> monitoring concepts).
- Secure and privacy-aware ML engineering practices.
- Regulatory alignment thinking for GDPR, PSD2, and the EU AI Act.
- Clear, reviewable artifacts suitable for interviews and learning.

## What you will learn
- How to design a fraud detection pipeline with governance in mind.
- How to structure features, training, and inference for auditability.
- How to document risk, privacy, and security controls.
- How to communicate ML work to compliance and executive stakeholders.

## Skills demonstrated
See `docs/skills_matrix.md` for a full skill-to-evidence mapping.

Highlights:
- Python, pandas, scikit-learn, and notebook-based experimentation.
- Feature engineering, anomaly detection, and evaluation logic.
- Threat modeling (STRIDE) and risk documentation.
- Privacy patterns: data minimization, pseudonymization, and DP concepts.

## Learning path (recommended)
Follow the guided path in `docs/learning_path.md`.

Quick order:
1. `notebooks/00_environment_check.ipynb`
2. `notebooks/01_data_cleaning.ipynb`
3. `notebooks/02_feature_engineering.ipynb`
4. `notebooks/03_model_training.ipynb`
5. Read the governance docs in `docs/` and `security/`.

## Quickstart

### Option A: GitHub Codespaces
1. Create a codespace for this repo.
2. In the terminal:

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

### Option B: Run locally

Prereqs: Python 3.10+ and Git.

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
# source .venv/bin/activate

pip install --upgrade pip
pip install -r requirements.txt
```

## Expected outputs
The notebooks produce the following artifacts in `notebooks/data/processed` and `notebooks/models`:
- Cleaned dataset: `fraud_cleaned.csv`
- Feature datasets: `features.csv`, `features.parquet`
- Train/test splits: `X_train.parquet`, `X_test.parquet`
- Feature metadata: `feature_config.json`, `feature_names.json`
- Derived model artifacts: `feature_pipeline.pkl`, `feature_scaler.pkl`

These are versioned to support traceability and reproducibility in a learning context.

## Repository tour
- `notebooks/`: Step-by-step pipeline notebooks.
- `docs/`: Business, compliance, and model documentation.
- `security/`: Threat modeling and security artifacts.
- `monitoring/`: Drift monitoring and logging strategy.
- `models/`: Example trained model artifacts and metadata.
- `executive/`: Executive summary for recruiter-style reviews.

## Recruiter summary (one-minute read)
- Scope: Fraud detection pipeline with governance and compliance mapping.
- Data: Fully synthetic, EU banking context.
- Focus: Security, privacy, auditability, and explainability.
- Evidence: See `docs/index.md` for a curated doc map.

## Disclaimer
This is a simulation and learning project. It does not claim production readiness or legal compliance.

## License
See `LICENSE`.
