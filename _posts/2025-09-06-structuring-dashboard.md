---
layout: post
title: "📖 Day 8 – Structuring the Dashboard"
date: 2025-09-06 23:54:24 +0200
categories: roadmap
tags: [python, roadmap, analytics]
---

# Intro

On Day 8, I started structuring the foundation for my Market Analysis Dashboard.
The focus was on creating reusable functions to download and clean financial time series, ensuring that missing values are handled correctly before moving into deeper analysis.

# Main Goals:

- Download and clean financial data from Yahoo Finance using a function.
- Handle missing values (ffill, bfill, dropna).
- Prepare a clean and flexible dataset for further analysis, changing dates and methods to handle missing values.

# Step by Step

📍 Step 1 – I wrote a simple function number_root() that takes a list of numbers and returns their square roots;

<pre>
```python
def number_root(numbers):
    return [i**0.5 for i in numbers]

print(number_root([9, 25, 36, 10000]))
```
</pre>

📍 Step 2: Main Task – Created a function get_data() that downloads financial data from Yahoo Finance and cleans missing values using forward fill;
<pre>
```python
def get_data(tickers, period="90d"):
    data = yf.download(tickers, period=period)
    close_prices = data["Close"]
    clean_data = close_prices.ffill()
    return clean_data
```
</pre>

📍 Step 3: Computed daily returns, visualized correlations using scatter plots (IWM vs GLD, IWM vs IGOV)
<pre>
```python
def get_customised_data(tickers, start, end, missing_method="ffill"):
    data = yf.download(tickers, start=start, end=end)
    close_prices = data["Close"]

    if missing_method == "ffill":
        clean_data = close_prices.ffill()
    elif missing_method == "bfill":
        clean_data = close_prices.bfill()
    elif missing_method == "drop":
        clean_data = close_prices.dropna()
    else:
        raise ValueError("missing_method must be 'ffill', 'bfill' or 'drop'")

    return clean_data
```
</pre>


# Challenges / Insights

- Reinforced how important it is to handle missing values properly in financial datasets.
- Learned to add parameters to functions, making them flexible and reusable.
- This is the first building block for the upcoming dashboard.


# Next Step
👉 **Return Calculations**: extending the function to calculate daily returns and cumulative returns as the next core component of the dashboard.

# You'll find my projects here:
- 🔗 [GitHub Repository](https://github.com/DLPietro/learning-roadmap)
- 📊 [Google Colab](https://colab.research.google.com/github/DLPietro/learning-roadmap/blob/main/notebooks/day_8.ipynb)
