## Practical Applications of Financial Risk Management in Python

This repository shows few practical applications in financial risk management using Python. To provide context on the regulatory environment, a brief overview of the **Basel III three-pillar framework** is available [here](./basel_III_framework.md).

The main focus is on hands-on analytics:

- **Credit Risk** — PD modeling, loan scoring, and regulatory-compliant reporting  
- **Liquidity Risk** — Basel III ratios (LCR, NSFR), cash management, and stress testing  
- **Market Risk** — coming soon  
- **Operational Risk** — coming soon  

The repo bridges regulatory context with practical Python implementations for risk analysis.

#### Repository Structure

```
risk_management_analysis/
├── README.md
├── credit_risk/
│   ├── data/
│   ├── model_results/
│   ├── credit_default_model.ipynb
│   └── loan_scoring_and_decision.ipynb
├── market_risk/
│   ├── data/ 
│   └── var_stress_testing.ipynb
├── liquidity_risk/
│   ├── data/ 
│   └── lcr_nsfr_stress_testing.ipynb
└── operational_risk/
    ├── data/
    └── fraud_detection.ipynb
```

#### Python packages

`pandas`, `numpy`, `requests`, `duckdb`, `matplotlib`, `scipy`, `geopandas`, `plotly`

---

### Credit Risk
End-to-end credit risk framework using machine learning for probability of default (PD) modeling, model calibration, automated credit decisioning, and regulatory-compliant adverse action reporting.
   
- [`credit_default_model.ipynb`](credit_risk/credit_default_model.ipynb) — Explored and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications). Built and compared Logistic Regression, KNN, Random Forest, and XGBoost classifiers. Evaluated with AUC-ROC, confusion matrices, and calibration curves. Applied Platt scaling for probability calibration.
- [`loan_scoring_and_decision.ipynb`](credit_risk/loan_scoring_and_decision.ipynb) — Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands. Generated SHAP-based adverse action notices for declined applicants (ECOA/FCRA compliance).

> **Credit risk** is the risk of financial loss due to a borrower's failure to repay a loan or meet contractual obligations.

---
  
### Liquidity Risk
Analysis covering Basel III regulatory ratios (LCR and NSFR), daily cash management, cash forecasting, and stress testing:

- [`basel_III_metrics.ipynb`](liquidity_risk/basel_III_metrics.ipynb) — LCR and NSFR calculation following Basel III methodology. Stress scenarios including crypto-specific risks. Market data integration from CoinGecko API. **Basel III** introduced two complementary standards: the **Liquidity Coverage Ratio (LCR)** for 30-day stress resilience and the **Net Stable Funding Ratio (NSFR)** for one-year structural stability.
- [`liquidity_management.ipynb`](liquidity_risk/liquidity_management.ipynb) — Daily cash monitoring, Monte Carlo forecasting (90-day), operational buffers, and liquidity stress testing. Effective liquidity management requires daily cash monitoring, multi-horizon forecasting, stress testing, and contingency funding planning.

> **Liquidity risk** is the risk that an institution cannot meet payment obligations when due without incurring unacceptable losses.

---

### Market Risk
*Coming soon*

> **Market risk** is the risk of losses due to adverse movements in market prices and rates (interest rates, foreign exchange, equities, commodities).

---

### Operational Risk
*Coming soon*

> **Operational risk** is the risk of loss resulting from inadequate or failed internal processes, people, systems, or external events.
