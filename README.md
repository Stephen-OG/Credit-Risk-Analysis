# Retail Credit Risk – PD Modelling & Risk Appetite Decisioning

## Overview
This project demonstrates a **bank-grade retail credit risk workflow** using the **German Credit dataset (UCI)** as a proxy for real-world lending data. The objective is to estimate the **Probability of Default (PD)** for loan applicants and translate model outputs into **practical credit decisions** aligned with a defined **risk appetite**.

The work is designed to mirror how a Risk Analyst would approach credit decisioning in a large UK bank, focusing on **governance, interpretability, and business impact**, not just model accuracy.

---

## Business Problem
Retail banks must decide which customers to approve, manually review, or decline for credit products. These decisions must:
- Control expected credit losses
- Support sustainable growth
- Align with the bank’s risk appetite
- Be explainable and auditable

This project answers the question:
> *How can Probability of Default estimates be converted into robust lending decisions under a defined risk appetite?*

---

## Dataset
- **Source:** German Credit Data (UCI Machine Learning Repository)
- **Records:** 1,000 loan applicants
- **Features:** Application-time borrower characteristics (e.g. credit duration, credit amount, employment status, savings, housing)
- **Target:** Credit outcome
  - `1` = Good credit
  - `2` = Bad credit (default)

The dataset contains **origination-time variables only**, ensuring no data leakage from future repayment behaviour.

---

## Methodology
### 1. Target Definition
- Created a binary **default** flag where `1` represents a bad credit outcome.

### 2. Preprocessing
- Separated numerical and categorical features
- Imputed missing values using median (numerical) and most frequent (categorical)
- Applied one-hot encoding to categorical variables

### 3. Model Selection
- **Logistic Regression** used as the primary PD model
- Chosen for interpretability, stability, and regulatory acceptability

### 4. Model Evaluation
- ROC-AUC to assess discriminatory power
- Confusion matrix to understand error types
- Focus on **false negatives**, which represent approved customers who later default

### 5. Threshold Selection & Risk Appetite
- Avoided the default 0.5 classification threshold
- Selected a **PD threshold of 18%** for auto-approval based on portfolio risk outcomes
- Introduced a **REFER band (18%–28%)** for borderline applications
- Decisions:
  - **APPROVE:** PD < 0.18
  - **REFER:** 0.18 ≤ PD < 0.28
  - **DECLINE:** PD ≥ 0.28

This approach reflects real-world lending policy design.

---

## Project Structure
```
├── german_credit_risk.ipynb   # Main analysis notebook
├── german.data                # Raw UCI dataset
├── README.md                  # Project overview
└── report.pdf / report.md     # Written analysis and discussion
```

---

## Key Insights
- Model accuracy alone is insufficient for credit decisioning
- **Risk appetite** determines how model outputs are used in practice
- Thresholds convert probabilities into policy
- Introducing a manual review band improves both risk control and growth

---

## Limitations & Future Work
- Dataset size is limited compared to real banking portfolios
- Loss Given Default (LGD) and Exposure at Default (EAD) are not modelled
- Future extensions could include:
  - PD calibration and monitoring
  - Stress testing under economic downturns
  - Fairness and bias analysis

---

## How This Relates to Risk Analyst Roles
This project demonstrates:
- Risk-based thinking beyond machine learning metrics
- Understanding of credit policy and governance
- Ability to translate analytics into business decisions

---

## Author
**Stephen Ogundero**

MSc Data Science | Risk & Analytics Projects

