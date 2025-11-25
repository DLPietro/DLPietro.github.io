---
layout: post
title: "📖 Day 1 – Intro"
date: 2025-08-14 18:45:26 +0200
categories: roadmap
tags: [python, roadmap, analytics]
---

# First Steps with Financial Data with Python

Today I started my journey into Python for Finance. The first step was to familiarize myself with the language basics and apply them immediately on financial datasets.

# Main Goals:

- First approach with python basics and standard
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

<pre>
```python
import yfinance as yf, pandas as pd

data = yf.download(['AAPL','MSFT','GOOGL'], period='60d')
close = data['Close']

returns = close.pct_change().dropna()
annualized_return = (1 + returns.mean())**252 - 1
```
</pre>

# Next Step
👉 Apply daily returns logic to more assets and explore volatility.

# Here are the project links below:
- 🔗 [GitHub Repository](https://github.com/DLPietro/learning-roadmap)
- 📊 [Google Colab](https://colab.research.google.com/github/DLPietro/learning-roadmap/blob/main/day_1.ipynb)
