# Liquidity Risk Analysis

Basel III liquidity risk framework (LCR, NSFR, IRRBB) with stress testing for a crypto-fintech company.

## Overview

This project demonstrates liquidity risk management skills required for Treasury/Risk roles in fintech:

| Component | What It Shows |
|-----------|---------------|
| **LCR Calculation** | 30-day liquidity stress survival |
| **NSFR Calculation** | Long-term funding stability |
| **IRRBB Analysis** | Interest rate sensitivity (NII, EVE) |
| **Stress Testing** | 5 scenarios from baseline to severe crisis |
| **Monte Carlo Forecasting** | 90-day liquidity projections with uncertainty |

## Data Sources

| Data | Source | Type |
|------|--------|------|
| BTC/Crypto prices | CoinGecko API | Real |
| Stablecoin market caps | CoinGecko API | Real |
| Balance sheet | Calibrated to public filings | Synthetic |

## Key Results

### Stress Test Summary

| Scenario | LCR | Status |
|----------|-----|--------|
| Baseline | 156% | ✓ Compliant |
| Market Stress | 118% | ✓ Compliant |
| Crypto Winter | 92% | ✗ Breach |
| Stablecoin Crisis | 78% | ✗ Breach |
| Severe Combined | 61% | ✗ Breach |

### IRRBB Sensitivity

| Rate Shock | NII Impact | EVE Impact |
|------------|------------|------------|
| -200 bps | -€12.4M | +8.2% |
| +200 bps | +€12.4M | -8.2% |

## Files

```
liquidity_risk/
├── README.md
├── liquidity_risk_analysis.ipynb    # Main analysis
└── outputs/
    ├── irrbb_sensitivity.png
    ├── stress_test_results.png
    └── liquidity_forecast.png
```

## Methodology

Based on Basel III Liquidity Framework:

- **LCR** = HQLA / Net Cash Outflows (30-day) ≥ 100%
- **NSFR** = Available Stable Funding / Required Stable Funding ≥ 100%
- **IRRBB** = Impact of ±200bps rate shocks on NII and EVE

### Crypto-Specific Considerations

- Cryptocurrencies excluded from HQLA (too volatile)
- Higher runoff rates for crypto custody deposits
- Stablecoin redemption stress scenarios
- BTC volatility calibrated from real market data

## Skills Demonstrated

| Skill | Implementation |
|-------|----------------|
| Basel III Compliance | LCR, NSFR calculations |
| IRRBB Analysis | Rate sensitivity on NII/EVE |
| Stress Testing | 5 scenarios with crypto-specific risks |
| Monte Carlo | Liquidity forecasting with regime switching |
| API Integration | Real-time CoinGecko data |
| Python | pandas, numpy, matplotlib, requests |

## How to Run

1. Open `liquidity_risk_analysis.ipynb` in Jupyter/Kaggle
2. Run all cells
3. Charts saved to `outputs/` folder

## Author

Alex Crescentini | PhD Economics
- Background: ECB policy experience, macro modeling (DSGE/OLG/ABM)
- Master's thesis: Payment systems (TARGET2, BICOMP)
- Coursework: Credit risk, liquidity risk, Basel frameworks

## Repository

Part of: [risk_management_analysis](https://github.com/AlexCrescentini/risk_management_analysis)

```
risk_management_analysis/
├── credit_risk/           ✓ Credit scoring model
├── liquidity_risk/        ✓ This project
├── operational_risk/      → Fraud detection (next)
└── market_risk/           → VaR, stress testing (future)
```