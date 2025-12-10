## Risk Management using Python

This repo uses Python to carry out few analysis across the main areas of risk management.

---

### Credit Risk
End-to-end credit risk framework using machine learning for probability of default (PD) modeling, model calibration, automated credit decisioning, and regulatory-compliant adverse action reporting.
   
- [`credit_default_model.ipynb`](credit_risk/credit_default_model.ipynb) — Explored and preprocessed the Kaggle "Give Me Some Credit" dataset (150K loan applications). Built and compared Logistic Regression, KNN, Random Forest, and XGBoost classifiers. Evaluated with AUC-ROC, confusion matrices, and calibration curves. Applied Platt scaling for probability calibration.
- [`loan_scoring_and_decision.ipynb`](credit_risk/loan_scoring_and_decision.ipynb) — Deployed the best model (XGBoost, AUC=0.87) to score new loan applications and automate approve/decline decisions based on risk bands. Generated SHAP-based adverse action notices for declined applicants (ECOA/FCRA compliance).

> **Credit risk** is the risk of financial loss due to a borrower's failure to repay a loan or meet contractual obligations.
  
### Liquidity Risk
Analysis covering Basel III regulatory ratios (LCR and NSFR), daily cash management, cash forecasting, and stress testing:

- [`basel_III_metrics.ipynb`](liquidity_risk/basel_III_metrics.ipynb) — LCR and NSFR calculation following Basel III methodology. Stress scenarios including crypto-specific risks. Market data integration from CoinGecko API. **Basel III** introduced two complementary standards: the **Liquidity Coverage Ratio (LCR)** for 30-day stress resilience and the **Net Stable Funding Ratio (NSFR)** for one-year structural stability.
- [`liquidity_management.ipynb`](liquidity_risk/liquidity_management.ipynb) — Daily cash monitoring, Monte Carlo forecasting (90-day), operational buffers, and liquidity stress testing. Effective liquidity management requires daily cash monitoring, multi-horizon forecasting, stress testing, and contingency funding planning.

> **Liquidity risk** is the risk that an institution cannot meet payment obligations when due without incurring unacceptable losses.

### Market Risk
*Coming soon*

> **Market risk** is the risk of losses due to adverse movements in market prices and rates (interest rates, foreign exchange, equities, commodities).

### Operational Risk
*Coming soon*

> **Operational risk** is the risk of loss resulting from inadequate or failed internal processes, people, systems, or external events.

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

# Basel III — 3 Pillar Framework

Basel III is implemented in the EU through CRR (Capital Requirements Regulation) and CRD IV/V (Capital Requirements Directive). The framework uses three pillars: minimum requirements, supervisory review, and market discipline.

---

## Pillar 1: Minimum Requirements

Quantitative, formula-based requirements that all institutions under the regulation (CRR Article 4) must meet. The risks involved here are credit risk, market risk, operational risk (for capital), and liquidity risk. They are divided in:

### 1. Capital Requirements

Capital ratios are expressed as a percentage of Risk-Weighted Assets (RWA). RWA translates exposures into a risk-adjusted measure, ensuring capital requirements are proportionate to actual risk.

| Requirement | Details |
|-------------|---------|
| **Minimum Ratios** | CET1 ≥ 4.5% \| Tier 1 ≥ 6% \| Total Capital ≥ 8% — all as % of RWA |
| **Capital Conservation Buffer** | 2.5% CET1 — mandatory for all banks |
| **Countercyclical Buffer** | 0–2.5% CET1 — set by national authorities based on credit cycle |
| **Systemic Buffers** | G-SII (0–3.5%) and O-SII (0–3%) for systemically important institutions |
| **Leverage Ratio** | Tier 1 / Total Exposure ≥ 3% — non-risk-based backstop |

--> **Risk-Weighted Assets (RWA) Calculation**

Total RWA = Credit Risk RWA + Market Risk RWA + Operational Risk RWA

| Risk Type | Approaches | Key Inputs |
|-----------|------------|------------|
| Credit Risk | Standardised (SA) or Internal Ratings-Based (F-IRB, A-IRB) | PD, LGD, EAD, M; risk weights by exposure class |
| Market Risk | Standardised (SA) or Internal Models (IMA) — FRTB | Sensitivities, VaR, ES, default risk charge |
| Operational Risk | Standardised Approach (Basel III final) | Business Indicator (BI), Internal Loss Multiplier |

Banks must calculate RWA using approved approaches (SA or internal models with supervisory approval).

### 2. Liquidity Requirements

| Ratio | Details |
|-------|---------|
| **LCR** | Liquidity Coverage Ratio ≥ 100% — HQLA must cover 30-day net outflows under stress |
| **NSFR** | Net Stable Funding Ratio ≥ 100% — available stable funding must cover required stable funding over 1 year |

---

## Pillar 2: Supervisory Review

Qualitative and quantitative assessment of risks not fully captured by Pillar 1. Subject institutions perform an internal assessment; the supervisor reviews and may set additional requirements.

### The Process Chain

| Process | Owner | Purpose |
|---------|-------|---------|
| **ICAAP** | Bank (internal) | Internal Capital Adequacy Assessment — identify all material risks, quantify capital needs above Pillar 1 |
| **ILAAP** | Bank (internal) | Internal Liquidity Adequacy Assessment — assess liquidity risks beyond LCR/NSFR |
| **SREP** | Supervisor | Supervisory Review and Evaluation — assess business model, governance, capital and liquidity adequacy |
| **P2R** | Supervisor → Bank | Pillar 2 Requirement — binding additional capital based on SREP findings |
| **P2G** | Supervisor → Bank | Pillar 2 Guidance — expected buffer above P2R (not legally binding) |

### 1. Capital Adequacy (ICAAP)

| Risk | What It Covers |
|------|----------------|
| **IRRBB** | Interest Rate Risk in Banking Book — EVE and NII sensitivity to rate shocks; NMD behavioral modeling |
| **CSRBB** | Credit Spread Risk in Banking Book — value sensitivity to credit spread movements |
| **Concentration Risk** | Single-name, sectoral, geographic concentrations not fully captured in Pillar 1 |
| **Residual Credit/Op Risk** | Model risk, migration risk, conduct risk, IT/cyber risk, legal risk |
| **Strategic / Business Risk** | Earnings volatility, business model sustainability |

### 2. Liquidity Adequacy (ILAAP)

| Risk | What It Covers |
|------|----------------|
| **Funding Concentration** | Over-reliance on single counterparties, funding sources, currencies, maturities |
| **Intraday Liquidity** | Payment and settlement timing risk within the day |
| **Contingent Liabilities** | Off-balance sheet commitments that could crystallize under stress |
| **Asset Encumbrance** | Pledged assets reducing available liquidity buffer |
| **FX Liquidity** | Currency mismatch — ability to meet obligations in each significant currency |

--> **The Complete Capital Stack**

| Layer | Typical Range |
|-------|---------------|
| *P2G (guidance — not binding)* | ~1–3% |
| **P2R (binding)** | ~1–4% |
| **Countercyclical Buffer** | 0–2.5% |
| **Systemic Buffers (G-SII / O-SII)** | 0–3.5% |
| **Capital Conservation Buffer** | 2.5% |
| **Pillar 1 Minimum** | 8% (CET1 4.5% + AT1 1.5% + T2 2%) |

*Typical EU bank: 12–18% total capital requirement depending on risk profile.*

---

## Pillar 3: Market Discipline

Public disclosure requirements enabling market participants to assess bank risk profiles. Creates external discipline through transparency.

### Disclosure Requirements

| Disclosure Area | Content |
|-----------------|---------|
| **Capital** | Composition of capital, capital ratios, leverage ratio, reconciliation to accounting |
| **Risk Exposures** | Credit risk exposures by portfolio, geography, maturity; market risk; operational risk |
| **RWA** | RWA by risk type, approach used (SA/IRB/IMA), RWA flow statements |
| **Liquidity** | LCR and NSFR ratios, HQLA composition, funding profile |
| **IRRBB** | EVE and NII sensitivities, key assumptions (especially NMD treatment) |
| **Risk Management** | Governance, risk appetite, policies and processes for each risk type |
| **Remuneration** | Remuneration policies, pay outcomes for material risk takers |

### Disclosure Frequency

| Frequency | Content |
|-----------|---------|
| **Annual** | Full Pillar 3 report — all templates and qualitative disclosures |
| **Semi-Annual** | Key metrics and selected quantitative templates |
| **Quarterly** | Capital ratios, leverage ratio, LCR (large/listed institutions) |

*Format: Standardised templates under CRR Part Eight and EBA ITS. Must be published on the institution's website.*

---

## Regulatory Compliance

All credit institutions authorised under CRD are subject to Pillar 1 requirements. Compliance is mandatory and continuous — requirements must be met at all times, not just at reporting dates. Internal systems must monitor ratios daily/weekly; formal reporting is periodic.

| Requirement | Must Be Met | Reporting Frequency |
|-------------|-------------|---------------------|
| Capital Ratios | Continuously | Quarterly (COREP templates) |
| LCR | Continuously | Monthly (large banks) / Quarterly (others) |
| NSFR | Continuously | Quarterly |
| Leverage Ratio | Continuously | Quarterly |
| Large Exposures | Continuously | Quarterly |

*Note: COREP (Common Reporting) is the standardised EU reporting framework covering own funds, capital ratios, RWA by risk type, large exposures, leverage, and liquidity.*
