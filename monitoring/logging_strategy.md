# Logging and Audit Strategy - Secure AI Fraud Detection Pipeline

## 1. Purpose and Scope
Define a unified logging and audit trail approach for the fraud detection pipeline to ensure:
- Security: tamper-evident, integrity-protected logs.
- Privacy: GDPR-aligned minimization and redaction.
- Auditability: evidence for EU AI Act, PSD2, ISO/IEC 27001, NIST AI RMF.
- Operational monitoring: drift and performance signals (conceptual).

## 2. Log Categories
- Security and audit logs: authentication attempts, key usage, access grants, model promotions.
- Data lineage logs: dataset version, feature set hash, transformation IDs, signer identity.
- Inference and serving logs: request_id, client_id (pseudonymized), model version, score summaries (no raw PII).
- Monitoring logs: drift metrics, thresholds, and retrain decisions (conceptual).

## 3. Data Minimization and Privacy
- No raw PII (no PANs, account numbers, or names in logs).
- Use hashed or pseudonymized identifiers (SHA-256 with salt, or UUID).
- Redact free-text fields.
- Retention aligned with GDPR Art. 5(1)(e) - default 180 days, exceptions for legal hold.

## 4. Controls and Protections
- Integrity: append-only storage (e.g., WORM/S3 Object Lock), hash chaining, periodic notarization.
- Confidentiality: AES-256 encryption at rest, TLS 1.3 in transit, KMS-managed key rotation.
- Access: RBAC plus Just-In-Time (JIT) access; break-glass accounts require dual approval.
- Monitoring: anomaly detection on log volume and access patterns.

## 5. Example JSON Schema (Inference Log)
```json
{
  "ts": "2025-08-17T12:00:00Z",
  "kind": "inference",
  "request_id": "rq-123abc",
  "client_id": "svc-risk-scorer",
  "model_version": "iforest-2025.08.12",
  "input_schema_hash": "sha256:...",
  "score_p50": 0.12,
  "score_p95": 0.89,
  "decision": "review",
  "pii": false
}
```

## 6. Alerting and Thresholds
- Thresholds are versioned in `models/thresholds.json`.
- Examples: PSI drift > 0.2, JSD > 0.05, FP-rate > 7%, fraud loss avoided < 100k/week.
- Alerts routed to on-call SOC and MLOps team.

## 7. Audit and Evidence Pack
- Quarterly integrity verification of logs (hash validation).
- Export pack includes log samples, retention proof, and access review evidence.
- Cross-reference with `docs/risk_register.md`.

## 8. Compliance Mapping
- GDPR: Art. 5 (accountability), Art. 25 (Privacy by Design), Art. 32 (security of processing).
- EU AI Act: logging, traceability, human oversight for high-risk AI.
- ISO/IEC 27001: A.8.15 (logging), A.8.16 (monitoring activities), A.5 (identity).
- PSD2: Strong Customer Authentication logs, fraud monitoring evidence.

## 9. Review and Change Management
- Reviewed every 6 months or after material system change.
- Approval required by DPO, CISO, and MLOps lead.
