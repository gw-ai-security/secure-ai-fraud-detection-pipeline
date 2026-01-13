# GDPR Mapping Table for Fraud Detection Pipeline

This document maps major components of the fraud detection pipeline to GDPR requirements. The intent is to show how Privacy-by-Design and data protection principles are documented in this portfolio project.

## Table: GDPR Compliance Mapping

| GDPR Article | Requirement | Implemented Measures | Evidence |
| --- | --- | --- | --- |
| Art. 5(1)(c) | Data minimization | Only essential transaction fields are used; no raw PII retained | `security/data_minimization.md`, `notebooks/01_data_cleaning.ipynb` |
| Art. 5(1)(e) | Storage limitation | Synthetic data used; derived artifacts versioned for learning only | `notebooks/data/`, `notebooks/models/` |
| Art. 5(2) | Accountability | Design decisions documented with version control | `docs/`, `executive/` |
| Art. 25 | Privacy by Design and Default | Privacy measures documented and applied where feasible | `security/data_minimization.md`, `docs/compliance_mapping.md` |
| Art. 30 | Record of processing activities | Logging strategy documented; pipeline operations tracked | `monitoring/logging_strategy.md` |
| Art. 32(1) | Security of processing | Access control concepts, logging, and audit trails | `security/threat_model.md`, `monitoring/logging_strategy.md` |
| Art. 33-34 | Breach notification (if applicable) | Incident response discussed conceptually | `docs/risk_register.md` |
| Art. 35 | DPIA | DPIA-like analysis via threat modeling and risk register | `security/threat_model_stride.md`, `docs/risk_register.md` |
| Art. 44 ff. | Transfers to third countries | No transfers; synthetic data only | N/A |

## Additional Notes
- Pseudonymization and differential privacy are documented as concepts but not implemented as standalone scripts in this repo.
- No personally identifiable information (PII) is stored or processed during model development or evaluation.
- The project is fully self-contained with synthetic data to avoid compliance risk during development.

## Regulatory Coverage Summary

| Area | Status | Comments |
| --- | --- | --- |
| GDPR Art. 5 | Covered | Data minimization and synthetic data constraints |
| GDPR Art. 25 | Covered | Privacy-by-Design documented |
| GDPR Art. 30 | Covered | Logging strategy documented |
| GDPR Art. 32 | Covered (conceptual) | Security controls documented |
| GDPR Art. 35 | Covered (conceptual) | DPIA-like analysis documented |
| GDPR Art. 44+ | Not applicable | No cross-border data transfer |

## Conclusion
This project aligns with GDPR principles by minimizing data, documenting privacy measures, and maintaining audit-ready documentation.

For PSD2 and EU AI Act mappings, see:
- `docs/psd2_mapping_table.md`
- `docs/ai_act_ce_declaration_draft.md`
