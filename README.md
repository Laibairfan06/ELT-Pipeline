# ELT-Pipeline
ELT pipeline for FinTech data: Crypto, UPI transactions, and stock time-series

This project implements a complete ELT (Extract, Load, Transform) pipeline for the Financial Technology (FinTech) domain.
The pipeline integrates multiple real-world datasets, cleans them, performs exploratory analysis, and stores processed data in CSV and JSON formats for further analysis or AI/ML applications.

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


## Data Sources & Details

1. **CoinGecko API (Crypto)**  
   - Top 10 cryptocurrencies by market capitalization  
   - Parameters: `vs_currency=usd`, `order=market_cap_desc`, `per_page=10`, `sparkline=False`  
   - Columns include: `id`, `symbol`, `name`, `current_price`, `market_cap`, `roi`, `total_volume`, etc.  

2. **Kaggle UPI Transactions Dataset**  
   - Monthly transaction volume and value by banks  
   - Columns: `UPI Banks`, `Volume (Mn)`, `Value (Cr)`, `Month`, `Year`  

3. **Finance Time-Series (Yahoo Finance / CSV)**  
   - Historical stock prices of leading FinTech companies: `PYPL`, `MA`, `V`  
   - Columns: `Date`, `PYPL`, `MA`, `V`  

## Data Cleaning & Transformation

- Missing numeric values filled with 0 (for crypto `max_supply`, `roi`)  
- Duplicates removed from all datasets  
- Date columns standardized for consistent analysis  
- Summary statistics generated for numeric columns  
- Processed data stored in **both CSV and JSON formats**

## How to Run

1. **Install required Python packages:**

pip install pandas requests matplotlib seaborn yfinance
Open the notebook notebooks/fintech_pipeline.ipynb.
### Run all notebook cells from top to bottom:

- Extract data from API and CSV files
- Clean and transform datasets
- Save cleaned datasets to `data/cleaned/`
- Generate exploratory visualizations
