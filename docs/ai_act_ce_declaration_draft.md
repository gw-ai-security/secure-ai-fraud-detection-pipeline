# EU AI Act – CE Declaration (Draft Simulation)

This document simulates the structure of a **CE declaration of conformity** under the **EU Artificial Intelligence Act (AI Act)** for the use case of anomaly-based fraud detection in a banking context.

**Disclaimer:** This is a simulated example for educational and strategic consulting purposes only. It is not a legally binding document.

## 1. System Overview

| Attribute             | Value                                               |
|----------------------|-----------------------------------------------------|
| System Name          | Secure AI Fraud Detection Pipeline                  |
| Intended Purpose     | Detection of anomalous transactions in banking apps |
| Provider             | [Your Name / Organization]                          |
| Deployment Context   | EU-regulated financial institutions (PSD2 context)  |

## 2. AI Act Classification

| AI Act Article    | Assessment                                      |
|-------------------|-------------------------------------------------|
| **Art. 6**        | Classified as **High-Risk AI System** (Annex III.5.a: Credit, insurance, fraud scoring) |
| **Art. 9**        | Risk management system implemented via threat modeling and explainability |
| **Art. 10**       | Data governance includes anonymization, minimization, DP noise, and full traceability |
| **Art. 11**       | CE Declaration simulated via this document     |
| **Art. 13**       | Explainability ensured via SHAP                |
| **Art. 14**       | Human oversight optional (can be integrated into review loop) |
| **Art. 15**       | Robustness, accuracy, security via STRIDE + adversarial testing |

## 3. Risk Management Summary

- **Threat Model:** STRIDE-based threat analysis conducted on data, model, API, and inference level
- **Explainability:** SHAP-based local/global interpretability included in reports
- **Adversarial Testing:** FGSM-based evaluation of model robustness to input perturbations
- **Failover Plan:** Model drift alerts + fallback decision thresholds documented

## 4. Compliance Artefacts

| Document                              | Reference Path                         |
|---------------------------------------|----------------------------------------|
| GDPR Mapping                          | `docs/gdpr_mapping_table.md`           |
| PSD2 Mapping                          | `docs/psd2_mapping_table.md`           |
| Risk Assessment                       | `docs/threat_model.md`                 |
| Explainability Report                 | `notebooks/05_explainability_shap.ipynb` |
| Data Minimization Strategy            | `privacy/privacy_strategy.md`          |
| Logging & Audit Trail Design          | `monitoring/logging_strategy.md`       |
| CE Declaration Draft                  | This document                          |

## 5. Summary

This system is built to simulate conformance with the EU AI Act as a high-risk AI system under Annex III. Through privacy engineering, threat modeling, risk documentation, and explainability, the solution aligns with Articles 6–15 of the Act.

For production deployment, a formal conformity assessment procedure would need to be performed by a notified body or self-assessment, depending on risk and sector.
