## Risk Management using Python

This repo uses Python to carry out a few projects and analysis across the main areas of risk management.

---

### Credit Risk

End-to-end credit risk framework using machine learning for probability of default (PD) modeling, model calibration, automated credit decisioning, and regulatory-compliant adverse action reporting.
   
- [`credit_default_model.ipynb`](credit_risk/credit_default_model.ipynb) — Explored and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications). Built and compared Logistic Regression, KNN, Random Forest, and XGBoost classifiers. Evaluated with AUC-ROC, confusion matrices, and calibration curves. Applied Platt scaling for probability calibration.

- [`loan_scoring_and_decision.ipynb`](credit_risk/loan_scoring_and_decision.ipynb) — Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands; generated SHAP-based adverse action notices for declined applicants explaining the key factors driving the decision (regulatory requirement under ECOA/FCRA).  

### Market Risk

*Coming soon*

### Liquidity Risk

Basel III liquidity risk framework for a crypto-fintech company, covering regulatory metrics (LCR, NSFR), interest rate risk analysis (IRRBB), stress testing, and cash flow forecasting.

- [`lcr_nsfr_stress_testing.ipynb`](liquidity_risk/lcr_nsfr_stress_testing.ipynb) — Built a synthetic balance sheet calibrated to public filings, calculated LCR and NSFR following Basel III methodology, performed IRRBB sensitivity analysis (±200bps shocks on NII and EVE), designed 5 stress scenarios including crypto-specific risks (stablecoin crisis, crypto winter), and ran Monte Carlo simulations for 90-day liquidity forecasting. Integrated real market data from CoinGecko API for calibration.

This project builds a liquidity risk framework for a crypto-fintech company following Basel III.

| Component | Description |
|-----------|-------------|
| **LCR** | Liquidity Coverage Ratio - 30-day survival |
| **NSFR** | Net Stable Funding Ratio - long-term stability |
| **IRRBB** | Interest Rate Risk in Banking Book |
| **Stress Testing** | Multiple scenarios including crypto risks |
| **Forecasting** | Monte Carlo simulation |

| Data | Source | Type |
|------|--------|------|
| Crypto prices | CoinGecko API | Real |
| Stablecoin data | CoinGecko API | Real |
| Balance sheet | Calibrated to public filings | Synthetic |

### Operational Risk

*Coming soon*

---

### Python packages

`pandas`, `numpy`, `requests`, `duckdb`, `matplotlib`, `scipy`, `geopandas`, `plotly`

---

### Repository Structure

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
