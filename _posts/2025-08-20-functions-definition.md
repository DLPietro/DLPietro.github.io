---
title: "📖 Day 2 – Functions & Financial Calculations"
date: 2025-08-20 19:12:48 +0200
categories: [python, roadmap, data]
---

# Intro

Practising, making mistakes and correcting them during these first days, I was focused on building reusable functions in Python, and calculating financial metrics using functions.

# Main Goals:

- Definition and call of simple functions
- Metrics (Volatility and Daily returns) calculation (manually)
- Structure code with a more readable logic

# Step by Step
📍 Step 1: Defined a calc_daily_returns() function.
📍 Step 2: Added calc_annualized_return() and volatility calculations.
📍 Step 3: Tested functions with multiple tickers (in our case, I used a sample of 3 assets).

# Challenges / Insights

- Mixed up local vs global variables inside functions.
- Made a comparison between .sum() vs .mean() for metric analysis.
- First approach with pandas.Series modules.

# Code Snippet Final

<pre>
```python
def calc_daily_returns(prices):
    return prices.pct_change().dropna()

def analyse_returns(daily_returns):
    avg = daily_returns.mean()
    vol = daily_returns.std()
    return {
        "Annualized Return": (1+avg)**252 - 1,
        "Annualized Volatility": vol*np.sqrt(252)
    }
```
</pre>

# Next Step
👉 Work with pandas.DataFrame directly, instead of raw lists, for a faster and more accurate job.

# You'll find my projects here:
- 🔗 [GitHub Repository](https://github.com/DLPietro/learning-roadmap)
- 📊 [Google Colab](https://colab.research.google.com/github/DLPietro/learning-roadmap/blob/main/notebooks/day_2.ipynb)
