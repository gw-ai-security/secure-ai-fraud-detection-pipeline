# Threat Model - Secure AI Fraud Detection Pipeline

## Purpose
This document describes the security and AI-specific threat model for the Secure AI Fraud Detection Pipeline.
It is written for engineers, security reviewers, and auditors and follows a practical, risk-oriented approach.

The goal is not to claim perfect security, but to demonstrate structured security thinking in a regulated financial context.

## System Scope and Boundaries

In scope:
- Synthetic transaction data.
- Data cleaning and feature engineering pipeline.
- Feature preprocessing pipeline (`notebooks/models/feature_pipeline.pkl`).
- Train/test datasets.
- Offline model training (notebook-based).
- Stored artifacts (features, configs, metadata).

Out of scope:
- Production deployment.
- Real customer data.
- Real-time decisioning.
- External APIs.

## High-Level Architecture (Logical)
1. Synthetic transaction data (CSV).
2. Data cleaning notebook.
3. Feature engineering notebook.
4. Feature artifacts (Parquet, JSON, PKL).
5. Model training (notebook-based).
6. Evaluation and monitoring concepts.

Trust boundaries exist between:
- Raw data and processed data.
- Feature pipeline and model training.
- Artifact storage and execution environment.

## Threat Categories

### 1. Data Poisoning
Description:
Manipulation of input data to influence model behavior.

Risk example:
Injected fraudulent patterns during training could bias detection results.

Mitigations:
- Synthetic data only.
- Versioned datasets.
- Reproducible notebooks.
- Deterministic random seeds.

### 2. Model Inversion
Description:
Attacker attempts to reconstruct sensitive data from model outputs.

Risk example:
Re-identification of user behavior patterns.

Mitigations:
- No direct PII used.
- Aggregated and derived features.
- No public model API.
- Offline-only usage.

### 3. Membership Inference
Description:
Determining whether a specific record was part of training data.

Risk example:
Inference of user participation.

Mitigations:
- Synthetic dataset.
- No individual-level identifiers exposed.
- Regularization during training (conceptual).

### 4. Unauthorized Artifact Access
Description:
Access to feature artifacts or preprocessing pipeline.

Risk example:
Tampering with `notebooks/models/feature_pipeline.pkl`.

Mitigations:
- Clear artifact separation.
- Version control (Git).
- Intended read-only usage for inference.
- Hash-based verification (future step).

### 5. Concept Drift
Description:
Change in data distribution over time.

Risk example:
Fraud patterns evolve, model degrades.

Mitigations:
- Monitoring concept documented.
- Feature statistics stored.

## Risk Summary Table

| Threat | Likelihood | Impact | Mitigation Strength |
| --- | --- | --- | --- |
| Data Poisoning | Low | Medium | Strong |
| Model Inversion | Very Low | High | Strong |
| Membership Inference | Very Low | Medium | Strong |
| Artifact Tampering | Low | High | Medium |
| Concept Drift | Medium | High | Planned |

## Security-by-Design Principles Applied
- Least data principle.
- Reproducibility over opacity.
- Explicit trust boundaries.
- Artifact immutability mindset.
- Audit readiness.

## Limitations
This project is:
- Educational.
- Offline.
- Non-production.

It demonstrates security-aware AI engineering practices, not a fully hardened banking system.

## Reviewer Notes
This threat model is intentionally simple, transparent, and explainable.
It is designed to support:
- Technical interviews.
- Security reviews.
- AI governance discussions.
