# Model Inference Strategy

## Purpose
This document explains how the fraud detection model is intended to be used after training (inference/scoring).
It focuses on secure, auditable, and operationally realistic inference patterns for a regulated banking context.

This is a portfolio simulation. It does not claim production readiness.

## Inference Modes

### 1) Batch Scoring (Primary)
Description:
- Score transactions in periodic batches (e.g., hourly, daily).
- Typical for back-office fraud investigation workflows.

Why this is realistic:
- Supports human review processes.
- Easier monitoring and audit trails.
- Lower operational complexity.

Outputs:
- Anomaly score per transaction.
- Risk bucket (low/medium/high).
- Optional explanation artifacts (later).

### 2) Near Real-Time Scoring (Optional Extension)
Description:
- Score transactions shortly after event ingestion.
- Requires stricter latency and availability controls.

Why it is not the baseline here:
- Increases complexity (queues, services, scaling, incident response).
- Requires stronger production controls beyond portfolio scope.

## Input Contract (What the model expects)

Source of truth:
- `feature_pipeline.pkl`
- `feature_config.json`
- `feature_names.json`

Allowed inputs:
Only columns explicitly listed in `feature_config.json` may be used.
All other columns must be dropped.

This enforces:
- data minimization,
- consistent feature space,
- reduced leakage risk.

## Output Contract (What the system produces)

Core outputs:
- `anomaly_score` (float).
- `risk_bucket` (categorical label derived from a threshold).
- `model_version` (string).
- `pipeline_version` (string).
- `scored_at` (timestamp).

Human-in-the-Loop (HITL):
High-risk predictions are never auto-actioned in this portfolio setup.
Instead they are routed to a reviewer queue.

## Thresholding Strategy

Default approach:
- Start with conservative thresholds.
- Adjust based on operational review capacity, false-positive tolerance, and business impact.

Documentation requirement:
Threshold changes must be tracked in Git (config file) and documented with rationale.

## Security and Integrity Controls

Artifact integrity:
- Treat `feature_pipeline.pkl` and model files as derived artifacts.
- Future improvement: store hashes and verify before scoring.

Access control (conceptual):
- Score jobs run in restricted environments.
- No hardcoded secrets.
- Separate read/write permissions for artifacts.

## Privacy Considerations
- No direct identifiers in feature space.
- Scores should not include personal data.
- Explanations must avoid exposing sensitive attributes.

## Limitations (Portfolio Scope)
- Offline notebooks only.
- No API endpoint.
- No service hardening.
- No production IAM.

## Reviewer Notes
This document demonstrates:
- clear inference contracts,
- separation of training vs. inference concerns,
- operational realism and governance thinking.
