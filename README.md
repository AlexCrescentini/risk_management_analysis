## Risk Management using Python

This repo uses Python to carry out a few projects and analysis across the main areas of risk management. The topics covered are the following:

1. **Credit Risk** ([`credit_risk/`](credit_risk))

   Build and evaluate credit default prediction models using machine learning.
   
   **What I did:**
   
   - Explored, cleaned, and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications); built and compared multiple classification models (Logistic Regression, KNN, Random Forest, XGBoost) to predict default probability; evaluated model performance using AUC-ROC, confusion matrix, and calibration curves; applied Platt scaling to calibrate predicted probabilities.  
     → [`credit_default_model.ipynb`](credit_risk/credit_default_model.ipynb)
   
   - Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands; generated SHAP-based adverse action notices for declined applicants explaining the key factors driving the decision (regulatory requirement under ECOA/FCRA).  
     → [`loan_scoring_decisioning.ipynb`](credit_risk/loan_scoring_decisioning.ipynb)

#### 2. Liquidity Risk ([`liquidity_risk/`](liquidity_risk))

*Coming soon*

#### 3. Operational Risk ([`operational_risk/`](operational_risk))

*Coming soon*

#### 4. Market Risk ([`market_risk/`](market_risk))

*Coming soon*

---

**Python packages:** `pandas`, `numpy`, `requests`, `duckdb`, `matplotlib`, `scipy`, `geopandas`, `plotly`

---

#### Repository Structure

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
