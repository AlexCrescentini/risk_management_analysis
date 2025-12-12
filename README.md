## Practical Applications of Financial Risk Management in Python

This repository shows selected practical applications in financial risk management using Python. To provide context on the regulatory environment, a brief overview of the **Basel III three-pillar framework** is available [here](./basel_III_framework.md).

The projects covered are:

- **[Probability of Default (PD) and Loan Decision](#pd_modeling)** — ML-based PD modeling, loan scoring, and regulatory-compliant reporting  
- **[Liquidity Risk](#liquidity-risk)** — Basel III ratios (LCR, NSFR), cash management, and stress testing  
- **[ICAAP: Interest Rate Risk in the Banking Book (IRRBB)](#icaap-interest-rate-risk-in-the-banking-book-irrbb)** — NII and EVE sensitivity analysis, behavioural NMD modelling, stress testing  
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
│   ├── output/
│   ├── 00_basel_III_yield_curve_shocks.ipynb
│   ├── 01_synthetic_balance_sheet.ipynb
│   ├── 02_irrbb_fundamentals.ipynb
│   ├── 03_irrbb_NMD_behav.ipynb
│   └── 04_irrbb_stress_test.ipynb
└── fraud_detection/
    ├── data/
    └── fraud_detection.ipynb
```

#### Python packages

`pandas`, `numpy`, `requests`, `duckdb`, `matplotlib`, `scipy`, `geopandas`, `plotly`

---
<a name="pd-modeling"></a>
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
IRRBB is the risk to a bank's economic value or net interest income from changes in interest rates in the banking book. It arises from maturity mismatches between assets and liabilities — for example, holding long-term fixed-rate mortgages funded by short-term deposits. Under **Basel III Pillar 2**, banks must assess IRRBB through the ICAAP process, measuring sensitivity from two perspectives: **NII** (earnings impact over 1 year) and **EVE** (present value impact on equity). This framework implements the full IRRBB analysis pipeline:

- [`00_basel_III_yield_curve_shocks.ipynb`](icaap_irrbb/00_basel_III_yield_curve_shocks.ipynb) — Generated the six standard Basel yield curve shock scenarios (parallel ±200bp, steepener, flattener, short rate ±300bp) from U.S. Treasury data. These scenarios form the basis for regulatory stress testing.
- [`01_synthetic_balance_sheet.ipynb`](icaap_irrbb/01_synthetic_balance_sheet.ipynb) — Created a synthetic bank balance sheet with realistic asset/liability structure: fixed and floating rate loans (mortgages, SME, corporate), non-maturity deposits (NMDs) by segment, term deposits, wholesale funding, and subordinated debt.
- [`02_irrbb_fundamentals.ipynb`](icaap_irrbb/02_irrbb_fundamentals.ipynb) — Implemented **contractual** NII and EVE calculations. NII computed over 1Y horizon with repricing logic for floating-rate instruments. EVE computed as PV(Assets) − PV(Liabilities) under all six scenarios. Includes Basel outlier test (15% of Tier 1 threshold).
- [`03_irrbb_NMD_behav.ipynb`](icaap_irrbb/03_irrbb_NMD_behav.ipynb) — Applied **behavioural modelling** to NMDs: core/non-core deposit split, deposit beta (pass-through rates), and effective maturity assignment. Showed how behavioural assumptions significantly reduce measured sensitivity compared to contractual treatment.
- [`04_irrbb_stress_test.ipynb`](icaap_irrbb/04_irrbb_stress_test.ipynb) — **Stress tested** behavioural assumptions by shocking core ratios, betas, and effective maturities. Compared contractual vs behavioural vs stressed results. Assessed outlier test under adverse conditions and discussed hedging/management actions.

---

### Operational Risk: Fraud Detection - ([`fraud_detection/`](fraud_detection/))
Operational risk is the risk of loss resulting from inadequate or failed internal processes, people, systems, or external events. This section will focus on fraud detection as a tangible application using machine learning.
