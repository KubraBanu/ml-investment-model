# Environment Setup Guide

## Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

## Setup

### 1. Clone the repository
git clone https://github.com/KubraBanu/ml-investment-model.git
cd ml-investment-model

### 2. Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

### 3. Install dependencies
pip install -r requirements.txt

## Data Sources
Data is fetched automatically via APIs — no manual download needed:
- **NVIDIA stock prices**: Yahoo Finance API (via `yfinance`)
- **Fama-French factors**: Kenneth R. French Data Library (downloaded automatically in notebook)

## Running the Analysis

### CAPM Model
1. Open `CAPM.ipynb` in Jupyter Notebook
2. Run all cells sequentially
3. Outputs: CAPM regression results, XGBoost model, Random Forest model, R² comparison

### Fama-French Model
1. Open `Fama-French-model.ipynb` in Jupyter Notebook
2. Run all cells sequentially
3. Outputs: Five-factor model results, ML model comparison

## Key Results
- NVIDIA Beta (CAPM): 1.7356 — ~74% more volatile than the market
- Best model: XGBoost (CAPM features) — Test R² = 0.3290
- Analysis period: January 2015 – December 2024
