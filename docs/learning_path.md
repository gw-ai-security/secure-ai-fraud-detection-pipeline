# Learning Path

This project is designed as a structured learning experience. Follow the steps below in order.

## Prerequisites
- Python basics and virtual environments.
- Introductory ML concepts (features, training, evaluation).
- Basic security and privacy terminology (PII, threat models).

## Step 0: Environment check
Notebook: `notebooks/00_environment_check.ipynb`
You will learn:
- How to verify Python and library setup.
- How to validate the runtime before modeling work.

## Step 1: Data cleaning
Notebook: `notebooks/01_data_cleaning.ipynb`
You will learn:
- How to inspect and clean raw transaction data.
- How to standardize schemas and remove invalid rows.
Outputs:
- `notebooks/data/processed/fraud_cleaned.csv`

## Step 2: Feature engineering
Notebook: `notebooks/02_feature_engineering.ipynb`
You will learn:
- How to engineer risk-relevant features.
- How to define an explicit feature contract.
Outputs:
- `notebooks/data/processed/features.csv`
- `notebooks/data/processed/features.parquet`
- `notebooks/models/feature_config.json`
- `notebooks/models/feature_names.json`

## Step 3: Model training
Notebook: `notebooks/03_model_training.ipynb`
You will learn:
- How to train an Isolation Forest model for anomaly detection.
- How to preserve model artifacts and metadata.
Outputs:
- `notebooks/models/feature_pipeline.pkl`
- `notebooks/models/feature_scaler.pkl`
- `models/model_metadata.json`

## Step 4: Read the model docs
Docs:
- `docs/model_training.md`
- `docs/model_inference.md`
You will learn:
- Training and inference boundaries.
- How to reason about reproducibility and auditability.

## Step 5: Governance and security
Docs:
- `docs/compliance_mapping.md`
- `security/threat_model.md`
- `security/threat_model_stride.md`
- `docs/risk_register.md`
You will learn:
- How to document compliance mappings.
- How to communicate ML risks and mitigations.

## Step 6: Business and executive framing
Docs:
- `docs/business_use_case.md`
- `docs/business_impact.md`
- `executive/executive_summary_phase1.md`
You will learn:
- How to explain technical systems in business terms.
- How to quantify impact and ROI assumptions.

## Completion checklist
- You can explain the full pipeline from data to model.
- You can justify why unsupervised modeling is used here.
- You can point to the governance artifacts for risk and privacy.
- You can summarize the business impact assumptions.
