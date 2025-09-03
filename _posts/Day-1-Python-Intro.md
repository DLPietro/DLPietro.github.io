---
title: "📖 Day 1 – Python Intro & First Steps with Financial Data"
date: 2025-07-15 10:00:00 +0200
---

In my Master’s thesis, I analyzed 10 years of data from the S&P 500, IVV, and Fidelity Contrafund using R and GARCH models.

Key findings:
- The ETF matched the S&P 500 with lower fees
- Active management outperformed in bull markets but lagged in corrections

🔗 [Code on GitHub](https://github.com/DLPietro/thesis-analysis)📖 Day 1 – Python Intro & First Steps with Financial Data

Intro
Today I started my journey into Python for Finance. The first step was to familiarize myself with the language basics and apply them immediately on financial datasets.

Main Goals

Understand Python functions and lists

Download financial data with yfinance

Calculate daily and annualized returns

Step by Step
📍 Step 1: Installed and imported yfinance and pandas.
📍 Step 2: Downloaded 60 days of Apple, Microsoft, and Google data.
📍 Step 3: Wrote a function to calculate daily returns and annualized returns.

Challenges / Insights

Handling errors when looping through lists (indexing issues).

Realized the importance of .pct_change() instead of manually coding formulas.

First exposure to the difference between return and print.

Code Snippet Final
