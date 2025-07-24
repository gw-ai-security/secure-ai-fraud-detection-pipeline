# GDPR Mapping Table for Fraud Detection Pipeline

This document maps each major component of the fraud detection pipeline to the corresponding requirements of the General Data Protection Regulation (GDPR), with a focus on Articles 5, 25, 30, and 32. The goal is to demonstrate how this project implements Privacy by Design and ensures data protection throughout the machine learning lifecycle.

## Table: GDPR Compliance Mapping

| GDPR Article     | Requirement                              | Implemented Measures                                          | Affected Component(s)               |
|------------------|-------------------------------------------|----------------------------------------------------------------|-------------------------------------|
| **Art. 5(1)(c)** | Data Minimization                         | Only essential transaction fields used; no raw PII retained   | data/, notebooks/, feature_engineering |
| **Art. 5(1)(e)** | Storage Limitation                        | No permanent storage of user-level data; temp files deleted   | data/, privacy/, monitoring/        |
| **Art. 5(2)**    | Accountability                            | All design decisions documented with version control          | docs/, framework/, executive/       |
| **Art. 25**      | Privacy by Design & Default               | DP techniques (noise injection, k-anonymity), pseudonymization | privacy/, notebooks/, models/       |
| **Art. 30**      | Record of Processing Activities           | Logging strategy documented; pipeline operations tracked      | monitoring/logging_strategy.md      |
| **Art. 32(1)**   | Security of Processing                    | Access control, model encryption (simulated), audit trails    | privacy/, security/, monitoring/    |
| **Art. 33–34**   | Breach Notification (if applicable)       | Incident response plan with model failure detection           | monitoring/incident_response_playbook.md |
| **Art. 35**      | Data Protection Impact Assessment (DPIA)  | Risk mapping included, CE-simulation covers compliance risk   | docs/threat_model.md, ai_act_ce_declaration_draft.md |
| **Art. 44 ff.**  | Transfers to Third Countries              | No transfer of data outside of EU; simulated data only        | N/A (fully synthetic)               |

## Additional Notes

- Pseudonymization is performed on `user_id` and `account_id` fields using SHA-256 hashing.
- Differential privacy is implemented in the model training phase using calibrated Gaussian noise on aggregated features.
- No personally identifiable information (PII) is stored or processed during model development or evaluation.
- The project is fully self-contained with synthetic data to avoid compliance risk during development.

## Regulatory Coverage Summary

| Area                | Status       | Comments                                        |
|---------------------|--------------|-------------------------------------------------|
| GDPR Art. 5         | Fully covered | Data minimization, storage limitation enforced  |
| GDPR Art. 25        | Fully covered | Privacy by design integrated across pipeline    |
| GDPR Art. 30        | In progress  | Logging templates and versioned documentation   |
| GDPR Art. 32        | Partially covered | Simulated encryption and incident logging   |
| GDPR Art. 35        | Included     | DPIA-like elements documented in threat model   |
| GDPR Art. 44+       | Not applicable | No cross-border data transfer (synthetic only) |

## Conclusion

This project adheres to GDPR principles by applying privacy-enhancing techniques, minimizing data collection, maintaining detailed documentation, and aligning with Privacy by Design principles. All mappings are kept under version control to support audits, stakeholder reporting, and regulatory reviews.

For a full mapping to PSD2 and the EU AI Act, refer to:

- `psd2_mapping_table.md`
- `ai_act_ce_declaration_draft.md`
