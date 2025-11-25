---
layout: post
title: "🎯 iGaming Retention Test - Part 2"
date: 2025-10-20 18:14:36 +0200
categories: igaming
tags: [python, pandas, simulation, datagen, igaming]
---

# Simulating 70,000 Players

The next step in the iGaming analytics project was to **create realistic synthetic data** to analyze retention and churn — even without access to real players.

# Main Goals of the day

- Generate 70K synthetic players using `numpy` and `pandas`
- Split players into **control** and **treatment** groups
- Simulate sessions, deposits, and feature usage
- Add a binary churn indicator (player left or not)

# Step by Step

📍 Step 1: Defined statistical distributions for sessions (Poisson) and deposits (Gamma)  
📍 Step 2: Introduced treatment boost (+2 sessions, +€20 deposits)  
📍 Step 3: Simulated feature adoption (Binomial: 0.4 vs 0.7)  
📍 Step 4: Added dynamic churn probability by player group  

# Insights

> Treatment users showed higher average deposits and slightly more sessions.  
>  
> This mirrors what happens in **feature rollout or promo exposure scenarios** in real iGaming data.

# Code Snippet

```python
import numpy as np
import pandas as pd

n = 70000
groups = np.random.choice(['control', 'treatment'], size=n)
sessions = np.random.poisson(5 + (groups == 'treatment') * 2)
deposits = np.random.gamma(shape=2, scale=50, size=n) + (groups == 'treatment') * 20
```
# Next Step

> Run a statistical test (A/B) to check if the retention difference is significant
> Add retention rate and p-value calculation with _Chi-square test_
