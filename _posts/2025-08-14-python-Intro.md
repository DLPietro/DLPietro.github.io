---
title: "📖 Day 1 – Python Intro & First Steps with Financial Data"
date: 2025-08-14 18:45:26 +0200
---

# 📖 Day 1 – Python Intro & First Steps with Financial Data

Today I started my journey into Python for Finance. The first step was to familiarize myself with the language basics and apply them immediately on financial datasets.

# Main Goals:

- Understand Python functions and lists
- Download financial data with yfinance
- Calculate daily and annualized returns

# Step by Step
📍 Step 1: Installed and imported yfinance and pandas.
📍 Step 2: Downloaded 60 days of Apple, Microsoft, and Google data.
📍 Step 3: Wrote a function to calculate daily returns and annualized returns.

# Challenges / Insights

- Handling errors when looping through lists (indexing issues).
- Realized the importance of .pct_change() instead of manually coding formulas.
- First exposure to the difference between return and print.

# Code Snippet Final

import yfinance as yf, pandas as pd

data = yf.download(['AAPL','MSFT','GOOGL'], period='60d')
close = data['Close']

returns = close.pct_change().dropna()
annualized_return = (1 + returns.mean())**252 - 1

# Next Step
👉 Apply daily returns logic to more assets and explore volatility.

Here are the notes and the script: https://github.com/DLPietro/learning-roadmap/blob/main/notebooks/day_1.ipynb
