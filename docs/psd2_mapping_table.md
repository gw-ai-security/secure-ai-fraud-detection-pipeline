# PSD2 Mapping Table for AI-Based Fraud Detection

This document outlines how the AI fraud detection pipeline aligns with the regulatory requirements of PSD2, with a focus on transaction risk analysis, monitoring concepts, and auditability.

## Table: PSD2 Compliance Mapping

| PSD2 Requirement | Description | Implementation in This Project |
| --- | --- | --- |
| Art. 97 - Strong Customer Authentication (SCA) | Enforce multi-factor authentication for payment transactions | Fraud risk model supports SCA exemption reasoning (conceptual) |
| RTS Ch. 2, Art. 2-3 - Risk-Based Approach | Continuous transaction risk assessment required | Isolation Forest used to assess transaction anomalies |
| RTS Art. 10 - Transaction Monitoring | Ongoing monitoring to detect abnormal behavior | Monitoring and logging strategy documented |
| RTS Art. 13 - Exemptions from SCA | Fraud detection system must justify SCA exemption | Model output includes risk score and thresholding |
| RTS Art. 19 - Data Protection | Risk engine must operate in compliance with GDPR | GDPR-aligned data minimization and logging strategy |
| RTS Art. 20 - Audit Trail | Transactions must be traceable for audit and post-incident analysis | Logging strategy and audit trail documented |
| Annex II - Fraud Classification Codes | Classification of fraud types for reporting | Fraud scenarios mapped to PSD2 categories |

## Fraud Scenario Mapping (PSD2 Annex II)

| Scenario | PSD2 Code | Included in Model? | Notes |
| --- | --- | --- | --- |
| Card Not Present (CNP) | 5.1.3 | Yes | Simulated via synthetic online purchases |
| Login Takeover | 5.2.2 | Yes | Unusual IP/device access patterns |
| Social Engineering | 5.3.1 | Optional (future) | Requires NLP enrichment |
| Malware / Bot Attacks | 5.3.2 | Optional (future) | Requires additional signals |
| Internal Fraud | 5.4.1 | No | Outside current use case scope |

## Summary of PSD2 Alignment

| Area | Coverage Level | Comments |
| --- | --- | --- |
| Risk Engine Design | Covered | Isolation Forest and documented controls |
| SCA Support | Partially covered | Exemption reasoning simulated, not enforced |
| Audit Trail | Covered | Logging and audit concepts documented |
| Data Protection | Covered | Aligns with GDPR principles |
| Reporting Compliance | In progress | Classification available, reporting not automated |

## Conclusion
This AI-based fraud detection pipeline aligns with PSD2 risk management and monitoring expectations through documented controls and clear data protection mapping.
