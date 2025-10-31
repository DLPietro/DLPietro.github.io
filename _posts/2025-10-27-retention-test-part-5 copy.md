---
layout: post
title: "🎯 iGaming Retention Test - Part 5"
date: 2025-10-27 19:08:47 +0200
categories: igaming
tags: [sql, dataengineering, pipelines, analytics, retention]
---

# SQL Pipelines & Player Metrics

After modeling churn, it’s time to **structure the data pipeline** that feeds all metrics — just like in a real iGaming environment.

# Main Goals of the day

- Load player data into a **SQLite** database  
- Create SQL tables for player-level KPIs  
- Aggregate sessions, deposits, and feature usage per user  
- Prepare data for daily retention tracking  

# Step by Step

📍 Step 1: Loaded CSV data into SQLite  
📍 Step 2: Created player-level aggregation table  
📍 Step 3: Calculated churn and feature usage metrics  
📍 Step 4: Validated the schema for analytics use  

# Insights

> The SQL layer allows easier scaling and integration with BI dashboards.  
>  
> Once structured, retention metrics can refresh automatically — daily or weekly.

# Code Snippet

```sql
CREATE TABLE player_metrics AS
SELECT 
  user_id,
  user_group,
  SUM(sessions) AS total_sessions,
  SUM(deposits) AS total_deposits,
  AVG(feature_used) AS feature_ratio,
  AVG(churn) AS churn_rate
FROM player_activity
GROUP BY user_id, user_group;
```
# Next Step

> Connect SQL data to _Plotly_ visualizations
> Build an interactive dashboard for real-time retention tracking
