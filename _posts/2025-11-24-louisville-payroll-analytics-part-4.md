---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 5: Building the Tableau Dashboard"
date: 2025-11-24 21:36:47 +0200
categories: public-sector
tags: [tableau, bi, dashboard, payroll, analytics]
---

# 📊 From SQL Results to Visual Story

With the SQL layer stable (tables, indexes, views), it was finally time to switch hats and think like a BI developer.

The goal wasn’t to produce 20 random charts, but a **small dashboard** that a non‑technical stakeholder could actually use.

I decided on **four core views**:

1. **Yearly Trend:** headcount and overtime % over time  
2. **Salary by Department (2024):** total payroll and average salary  
3. **Overtime by Department (2024):** cost and intensity of overtime  
4. **Salary Variance by Job Title (2024):** internal pay ranges

---

# 🧩 Connecting Tableau to PostgreSQL

Steps:

- Data → PostgreSQL → connect to `louisville_payroll`  
- Use the analytical views (`v_department_summary`, `v_overtime_analysis`, `v_top_earners`) instead of raw tables  
- Verify field types (numeric vs string vs date)  
- Create a data source per thematic area (trend, department metrics, job title metrics)

Working directly on the views kept Tableau calculations clean and pushed heavy work down to SQL, where it belongs.

---

# 📈 View 1 – Yearly Trend

A dual‑axis chart:

- Area: number of employees over time  
- Line: overtime as a percentage of total payroll  

This immediately shows if overtime is growing faster than headcount, which is a red flag in any organization.

---

# 🏢 View 2 – Salary by Department (2024)

Horizontal bar chart:

- X‑axis: total payroll  
- Y‑axis: department (sorted descending)  

Tooltips include:

- employee count  
- average salary  
- share of total payroll  

This view answers “who costs the most?” at a glance, without touching SQL.

---

# 🔥 View 3 – Overtime by Department (2024)

Same structure as salary view, but:

- Bars = total overtime cost  
- Color = overtime % of total payroll  

This makes it impossible to ignore departments where overtime is both **large in absolute terms and heavy as a share of payroll**.

---

# ⚖️ View 4 – Salary Variance / Inequality

For this, I used a derived dataset (like *Salary-Variance-per-Job-Title*), built from SQL:

- Bars show salary range (max − min) per job title  
- Filter to job titles with at least N employees  
- Tooltip shows min, max, mean and std dev  

This is the visual counterpart of the SQL analysis on internal equity.

---

# 📌 Dashboard Layout

The final dashboard layout:



The work is directly tied to immediate and simple questions:

> _How big is the payroll?_  
> _Where is overtime concentrated?_
> _Which roles have the largest internal gaps?_

---

# 🎯 Next Steps

> Link it with the GitHub repo in the README.  
> Write a final “retrospective” post about what worked and what didn't.

**_To be continued..._**