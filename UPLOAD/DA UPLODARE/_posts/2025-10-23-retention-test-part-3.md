---
layout: post
title: "🎯 iGaming Retention Test - Part 3"
date: 2025-10-23 17:45:22 +0200
categories: igaming
tags: [abtest, retention, statistics, python, scipy]
---

# A/B Testing Retention

After generating our synthetic dataset, it’s time to **test if the new feature (treatment)** truly improves player retention.

# Main Goals of the day

- Compute retention rate for control vs treatment  
- Run a **Chi-square test** for statistical significance  
- Visualize retention results  

# Step by Step

📍 Step 1: Grouped players by `user_group` and computed churn/retention  
📍 Step 2: Built a 2x2 contingency table for the Chi-square test  
📍 Step 3: Ran `scipy.stats.chi2_contingency`  
📍 Step 4: Plotted retention difference  

# Insights

> Retention in treatment = **65.8%**  
> Retention in control = **56.3%**  
>  
> The treatment produced a **+9.5 percentage points uplift** in retention.

# Code Snippet

```python
from scipy.stats import chi2_contingency

contingency = [[35000*0.563, 35000*(1-0.563)],
               [35000*0.658, 35000*(1-0.658)]]

chi2, p, _, _ = chi2_contingency(contingency)
print(f"Chi-square: {chi2:.2f}, p-value: {p:.4f}")
```
# Next Step

> Extend the analysis with **churn prediction modeling**

> Test how features (sessions, deposits, feature_used) correlate with player churn
