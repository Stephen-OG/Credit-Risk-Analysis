# Credit-Risk-Analysis
Predict loan default risk at origination (PD model) using LendingClub data as a proxy for retail lending.
### Approach:
Created binary default label from loan_status (Fully Paid vs Charged Off/Default/Late).
Removed post-origination leakage fields (repayment/collections).
Built interpretable Logistic Regression baseline + compared tree model.
Evaluated AUC, precision/recall, confusion matrix, and PD calibration.
Implemented decisioning thresholds: Approve/Refer/Decline.
### Governance:
Interpretability prioritized for audit/regulatory defensibility.
Thresholds chosen based on risk appetite trade-offs.
Monitoring plan: AUC + calibration drift + data drift.
