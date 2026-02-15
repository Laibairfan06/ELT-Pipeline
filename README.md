# ELT-Pipeline
ELT pipeline for FinTech data: Crypto, UPI transactions, and stock time-series

This project implements a complete ELT (Extract, Load, Transform) pipeline for the Financial Technology (FinTech) domain.
The pipeline integrates multiple real-world datasets, cleans them, performs exploratory analysis, and stores processed data in CSV and JSON formats.

## Thematic Domain
**Financial Technology (FinTech)**:
- Crypto prices (CoinGecko API)
- UPI transaction volumes (Kaggle dataset)
- Finance stock time-series (Yahoo Finance / CSV)

## ELT Pipeline Steps

1. **Extract**
   - Fetch top 10 cryptocurrencies from CoinGecko API
   - Load UPI transaction CSV dataset
   - Load Finance stock price CSV dataset

2. **Load**
   - Load datasets into Pandas DataFrames
   - Store raw/processed data in `data/raw/` or `data/processed/`

3. **Transform & Clean**
   - Handle missing values (numeric columns filled with 0)
   - Remove duplicate rows
   - Standardize date columns (`datetime`)
   - Generate summary statistics

4. **Save Cleaned Data**
   - Save datasets in **CSV** (human-readable) and **JSON** (semi-structured)
   - Saved in `data/cleaned/`



## Data Sources and Assumptions

1. **Cryptocurrency Data (API)**
   - Source: https://www.coingecko.com/en/api
   - Data includes current prices, market capitalization, volume, supply, ROI, and other metrics for the top 10 cryptocurrencies.
   - **Assumptions:** Missing values in `max_supply` and `roi` are filled with 0. Only the top 10 coins are considered for analysis to focus on the most impactful assets.

2. **UPI Transactions (Public Dataset)**
   - Source: Kaggle dataset `fintech_transaction.csv`
   - Data includes monthly transaction volume and value by banks.
   - **Assumptions:** Month and Year columns are combined into a single datetime column. There are no missing values, so no imputation was required.

3. **Stock Prices (Time-Series)**
   - Source: Yahoo Finance via `yfinance` Python library
   - Data includes daily closing prices for Visa, MasterCard, and PayPal from 2021–2026.
   - **Assumptions:** Missing trading days are ignored. Prices are used directly without smoothing.

## Data Cleaning & Transformation

- Missing numeric values filled with 0 (for crypto `max_supply`, `roi`)  
- Duplicates removed from all datasets  
- Date columns standardized for consistent analysis  
- Summary statistics generated for numeric columns  
- Cleaned data stored in **both CSV and JSON formats**

## How to Run

1. **Install required Python packages:**

pip install pandas requests matplotlib seaborn yfinance
Open the notebook notebooks/fintech_pipeline.ipynb.
### Run all notebook cells from top to bottom:

- Extract data from API and CSV files
- Clean and transform datasets
- Save cleaned datasets to `data/cleaned/`
- Generate exploratory visualizations
