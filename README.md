## Practical Applications of Financial Risk Management in Python

This repository shows selected practical applications in financial risk management using Python. To provide context on the regulatory environment, a brief overview of the **Basel III three-pillar framework** is available [here](./basel_III_framework.md).

The projects covered are:

- **[Probability of Default (PD) and Loan Decision](#probability-of-default-pd-modeling-and-loan-decision)** — ML-based PD modeling, loan scoring, and regulatory-compliant reporting  
- **[Liquidity Risk](#liquidity-risk)** — Basel III ratios (LCR, NSFR), cash management, and stress testing  
- **[ICAAP: Interest Rate Risk in the Banking Book (IRRBB)](#icaap-interest-rate-risk-in-the-banking-book-irrbb)** — EVE and NII sensitivity analysis, Pillar 2 capital assessment  
- **[Operational Risk: Fraud Detection](#operational-risk-fraud-detection)** — ML-based fraud detection and operational risk monitoring

#### Repository Structure

```
risk_management_analysis/
├── README.md
├── pd_modeling/
│   ├── data/
│   ├── model_results/
│   ├── credit_default_model.ipynb
│   └── loan_scoring_and_decision.ipynb
├── liquidity_risk/
│   ├── data/
│   ├── results/
│   ├── basel_III_metrics.ipynb
│   └── liquidity_management.ipynb
├── icaap_irrbb/
│   ├── data/ 
│   └── var_stress_testing.ipynb
└── fraud_detection/
    ├── data/
    └── fraud_detection.ipynb
```

#### Python packages

`pandas`, `numpy`, `requests`, `duckdb`, `matplotlib`, `scipy`, `geopandas`, `plotly`

---

### Probability of Default (PD) Modeling and Loan Decision - ([`pd_modeling/`](pd_modeling/))
PD is a central element in credit risk management and forms a key basis for Basel III Pillar 1 capital requirements. Here we focus on using machine learning for probability of default (PD) modeling, model calibration, automated credit decisioning, and regulatory-compliant adverse action reporting.
   
- [`credit_default_model.ipynb`](pd_modeling/credit_default_model.ipynb) — Explored and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications). Built and compared Logistic Regression, KNN, Random Forest, and XGBoost classifiers. Evaluated with AUC-ROC, confusion matrices, and calibration curves. Applied Platt scaling for probability calibration.
- [`loan_scoring_and_decision.ipynb`](pd_modeling/loan_scoring_and_decision.ipynb) — Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands. Generated SHAP-based adverse action notices for declined applicants (ECOA/FCRA compliance).

---

### Liquidity Risk - ([`liquidity_risk/`](liquidity_risk/))
Analysis covering Basel III - pillar 1 regulatory ratios (LCR and NSFR), daily cash management, cash forecasting, and stress testing:

- [`basel_III_metrics.ipynb`](liquidity_risk/basel_III_metrics.ipynb) — LCR and NSFR calculation following Basel III methodology. Stress scenarios including crypto-specific risks. Market data integration from CoinGecko API. **Basel III** introduced two complementary standards: the **Liquidity Coverage Ratio (LCR)** for 30-day stress resilience and the **Net Stable Funding Ratio (NSFR)** for one-year structural stability.
- [`liquidity_management.ipynb`](liquidity_risk/liquidity_management.ipynb) — Daily cash monitoring, Monte Carlo forecasting (90-day), operational buffers, and liquidity stress testing. Effective liquidity management requires daily cash monitoring, multi-horizon forecasting, stress testing, and contingency funding planning.

---

### ICAAP: Interest Rate Risk in the Banking Book (IRRBB) - ([`icaap_irrbb/`](icaap_irrbb/))
IRRBB is the risk to a bank’s economic value or net interest income from changes in interest rates in the banking book. It is primarily assessed under Basel III Pillar 2 (ICAAP).

---

### Operational Risk: Fraud Detection - ([`fraud_detection/`](fraud_detection/))
Operational risk is the risk of loss resulting from inadequate or failed internal processes, people, systems, or external events. This section will focus on fraud detection as a tangible application using machine learning.
