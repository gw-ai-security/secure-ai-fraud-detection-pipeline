# Project Overview – Secure AI Fraud Detection Pipeline

## Purpose of this Project
This repository is a **learning and portfolio project** that simulates how an AI-based fraud detection system can be designed in a **regulated EU banking environment**.

The goal is **not** to claim production readiness or legal compliance, but to demonstrate:
- structured thinking,
- secure and privacy-aware ML engineering,
- and audit-ready artefact creation.

All data used in this project is **synthetic**.

---

## Problem Statement (Simulated)
Financial institutions must detect suspicious transactions early while complying with:
- strict data protection requirements (GDPR),
- operational risk controls,
- and increasing AI governance obligations.

This project simulates that challenge by building a **fraud detection pipeline** from raw events to model-ready features.

---

## Why Synthetic Data?
Real banking data cannot be shared publicly.

Therefore:
- all datasets are **synthetically generated**,
- schemas resemble realistic transaction data,
- no personal identifiable information (PII) is used.

This allows safe experimentation while keeping the project **GDPR-friendly by design**.

---

## Pipeline Overview

High-level flow:

1. **Data Ingestion**
2. **Data Cleaning (`01_data_cleaning.ipynb`)**
3. **Feature Engineering (`02_feature_engineering.ipynb`)**
4. **Artefact Export**
5. **Train/Test Split**

---

## Key Design Principles
- Security-by-Design
- Privacy-by-Design
- Audit Readiness

---

## Target Audience
Recruiters, security-aware data science teams, and regulated industry environments.
