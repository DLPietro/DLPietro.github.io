---
layout: post
title: "📖 Day 4 – Pandas Basics"
date: 2025-08-27 10:51:26 +0200
categories: roadmap
tags: [python, roadmap, analytics]
---

# Series & DataFrame

This exercise was about moving from Python lists to Pandas Series and DataFrames: using this library, the work will be easier and more focused on financial analysis.

# Main Goals:

- Create DataFrames with financial data
- Use .pct_change() to calculate returns directly
- Add new columns to the DataFrame 

# Step by Step
📍 Step 1: Downloaded 3 tickers (IWM, GLD, IGOV), to start practising with matrices.

📍 Step 2: Selected closing prices and volume into separate DataFrames, and working with them.

📍 Step 3: Defined a function to calculate daily returns with .pct_change().

# Challenges / Insights

- Learned the difference between Series and DataFrames.
- Realized how powerful pandas indexing is for selecting specific tickers.
- .head() and .tail() are great for checking results quickly; you can select the number of row to be viewed.

# Code Snippet

<pre>
```python
data = yf.download(['IWM','GLD','IGOV'], period='60d')
close = data['Close']
volume = data['Volume']

returns = close.pct_change().dropna()
```
</pre>

# Next Step
👉 Data Visualization: shouwing moving averages and volatility.

# You'll find my projects here:
- 🔗 [GitHub Repository](https://github.com/DLPietro/learning-roadmap)
- 📊 [Google Colab](https://colab.research.google.com/github/DLPietro/learning-roadmap/blob/main/notebooks/day_4.ipynb)
