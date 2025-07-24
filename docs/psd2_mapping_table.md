# PSD2 Mapping Table for AI-Based Fraud Detection

This document outlines how the AI fraud detection pipeline aligns with the regulatory requirements of the **Revised Payment Services Directive (PSD2)**, with a focus on real-time detection, Strong Customer Authentication (SCA), risk analysis, and auditability.

## Table: PSD2 Compliance Mapping

| PSD2 Requirement                          | Description                                                             | Implementation in This Project                    |
|-------------------------------------------|-------------------------------------------------------------------------|---------------------------------------------------|
| **Art. 97** – Strong Customer Authentication (SCA) | Enforce multi-factor authentication for payment transactions            | Fraud risk model supports real-time SCA exemption evaluation |
| **RTS Ch. 2, Art. 2–3** – Risk-Based Approach | Continuous transaction risk assessment required                         | Isolation Forest used to assess transaction anomalies |
| **RTS Art. 10** – Transaction Monitoring   | Ongoing monitoring to detect abnormal behaviour                         | Real-time scoring and drift detection integrated    |
| **RTS Art. 13** – Exemptions from SCA      | Fraud detection system must justify SCA exemption                       | Model output includes fraud probability + justification log |
| **RTS Art. 19** – Data Protection          | Risk engine must operate in compliance with GDPR                        | GDPR-compliant data minimization, pseudonymization, and logging strategy |
| **RTS Art. 20** – Audit Trail              | Transactions must be traceable for audit and post-incident analysis     | Audit trail logging system and explainable model outputs provided |
| **Annex II** – Fraud Classification Codes  | Classification of fraud types for reporting                             | Fraud scenarios are mapped to PSD2 categories (e.g. CNP fraud, login takeover) |

## Fraud Scenario Mapping (PSD2 Annex II)

| Scenario                 | PSD2 Code      | Included in Model? | Notes                               |
|--------------------------|----------------|--------------------|--------------------------------------|
| Card Not Present (CNP)   | 5.1.3          | Yes                | Simulated via synthetic online purchases |
| Login Takeover           | 5.2.2          | Yes                | Unusual IP/device access patterns     |
| Social Engineering       | 5.3.1          | Optional (future)  | Requires NLP enrichment               |
| Malware / Bot Attacks    | 5.3.2          | Optional           | To be modeled with adversarial examples |
| Internal Fraud           | 5.4.1          | No                 | Outside current use case scope        |

## Summary of PSD2 Alignment

| Area                 | Coverage Level    | Comments                                      |
|----------------------|-------------------|-----------------------------------------------|
| Risk Engine Design   | Fully covered     | Isolation Forest + privacy-enhanced preprocessing |
| SCA Support          | Partially covered | Exemption scoring simulated, not enforced     |
| Audit Trail          | Fully covered     | Logging, incident response, explainability    |
| Data Protection      | Fully covered     | Aligns with GDPR principles (see separate mapping) |
| Reporting Compliance | In progress       | Classification available, not yet automated   |

## Conclusion

This AI-based fraud detection pipeline satisfies the risk management and monitoring expectations of PSD2 while operating under full data protection compliance. Exemption handling, auditability, and fraud classification are explicitly designed for PSD2 RTS interpretation.
