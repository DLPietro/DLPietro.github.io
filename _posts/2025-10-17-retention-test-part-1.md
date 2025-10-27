---
layout: post
title: "🎯 iGaming Retention Test - Part 1"
date: 2025-10-17 17:52:00 +0200
categories: igaming
tags: [python, sql, retention, abtest, igaming]
---

# From Players to Patterns

I’ve started a new piece of the iGaming analytics project — focused on **player retention and promo testing**.

# Main Goals of the day

- Build an A/B test simulation on player promos (NEWUSER10 vs control)
- Use survival analysis to model retention over time
- Create SQL pipelines for session aggregation and player-level metrics

# Step by Step

📍 Step 1: Generated synthetic player activity over 4 weeks  
📍 Step 2: Flagged promo-exposed players (`treatment`) vs control  
📍 Step 3: Modeled survival function using **Lifelines Kaplan-Meier**  
📍 Step 4: Visualized retention curves and promo impact  

# Insights

> Retention uplift detected around day 10 for promo users.  
>  
> Next goal: validate if the difference is **statistically significant** — using the log-rank test.  

The interesting part?  
Retention behavior in gaming is **non-linear**: you have short bursts of engagement, then long periods of silence. The model needs to reflect that.

# Code Snippet

```python
from lifelines import KaplanMeierFitter

kmf = KaplanMeierFitter()
kmf.fit(durations=treatment['days_active'], event_observed=treatment['active'])
kmf.plot_survival_function(label="Promo Group")
```
# Next Step

> Validate statistical significance of retention difference
> Add monetization variable (GGR / session duration)
> Create an automated SQL + Python workflow for periodic tests
