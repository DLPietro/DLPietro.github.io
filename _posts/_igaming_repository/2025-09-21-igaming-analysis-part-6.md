---
layout: post
title: "🎲 Casino Analytics Dashboard - Part 6"
date: 2025-09-21 19:48:50 +0200
categories: [sql, cohort, igaming, retention]
---

# Intro

I wrote the SQL cohort analysis to find **who’s about to leave**.

# Main Goals of the day:

- Write SQL to calculate intra-week retention (Day 0 to Day 6)  
- Focus on **first deposit date** as cohort anchor  
- Don’t do “monthly” — do **weekly**, because my data is 7 days

# Step by Step

📍 Step 1: Found first deposit date per player → `MIN(session_start)` where deposit > 0  
📍 Step 2: Joined back to sessions → now I know: “Player P0123 deposited on Sep 2”  
📍 Step 3: Calculated `day_diff = session_date - cohort_date`  
📍 Step 4: Filtered to `day_diff BETWEEN 0 AND 6` → only sessions within 7 days of first deposit  
📍 Step 5: Grouped by cohort_date + day_diff → counted active players per day

# Challenges / Insights

> Cohort analysis is used for monthly retention. I tried to adapt it according to the simulated dataset in the window you have.**

With this method, you could see the effects on a **7-day cohort** of the marketing campaigns.

And guess what?  
It’s **more useful**.

Because in iGaming:  
- If a player doesn’t return by Day 4 → they’re gone.  
- If they return by Day 2 → they’re hooked.

This isn’t academic, but **survival**.

# SQL Snippet Final

```sql
WITH first_deposit AS (
  SELECT player_id, MIN(session_start) AS cohort_date
  FROM player_sessions
  WHERE deposit_amount > 0
  GROUP BY player_id
)
SELECT 
  DATE(fd.cohort_date) AS cohort_date,
  DATEDIFF(ps.session_start, fd.cohort_date) AS day_diff,
  COUNT(DISTINCT ps.player_id) AS active_users
FROM player_sessions ps
JOIN first_deposit fd ON ps.player_id = fd.player_id
WHERE ps.session_start BETWEEN fd.cohort_date AND fd.cohort_date + INTERVAL '6 days'
GROUP BY 1,2
ORDER BY 1,2;
```
</pre>

# Next Step
👉 Generate the heatmap in Python → _show it visually._
