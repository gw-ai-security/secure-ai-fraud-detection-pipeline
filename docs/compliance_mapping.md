# Compliance Mapping (GDPR, PSD2 RTS, EU AI Act) – Secure AI Fraud Detection Pipeline

## 1. Purpose and Scope
This document provides a consolidated crosswalk of regulatory requirements and industry best practices for an AI-based fraud detection system in EU banking. It translates obligations from GDPR, PSD2 RTS, and the EU AI Act into implementable controls and audit evidence within this repository. It also aligns to recognized frameworks (ISO/IEC 27001 & 27701, NIST AI RMF) without creating new legal obligations.

## 2. Summary of Best Practices Adopted
- **Risk-based and privacy-by-design architecture** integrated from data ingestion to inference.
- **Data governance** covering data quality, lineage, minimization, and retention.
- **Human oversight & transparency** for high-impact decisions.
- **Security controls** for model, data, and pipeline; adversarial resilience and monitoring.
- **Comprehensive logging & audit trails** with evidence links for audits (internal, external, regulatory).
- **Post-deployment monitoring** including drift, performance, and incident response.

## 3. Master Crosswalk
The table maps key requirements to concrete controls and to where evidence lives in this repo.

| Domain | Requirement (Key Articles/Guidelines) | Control/Pattern Implemented | Evidence Path (Repo) | Owner | Frequency |
|---|---|---|---|---|---|
| GDPR | Art. 5(1)(c) Data minimisation; Art. 25 Privacy by Design; Art. 30 Records; Art. 32 Security | Collect only essential fields; pseudonymise identifiers; delete temp files; restrict access; maintain RoPA; security hardening for data & models | `docs/gdpr_mapping_table.md`, `privacy/pseudonymization_demo.py`, `privacy/privacy_config.json`, `monitoring/logging_strategy.md` | DPO, Security | Continuous; quarterly review |
| GDPR | Art. 35 DPIA where high risk | Threat model + DPIA-like analysis before go-live; document risks/mitigations | `security/threat_model_stride.md`, `security/model_risk_analysis.md` | DPO, CISO | Before material change |
| PSD2 RTS | SCA (Art. 97 PSD2; Delegated Reg. 2018/389), Transaction Risk Analysis (TRA), Monitoring, Audit trail | Real-time anomaly scoring to support SCA exemptions; justification logs; traceability of decisions | `docs/psd2_mapping_table.md`, `monitoring/logging_strategy.md`, `monitoring/alert_thresholds_config.yaml` | Payments Ops, Compliance | Continuous |
| PSD2/EBA | Fraud reporting templates and definitions | Map model outputs to PSD2 fraud categories; half-year reporting dataset extract | `docs/psd2_mapping_table.md` (Annex mapping), `monitoring/` exports | Compliance | Semi-annual |
| EU AI Act (High-Risk) | Art. 9 Risk mgmt system; Art. 10 Data governance; Art. 11 Technical documentation; Art. 13 Transparency; Art. 14 Human oversight; Art. 15 Accuracy/robustness/security | Document risk cycle; data specs, quality checks; tech docs; SHAP explainability; human-in-the-loop review for high-risk decisions; adversarial & robustness testing; defined accuracy targets | `docs/ai_act_ce_declaration_draft.md`, `notebooks/05_explainability_shap.ipynb`, `security/07_threat_adversarial_tests.ipynb`, `security/incident_response_plan.md` | Provider/Deployer, CISO, DPO | Pre-go-live; continuous monitoring |
| ISO/IEC 27001/27701 (good practice) | ISMS/PIMS controls for access, crypto, logging, retention | Role-based access, encryption-at-rest/in-transit (simulated), log integrity, retention schedule | `privacy/encryption_demo.py`, `monitoring/logging_strategy.md` | Security | Continuous |
| NIST AI RMF (good practice) | Govern–Map–Measure–Manage | Governance policy; risk mapping; measurement KPIs; risk response and monitoring | `docs/compliance_mapping.md`, `docs/business_impact.md`, `monitoring/drift_monitor.py` | AI Governance | Quarterly

## 4. Human Oversight and Transparency Plan (EU AI Act)
- **Decision categories:** automatic approval/decline, review-required. Review thresholds are configured and periodically reassessed.
- **Oversight roles:** Fraud Operations for case review; DPO oversight on privacy impacts; CISO for security events.
- **User-facing transparency:** Where legally required, inform users that a high-risk AI system is used; provide meaningful information on logic, significance, and envisaged consequences; enable contestation/appeal channels.
- **Records:** Store reviewer decisions, rationales, and overrides for auditability.

## 5. Data Governance Controls (GDPR Art. 5, 25; EU AI Act Art. 10)
- **Specification & provenance:** Define schemas, data sources, and lineage; retain metadata.
- **Quality checks:** Null, range, format, outlier checks; drift monitoring of distributions.
- **Minimisation & retention:** Only essential fields; retain derived features where possible; purge raw identifiers; retention schedule aligned to legal and business needs.
- **Pseudonymisation/anonymisation:** Hash user/account IDs; differential privacy for aggregates where feasible.

## 6. Security & Robustness Controls (GDPR Art. 32; EU AI Act Art. 15; PSD2 RTS)
- **Model security:** Adversarial testing (FGSM/PGD where applicable), input validation, score tamper protection.
- **Pipeline security:** Secrets management, least-privilege access, integrity checks for models and data artefacts.
- **Operational security:** Monitoring of inference latency, error rates, and abuse; alerting on anomalies.
- **Audit trails:** Immutable logs for inference requests, decisions, explanations, and reviewer actions.

## 7. Technical Documentation (EU AI Act Art. 11)
Maintain and version technical documentation including: intended purpose, system architecture, data specifications, training/validation procedures, performance metrics, known limitations, and monitoring plans. Evidence: `README.md`, `docs/*`, notebooks, and `security/*`.

## 8. Post-Deployment Monitoring and Incident Response
- **Drift & performance monitoring:** Statistical drift checks; periodic backtesting; recalibration when KPIs breach thresholds.
- **Incident taxonomy:** Model failure, data leakage, false positive spikes, SCA exemption misclassification.
- **Response playbooks:** Contain, roll back, notify stakeholders where required; maintain evidence for regulators.

## 9. Audit Evidence Index (Where to Look)
- **Regulatory mappings:** `docs/gdpr_mapping_table.md`, `docs/psd2_mapping_table.md`, `docs/ai_act_ce_declaration_draft.md`
- **Risk & oversight:** `security/threat_model_stride.md`, `security/model_risk_analysis.md`, `security/incident_response_plan.md`
- **Data governance:** `privacy/*`, `data/*`, `notebooks/*`
- **Monitoring:** `monitoring/*`

## 10. Change Control
Any change to model, data schema, thresholds, or exemption logic requires: impact analysis, DPO/CISO sign-off, updated documentation, and versioned release notes.

