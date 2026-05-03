# ML-Based Investment Model — NVIDIA Excess Return Prediction

**Author:** Kubra Banu

---

## Overview

This project compares **traditional asset pricing models** (CAPM, Fama-French Five-Factor) against **machine learning models** (XGBoost, Random Forest) in predicting NVIDIA's daily excess stock returns from 2015 to 2024.

The central research question: **Can ML models outperform classical financial models in explaining NVIDIA's excess returns?**

---

## Research Hypothesis

- **Null Hypothesis:** Traditional CAPM and Fama-French models perform equally well as advanced ML models in predicting NVIDIA's excess returns
- **Alternative Hypothesis (H₁):** ML-based models achieve better predictive performance than classical linear models

---

## Data Sources

| Source | Description |
|--------|-------------|
| **Yahoo Finance (yfinance)** | NVIDIA daily adjusted closing prices (Jan 2015 – Dec 2024) |
| **Kenneth R. French Data Library** | Fama-French Five-Factor daily returns (mkt_rf, smb, hml, rmw, cma) |

**Target variable:** `nvda_exret` — NVIDIA daily excess return (log return minus daily risk-free rate)

---

## Models Compared

| Model | Type | Test R² | Test MSE |
|-------|------|---------|---------|
| CAPM | Linear Regression | 0.3243 | 0.000681 |
| Fama-French Five-Factor | Linear Regression | 0.1651 | 0.000851 |
| CAPM + XGBoost | Gradient Boosting | 0.3290 | 0.000676 |
| CAPM + Random Forest | Ensemble | 0.3270 | 0.000678 |
| Fama-French + XGBoost | Gradient Boosting | 0.1506 | 0.000866 |
| Fama-French + Random Forest | Ensemble | 0.1362 | 0.000880 |

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Python** | Core analysis and modeling |
| **yfinance** | NVIDIA stock data retrieval |
| **pandas / numpy** | Data processing and preprocessing |
| **scikit-learn** | Random Forest, train/test split, metrics |
| **XGBoost** | Gradient boosting models |
| **matplotlib / seaborn** | EDA visualizations (correlation heatmap, pairplot, histograms) |

---

## Methodology

1. **Data Collection** — NVIDIA daily prices + Fama-French factor returns (2015–2024)
2. **Feature Engineering** — Daily log returns → excess returns (minus risk-free rate)
3. **EDA** — Summary statistics, return distribution, correlation heatmap, time series comparison
4. **Modeling** — 6 models trained on 80% / tested on 20% holdout
5. **Evaluation** — MSE, RMSE, R², Adjusted R² on test set
6. **Hypothesis Testing** — ML vs. linear model comparison

---

## Key Findings

- NVIDIA's beta (β = 1.74) confirms it is ~74% more volatile than the market
- CAPM alone explains ~40.5% of return variance (full sample), 32.4% on test set
- XGBoost with CAPM features marginally outperforms linear CAPM (R² 0.329 vs 0.324)
- Fama-French ML models underperformed — extra factors added noise rather than signal
- NVIDIA's returns driven primarily by market risk (MKT_prm correlation: 0.62)
- Negative correlations with HML (-0.30) and CMA (-0.37) consistent with a high-growth tech stock

---

## Files

| File | Description |
|------|-------------|
| `CAPM.ipynb` | CAPM linear regression + XGBoost + Random Forest (market factor only) |
| `Fama-French-model.ipynb` | Fama-French five-factor model + XGBoost + Random Forest |
| `ML-_Report-234-no-referances.docx` | Full project report |

---

## NVIDIA Key Stats (2015–2024)

- **Mean daily excess return:** -0.0039
- **Std deviation:** 0.0314
- **Beta (CAPM):** 1.7356
- **Alpha (CAPM):** 0.00197
- **Best model:** XGBoost (CAPM features) — Test R² = 0.3290
