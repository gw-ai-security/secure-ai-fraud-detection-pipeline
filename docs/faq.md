# FAQ - Secure AI Fraud Detection Pipeline

## 1. What types of fraud can this AI system detect?
AI-driven fraud detection can uncover a wide range of threats, including account takeover (ATO), Authorized Push Payment (APP) fraud, synthetic identity fraud, credential stuffing, CNP (card-not-present) fraud, insider threats, and social engineering-based schemes by spotting anomalies in transaction patterns and user behavior.

## 2. How does the model adapt to new and emerging fraud patterns?
By incorporating continuous learning and feedback loops from confirmed fraud cases, AI models adapt to evolving threats in near real time. This adaptability enables the model to detect emerging fraud trends before rigid rule systems would.

## 3. Can small banks implement AI-powered fraud detection?
Yes. AI is increasingly accessible to smaller financial institutions via scalable cloud-based services, open-source libraries, or managed platforms. Fraud detection using ML and AI can be modularly scaled based on transaction volumes and institutional needs.

## 4. How does this project comply with GDPR and PSD2?
- GDPR: Privacy-by-Design (Art. 25), data minimization, pseudonymization, audit logs (Art. 30), and DPIA-like threat modeling (Art. 35) are integrated.
- PSD2 RTS: The risk engine architecture supports real-time transaction monitoring, SCA exemption justification, and auditability, aligned with PSD2 regulatory standards.

## 5. Why prefer AI over rule-based systems for fraud detection?
Unlike static rule-based systems, AI can detect subtle, complex fraud signals across vast datasets, reduce false positives by understanding context, and adapt to new fraud vectors dynamically.

## 6. How do we maintain explainability and trust in AI decisions?
We use Explainable AI techniques such as SHAP to maintain transparency. Decisions are audit-traceable, and high-risk decisions can be subject to human-in-the-loop review.

## 7. How do we mitigate AI risks like model drift or adversarial attacks?
- Model drift: Detected via monitoring pipelines; triggers retraining or threshold recalibration.
- Adversarial resilience: We include adversarial testing (e.g., FGSM perturbations), input validation, and fail-safe mechanisms for anomalous input.

## 8. What is Risk-Based Authentication and its role in SCA?
Risk-Based Authentication (RBA) dynamically adjusts authentication requirements based on transaction context; if low-risk, the system may waive strict SCA requirements, improving user experience while maintaining security.

## 9. What are the main challenges in deploying such a system?
- Ensuring data quality and governance under regulatory frameworks (GDPR, PSD2).
- Addressing legacy tech integration in banking environments.
- Minimizing false positives to avoid customer friction without sacrificing security.

## 10. How do we ensure long-term governance and audit readiness?
- Establish an AI governance structure, including periodic audits, AI ethics oversight, training, and documentation.
- Leverage frameworks such as NIST AI Risk Management to map, measure, and manage risks.
