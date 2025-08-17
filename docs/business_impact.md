# Business Impact and ROI Model – Secure AI Fraud Detection Pipeline

## 1. Executive Summary
This document defines a CFO-ready method to quantify costs, benefits, and risk for an AI-based fraud detection capability in EU banking. It combines external benchmarks (fraud rates, trends) with bank-specific inputs to compute ROI, TCO, and sensitivity to key assumptions. It also defines KPIs and an experiment design (champion–challenger) for evidence-based tuning.

## 2. Baseline and External Benchmarks
- **EU card fraud macro-rate:** Recent ECB/EBA reporting shows card fraud rates in the EEA on the order of ~0.015–0.03% of transactions by volume/value. Use this only to sanity-check internal baselines; always prioritise your bank’s own data.
- **UK losses context:** UK Finance reports ~£1.17bn in fraud losses (2023), with APP fraud a major component. Use such figures to frame strategic priority, not to substitute local baselines.
- **Trend factors:** Instant payments, social-engineering APP fraud, and data compromise continue to shape loss patterns across SEPA; operational responses must combine analytics, customer education, and coordinated risk ownership.

## 3. Cost and Benefit Components
### 3.1 Direct Loss Avoidance
- **Prevented fraud:** \(\Delta L = L_{baseline} - L_{post}\) where loss is measured net of recoveries/chargebacks.
- **Detection uplift:** Improvements in recall at a given precision reduce residual loss.

### 3.2 Operational Costs
- **Alert handling cost:** \(C_{ops} = N_{alerts} \times c_{case}\) (analyst time, tooling).
- **False positive cost:** Customer contact, case closure, chargeback handling.
- **Model lifecycle:** Data engineering, compute, monitoring, periodic retraining.

### 3.3 Customer Friction and Revenue Impact
- **Friction cost:** Additional authentication, delayed transactions, and abandonment rates (esp. SCA). Track conversion impact on exemptable flows.
- **Reputational benefit:** Incident reduction and regulator confidence; quantify where possible via avoided penalties and SLA credits.

## 4. KPI Definitions (Report Monthly and Quarterly)
| KPI | Definition | Target/Notes |
|---|---|---|
| Fraud Recall (Sensitivity) | True positives / All actual fraud | Maximise subject to precision |
| Precision (PPV) | True positives / All alerts | Manage analyst workload & CX |
| False Positive Rate | Non-fraud alerts / All alerts | Minimise; tie to case costs |
| Detection Latency | Time from event to flag | <= real-time for TRA-driven SCA |
| APP Fraud Loss | Monetary losses for APP scams | Track separately from card fraud |
| Alert Handling Cost per Case | Avg. operational cost per alert | Reduce via triage & tooling |
| SCA Exemption Accuracy | Correct exemption decisions / all exemptions | Align with PSD2 RTS and risk appetite |

## 5. ROI and TCO Formulas
Let:
- \(L_0\): baseline fraud loss (annual), \(L_1\): post-implementation loss  
- \(C_{ops}\): operational costs (analysts, systems)  
- \(C_{capex}\): setup costs (one-off)  
- \(C_{run}\): run costs (cloud/infra/monitoring)  

**Annual Benefit:** \(B = L_0 - L_1\)  
**Annual Net Impact:** \(NI = B - (C_{ops} + C_{run})\)  
**Payback Period (months):** \(PP = 12 \times \frac{C_{capex}}{B}\)  
**ROI (year 1):** \(ROI = \frac{B - (C_{ops} + C_{run}) - C_{capex}}{C_{capex}}\)

## 6. Example (Replace with Bank-Specific Inputs)
- Transactions/year: 250M  
- Baseline fraud loss rate (value): 0.025%  
- Average transaction value: €45  
- Estimated baseline loss: \(L_0 \approx 250{,}000{,}000 \times 45 \times 0.00025 = €2.81\,bn\) (illustrative; replace with actuals)  
- Target improvement: 25% reduction in residual losses via improved recall and better thresholds  
- Prevented fraud \(B\): €0.70bn (illustrative)  
- Costs: setup €2m, run €1.2m/year, ops cost €10 per alert at 300k alerts → €3.0m  
- Net impact Year 1: \(NI = 700m - 1.2m - 3.0m - 2.0m\) (replace with realistic numbers)

> Important: The example is a placeholder. Insert real bank inputs; use backtesting to compute \(L_0, L_1\).

## 7. Experiment Design (Champion–Challenger)
- **Holdout & A/B:** Split traffic by segment or time window; measure recall, precision, loss, and CX impact.
- **Threshold tuning:** Sweep decision thresholds to find Pareto-optimal points; fix targets (e.g., minimum precision) to constrain operational load.
- **Bias & fairness checks:** Verify performance across segments (device, geography); avoid discriminatory outcomes.
- **Governance:** Document changes; require sign-off by DPO/CISO for material changes.

## 8. Sensitivity and Scenario Analysis
- Vary: fraud base rates, average ticket sizes, alerting thresholds, analyst capacity, exemption policies.
- Compute tornado charts for NI/ROI to identify dominant levers.
- Create “stress scenarios” for spikes (e.g., data breach) and for new fraud patterns.

## 9. Dashboard and Reporting
- **Monthly dashboard:** KPIs in Section 4, trend lines, incident log summary, A/B outcomes.
- **Quarterly review:** ROI update, control effectiveness, retraining needs, regulator queries.
- **Board pack:** Executive summary; path-to-value; risk & compliance posture.

## 10. How to Use This Document
- Link this to `monitoring/` and to executive artefacts.
- Keep all assumptions versioned; capture actuals monthly.
- Iterate with Finance, Fraud Ops, and Compliance to ensure shared ownership.

