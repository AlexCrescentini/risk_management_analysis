## Risk Management using Python

This repo uses Python to carry out a few projects and analysis across the main areas of risk management.

---

### Credit Risk

End-to-end credit risk framework using machine learning for probability of default (PD) modeling, model calibration, automated credit decisioning, and regulatory-compliant adverse action reporting.
   
[`credit_default_model.ipynb`](credit_risk/credit_default_model.ipynb) — Explored and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications). Built and compared Logistic Regression, KNN, Random Forest, and XGBoost classifiers. Evaluated with AUC-ROC, confusion matrices, and calibration curves. Applied Platt scaling for probability calibration.

[`loan_scoring_decisioning.ipynb`](credit_risk/loan_scoring_decisioning.ipynb) — Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands; generated SHAP-based adverse action notices for declined applicants explaining the key factors driving the decision (regulatory requirement under ECOA/FCRA).  


### Market Risk

*Coming soon*

### Liquidity Risk

Build and evaluate credit default prediction models using machine learning.
   
[`credit_default_model.ipynb`](credit_risk/credit_default_model.ipynb) — Explored and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications). Built and compared Logistic Regression, KNN, Random Forest, and XGBoost classifiers. Evaluated with AUC-ROC, confusion matrices, and calibration curves. Applied Platt scaling for probability calibration.

[`loan_scoring_decisioning.ipynb`](credit_risk/loan_scoring_decisioning.ipynb) — Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands; generated SHAP-based adverse action notices for declined applicants explaining the key factors driving the decision (regulatory requirement under ECOA/FCRA).  

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
│   └── loans_scoring_decision.ipynb
├── market_risk/
│   ├── data/ 
│   └── var_stress_testing.ipynb
├── liquidity_risk/
│   ├── data/ 
│   └── fraud_detection.ipynb
└── operational_risk/
    ├── data/
    └── fraud_detection.ipynb
```
