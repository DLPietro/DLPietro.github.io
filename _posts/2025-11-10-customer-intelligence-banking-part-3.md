---
layout: post
title: "💰 Customer Intelligence Analytics Banking - Part 3"
date: 2025-11-10 14:45:57 +0200
categories: banking
tags: [sql, postgresql, datavisualization, tableau, banking, analytics, queries, risk]
---

# 📊 Tableau Dashboard & Call to Action

As I started to build out the Tableau dashboard, it became clear that the **real value** in this project was not just generating SQL queries, but creating a **Visual Tool** that could be used by stakeholders to make better decisions in real-time: in other words, whoever finds numbers and graphs difficult to read and understand.


# ⚽ Main Goals

> Build and refine the **Tableau Dashboard**  
> Add filters and interactivity for better insights
> Implement **call-to-action** for customer retention  
> Focus on **Tier-1 customers** as they are the most valuable, and identifying the high-risk ones 

---

# 📋 Step by Step

📍 Step 1: Designed the **KPI Summary** tab, key metrics like loan portfolio size, average balance, and high utilization 
📍 Step 2: Built the **Customer Overview** tab, showing account balances and behaviors by **account type**  
📍 Step 3: Integrated a **Credit Card Health** tab to highlight customers above 80% utilization
📍 Step 4: Added the **Customer Value** bubble chart, to compare tier lists and net positions of each client  


# 🔑 Key Insights

> **Tier-1 customers** (high-value, low-risk) emerged as the main focus for retention.  
> These customers use credit more frequently, despite their negative balances, their income are safer for long-term profitability.  
> The dashboard visualizes this, allowing teams to focus on creating customised product and services for these clients.


# 📊 Tableau Visual: CI Dashboard

![Customer Value by Tier](https://github.com/DLPietro/customer-intelligence-analytics-banking/blob/main/bi/customer_intelligence_dashboard.png)
_The Dashboard shows the KPIs table, customer segmentation, credit card types, loan type an status barchart seen previously, and the Customer Value bubble chart._

---

# 🏆 Final Thoughts: The Other Side of the Dashboard

After being inside this project, I can say one thing: building dashboards and writing SQL queries was not easy, but the real challenge is understanding **what kind of world that data comes from**.

This dataset, as mentioned before, comes from the **U.S. banking market**, and you can feel it in every line of data.  
Americans have a completely different relationship with money: **credit is not a danger**, it’s a tool.  
They borrow to invest, to build, to move forward.  
Debt, for them, is almost part of growth.

In Europe, and especially in Southern Europe, it’s the opposite story.  
We save before we spend. We fear debt, and we see loans as something exceptional, not strategic.  
So while analyzing this dataset, I constantly found myself thinking:  
> “If these were European customers, half these behaviors would never appear.”

That’s the interesting part — the same SQL queries, the same segmentation logic,  
but a completely different **financial psychology** behind the numbers.

This project taught me that **analytics is not just about precision**,  
it’s about **context**.  
You can’t read data without understanding the culture it comes from.  

And that’s what I love about this work — you start with columns and CSVs,  
and end up questioning **how people live, think, and spend**.

💬 *Next step?* Maybe I’ll rebuild this entire analysis using **European-style banking data**, to see what happens when “credit” becomes the exception, not the rule.

> From the dashboard to thinking.