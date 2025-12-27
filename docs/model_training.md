# Model Training Strategy

## Purpose
This document describes the **model training approach** used in the Secure AI Fraud Detection Pipeline.
The goal is not maximum predictive performance, but **robust, explainable, and auditable ML behavior** suitable for regulated financial environments.

---

## Training Objectives

- Detect anomalous or fraudulent transaction patterns
- Minimize false positives to reduce operational burden
- Ensure reproducibility and auditability
- Avoid privacy leakage or memorization of sensitive patterns

---

## Learning Paradigm

### Primary Mode: Unsupervised / Semi-Supervised

**Rationale**
- Real-world fraud labels are scarce, delayed, or unreliable
- Supports early-stage fraud discovery
- Aligns with realistic banking constraints

**Candidate Models**
- Isolation Forest (baseline)
- One-Class SVM (optional)
- Local Outlier Factor (exploratory)

Supervised models (e.g. Logistic Regression, XGBoost) are optional extensions if high-quality labels become available.

---

## Feature Usage

Only features defined in:
- `models/feature_names.json`
- `models/feature_config.json`

are allowed for training.

This ensures:
- Consistency between training and inference
- Explicit control over data minimization

---

## Train / Test Strategy

- Default: 80/20 random split
- If labels exist: stratified split
- If no labels: hold-out validation for drift detection

No cross-user leakage is allowed.

---

## Security Considerations

- Models are trained only on synthetic data
- Serialized models (`.pkl`) are treated as derived artefacts
- Feature pipelines are versioned separately from models

---

## Explainability & Review

- Feature attribution via SHAP (later stage)
- Model decisions must be explainable to:
  - Risk Management
  - Compliance
  - Auditors

---

## Limitations

- Not production-grade
- No real-time scoring
- No automated retraining loop

---

## Portfolio Value

This setup demonstrates:
- Secure ML lifecycle thinking
- Regulatory awareness
- Practical AI governance skills
