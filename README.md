import pandas as pd
import numpy as np

# 1. Financial Data Construction (Saudi Petrochemical Sector - SAR Millions)
data = {
    'Year': [2021, 2022, 2023, 2024, 2025],
    'SABIC_Revenue': [174880, 198400, 141000, 152000, 161000],
    'SABIC_Net_Income': [23000, 16500, -2770, 4200, 7800],
    'SABIC_Total_Assets': [318000, 312000, 305000, 310000, 315000],
    'SABIC_Total_Equity': [180000, 185000, 178000, 181000, 186000],
    
    'TASNEE_Revenue': [8600, 9800, 8100, 8900, 9400],
    'TASNEE_Net_Income': [1350, 790, 180, 450, 620],
    'TASNEE_Total_Assets': [24500, 23800, 22900, 23400, 24000],
    'TASNEE_Total_Equity': [10200, 10800, 10500, 10900, 11300]
}

df = pd.DataFrame(data)

# 2. Financial Ratios Calculation
# SABIC Metrics
df['SABIC_Net_Margin_%'] = (df['SABIC_Net_Income'] / df['SABIC_Revenue']) * 100
df['SABIC_ROA_%'] = (df['SABIC_Net_Income'] / df['SABIC_Total_Assets']) * 100
df['SABIC_ROE_%'] = (df['SABIC_Net_Income'] / df['SABIC_Total_Equity']) * 100

# TASNEE Metrics
df['TASNEE_Net_Margin_%'] = (df['TASNEE_Net_Income'] / df['TASNEE_Revenue']) * 100
df['TASNEE_ROA_%'] = (df['TASNEE_Net_Income'] / df['TASNEE_Total_Assets']) * 100
df['TASNEE_ROE_%'] = (df['TASNEE_Net_Income'] / df['TASNEE_Total_Equity']) * 100

# 3. Sector Valuation Multiples Comparison (Current Market Estimates)
valuation_data = {
    'Company': ['SABIC', 'TASNEE', 'Sector Average'],
    'Ticker': ['2010.SR', '2060.SR', 'Petrochem Sector'],
    'P/E_Ratio': [18.5, 15.2, 17.1],
    'P/B_Ratio': [1.35, 0.95, 1.20],
    'EV/EBITDA': [8.4, 7.1, 7.8],
    'Dividend_Yield_%': [4.2, 3.1, 3.8]
}

df_valuation = pd.DataFrame(valuation_data)

# 4. Display Results
print("=== 1. SABIC vs TASNEE Historical Profitability Metrics ===")
print(df[['Year', 'SABIC_Net_Margin_%', 'SABIC_ROE_%', 'TASNEE_Net_Margin_%', 'TASNEE_ROE_%']].round(2))

print("\n=== 2. Saudi Petrochemical Valuation Benchmark ===")
print(df_valuation)
