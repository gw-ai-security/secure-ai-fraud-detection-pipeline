# Threat Model - STRIDE for Secure AI Fraud Detection Pipeline

## 1. Purpose and Scope
This document applies STRIDE threat modeling to the Secure AI Fraud Detection Pipeline.
It covers data ingestion, feature engineering, model training, serving, monitoring, and analyst access.
The scope is aligned with banking-grade environments (PSD2) and high-risk AI classification under the EU AI Act.

## 2. System Overview
Components:
- E1 External sources: core banking, transaction logs, authentication events.
- P1 Ingestion service: validation, pseudonymization, schema enforcement.
- D1 Raw datastore: encrypted at rest, access-controlled.
- P2 Feature pipeline: cleaning, engineering, scaling, DP where feasible.
- D2 Feature store: versioned, lineage tracked, encrypted.
- P3 Model training: offline (Isolation Forest, DP simulations, SHAP explainability).
- D3 Model registry: signed artifacts, reproducible training, version control.
- P4 Serving API: real-time scoring, thresholds, alerting.
- P5 Monitoring service: drift detection, adversarial test hooks, audit logging.
- A1 Analyst UI: role-based dashboards, executive reporting.
- Auditors/Regulators: controlled read-only exports.

## 3. Assets and Security Objectives
- PII and financial data: confidentiality, minimization, unlinkability.
- Model artifacts: integrity, provenance, reproducibility.
- Serving endpoints: availability, abuse resistance.
- Logs and evidence: tamper-proof, audit-ready, retention aligned with GDPR.

## 4. STRIDE Analysis

### Spoofing
- Risk: API key theft, service impersonation (ingestion/serving).
- Controls: mTLS, OIDC with short-lived tokens, device identity, IP allowlists.

### Tampering
- Risk: Data poisoning, model registry manipulation.
- Controls: Signed datasets, WORM storage for registry, reproducible pipelines, CI/CD policy-as-code.

### Repudiation
- Risk: Analysts or admins deny changes or model deployments.
- Controls: Cryptographic signing, append-only audit logs, JWS for approvals.

### Information Disclosure
- Risk: Model inversion, logs exposing PII, feature leakage.
- Controls: Pseudonymization, differential privacy, output redaction, role-based dashboards.

### Denial of Service
- Risk: Flooding serving API with scoring requests, monitoring overload.
- Controls: Autoscaling and quotas, WAF and rate limiting, caching, circuit breakers.

### Elevation of Privilege
- Risk: Lateral movement via service accounts, dev-to-prod access escalation.
- Controls: JIT access, least privilege IAM, workload identity federation, separate tenants.

## 5. Adversarial ML Threats
- Evasion: Perturbed inputs bypass detection, mitigated with preprocessing, ensembles, threshold tuning, adversarial retraining.
- Poisoning: Malicious samples in training, mitigated with canary datasets, provenance checks, hash manifests.
- Model inversion/stealing: Attackers extract model behavior, mitigated with output limiting, watermarking, randomized rounding.
- Drift exploitation: Adversaries exploit stale thresholds, mitigated with documented monitoring concepts (`monitoring/monitoring_concept.md`).

## 6. Control Mapping
- ISO/IEC 27001: A.5 identity, A.8 data security, A.12 monitoring.
- GDPR: Art. 5 (minimization), Art. 25 (Privacy-by-Design), Art. 32 (security of processing).
- EU AI Act: High-risk AI, risk management, technical documentation, logging, human oversight.
- PSD2: Strong Customer Authentication, fraud monitoring obligations.

## 7. Validation and Test Cases
- Invalid client certificates rejected at serving endpoint (P4).
- Attempt to push unsigned model blocked at registry (D3).
- Drift injection alert raised and logged (P5).
- Adversarial testing is planned as a future extension.

## 8. Residual Risk and Acceptance
- Adversarial ML is an evolving threat; residual risk remains medium.
- Documented in `docs/risk_register.md` with ownership and review cycle.

## 9. Change and Review
- Reviewed quarterly or after significant architecture change.
- Linked to risk register, incident response plan, and executive summaries.
