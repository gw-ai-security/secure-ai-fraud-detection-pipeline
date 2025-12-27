# Threat Model – Secure AI Fraud Detection Pipeline

## Purpose
This document describes the **security and AI-specific threat model** for the Secure AI Fraud Detection Pipeline.
It is written for **engineers, security reviewers, and auditors** and follows a practical, risk-oriented approach.

The goal is not to claim perfect security, but to demonstrate **structured security thinking** in a regulated financial context.

---

## System Scope & Boundaries

### In Scope
- Synthetic transaction data
- Data cleaning and feature engineering pipeline
- Feature preprocessing pipeline (`feature_pipeline.pkl`)
- Train/test datasets
- Offline model training (future step)
- Stored artefacts (features, configs, metadata)

### Out of Scope
- Production deployment
- Real customer data
- Real-time decisioning
- External APIs

---

## High-Level Architecture (Logical)

1. Synthetic transaction data (CSV)
2. Data cleaning notebook
3. Feature engineering notebook
4. Feature artefacts (Parquet, JSON, PKL)
5. Model training (planned)
6. Evaluation & monitoring (planned)

Trust boundaries exist between:
- Raw data and processed data
- Feature pipeline and model training
- Artefact storage and execution environment

---

## Threat Categories

### 1. Data Poisoning
**Description:**  
Manipulation of input data to influence model behavior.

**Risk Example:**  
Injected fraudulent patterns during training could bias detection results.

**Mitigations:**
- Synthetic data only
- Versioned datasets
- Reproducible notebooks
- Deterministic random seeds

---

### 2. Model Inversion
**Description:**  
Attacker attempts to reconstruct sensitive data from model outputs.

**Risk Example:**  
Re-identification of user behavior patterns.

**Mitigations:**
- No direct PII used
- Aggregated and derived features
- No public model API
- Offline-only usage

---

### 3. Membership Inference
**Description:**  
Determining whether a specific record was part of training data.

**Risk Example:**  
Inference of user participation.

**Mitigations:**
- Synthetic dataset
- No individual-level identifiers exposed
- Planned regularization during training

---

### 4. Unauthorized Artefact Access
**Description:**  
Access to feature artefacts or preprocessing pipeline.

**Risk Example:**  
Tampering with `feature_pipeline.pkl`.

**Mitigations:**
- Clear artefact separation
- Version control (Git)
- Intended read-only usage for inference
- Hash-based verification (future step)

---

### 5. Concept Drift
**Description:**  
Change in data distribution over time.

**Risk Example:**  
Fraud patterns evolve, model degrades.

**Mitigations:**
- Drift detection planned
- Feature statistics stored
- Monitoring module planned

---

## Risk Summary Table

| Threat | Likelihood | Impact | Mitigation Strength |
|------|------------|--------|---------------------|
| Data Poisoning | Low | Medium | Strong |
| Model Inversion | Very Low | High | Strong |
| Membership Inference | Very Low | Medium | Strong |
| Artefact Tampering | Low | High | Medium |
| Concept Drift | Medium | High | Planned |

---

## Security-by-Design Principles Applied

- Least data principle
- Reproducibility over opacity
- Explicit trust boundaries
- Artefact immutability mindset
- Audit-readiness

---

## Limitations

This project is:
- Educational
- Offline
- Non-production

It demonstrates **security-aware AI engineering practices**, not a fully hardened banking system.

---

## Reviewer Notes

This threat model is intentionally simple, transparent, and explainable.
It is designed to support:
- Technical interviews
- Security reviews
- AI governance discussions
