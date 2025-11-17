---
layout: post
title: "📖 Day 5 – Financial Statistics"
date: 2025-08-30 17:32:15 +0200
categories: roadmap
tags: [python, roadmap, analytics]
---

# Rolling Statistics: Moving Average

This day I explored rolling statistics in Pandas, applied to financial time series; this lets me smooth data and analyzing volatility trends.

# Main Goals:

- Calculate moving averages (in this work 7 days) of closing prices.
- Calculate standard deviation (volatility), so the risk of each asset.
- Plot: first plots of daily returns and rolling metrics

# Step by Step
📍 Step 1: Download of data Matrix with assets and volumes as per previous works (closing prices and volumes of IWM, GLD, IGOV).

📍 Step 2: Calculated .pct_change(), 7-day moving average, and rolling std.

📍 Step 3: Plotted returns, moving averages, and volatility together, comparing the performances of each asset.

# Challenges / Insights

- Learned how .rolling(window) works.
- Discovered how to layer multiple plots on the same figure (ax=plt.gca()).
- Saw how volatility clusters can appear visually.

# Code Snippet

<pre>
```python
returns = close.pct_change().dropna()
mov_avg = close.rolling(window=7).mean()
std = close.rolling(window=7).std()

returns.plot(figsize=(10,6), title="Daily Returns")
mov_avg.plot(figsize=(10,6), title="7-Day Moving Average")
std.plot(ax=plt.gca())
plt.show()
  
```
</pre>

# Plots

<img src="https://github.com/DLPietro/DLPietro.github.io/blob/main/assets/img/1_daily_returns.png" alt="Daily Returns">
<p><em>Returns of the assets.</em></p>

<img src="https://github.com/DLPietro/DLPietro.github.io/blob/main/assets/img/2_moving_average.png" alt="MA">
<p><em>Moving Average.</em></p>


# Next Step
👉 Correlation analysis between assets.

# You'll find my projects here:
- 🔗 [GitHub Repository](https://github.com/DLPietro/learning-roadmap)
- 📊 [Google Colab](https://colab.research.google.com/github/DLPietro/learning-roadmap/blob/main/notebooks/day_4.ipynb)
