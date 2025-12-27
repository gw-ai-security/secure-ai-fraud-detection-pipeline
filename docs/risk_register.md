# Risk Register – Secure AI Fraud Detection Pipeline

## Purpose
This risk register documents **technical, security, privacy, and governance risks**
associated with the project, along with mitigation strategies.

---

## Risk Register

| ID | Risk Description | Category | Impact | Likelihood | Mitigation |
|----|------------------|----------|--------|------------|------------|
| R1 | Model overfitting on synthetic patterns | AI/ML | Medium | Medium | Conservative models, limited features |
| R2 | False positives causing operational overhead | Business | High | Medium | Threshold tuning, explainability |
| R3 | Feature leakage of personal data | Privacy | High | Low | Data minimization, synthetic data |
| R4 | Model manipulation via adversarial inputs | Security | Medium | Low | Robust preprocessing, monitoring |
| R5 | Lack of explainability | Compliance | High | Medium | SHAP, documented features |
| R6 | Reproducibility issues across environments | Engineering | Medium | Medium | Version-pinned dependencies |
| R7 | Misinterpretation of outputs by stakeholders | Governance | Medium | Medium | Documentation, disclaimers |
| R8 | Unauthorized model access | Security | High | Low | Access control, repo hygiene |
| R9 | Drift undetected over time | AI/ML | High | Medium | Monitoring notebooks |
| R10| Regulatory misalignment | Compliance | High | Low | Explicit GDPR / EU AI Act mapping |

---

## Risk Treatment Strategy

- Avoidance: no real data usage
- Reduction: explainability, documentation
- Acceptance: limited scope risks (portfolio context)

---

## Regulatory Mapping

- **GDPR Art. 5**: Data minimization
- **GDPR Art. 25**: Privacy by design
- **EU AI Act**: Risk awareness & transparency
- **ISO/IEC 27001**: Risk-based security controls

---

## Review Notes

This risk register is:
- Living documentation
- Intended for interviews, audits, and reviews
- Not a legal compliance statement
