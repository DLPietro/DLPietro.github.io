---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 1"
date: 2025-11-10 19:15:00 +0200
categories: public-sector
tags: [sql, postgresql, dataengineering, tableau, payroll, analytics]
---

# From Payroll Chaos to Structured Analytics

I was tired of looking at public data as a huge CSV and _not really understanding anything_: I wanted to go beyond “open data as a file” and build an actual **analytics pipeline** creating SQL queries, views, and a live dashboard.

It turned into a month-long journey full of permission errors, failed imports, wrong joins, and a lot of satisfaction when things finally clicked.

> **Turn the raw public sector salaries of a city (starting with Louisville) into a clean PostgreSQL schema + SQL views + a Tableau Public dashboard** that tells us a story about salaries, overtime and equity.

---

# ⚽ Main Goals

> Set up a working PostgreSQL environment (with DBeaver as SQL client)  
> Import the real **Louisville Metro payroll CSV** into a proper table  
> Design a SQL schema and views to support analytics (salary distribution, overtime, inequality)  
> Build a Tableau dashboard with 3–4 core views for business-style storytelling  
> Document everything in a GitHub repo so the work is **reproducible**, not a one‑off experiment  

---

# 📋 Step by Step

📍 **Step 1 – Losing time on PostgreSQL permissions**  
Creating a simple table should be easy, right? It wasn’t. I hit `permission denied for schema public` more times than I can count. Fixing roles, grants, and reconnecting from DBeaver took longer than expected, but it forced me to really understand how PostgreSQL handles users and schemas.

📍 **Step 2 – Designing the `salary_data` table and loading the CSV**  
Once permissions were fixed, I created a clean table for the dataset and used DBeaver’s import wizard. First attempt failed because of NOT NULL constraints and column mismatches. After adjusting the mapping (especially `cal_year`, `ytd_total`, and overtime columns), the dataset finally landed in PostgreSQL.

📍 **Step 4 – Connecting Tableau Public and shaping the dashboard**  
The last mile was visual. I connected Tableau directly to the views, built a yearly trend view (headcount + overtime %), a salary‑by‑department chart, an overtime‑by‑department chart, and a pay‑range‑by‑job‑title view for equity analysis.

# ⚡ PostgreSQL & DBeaver: The Hard Part No One Shows

The biggest hidden time sink in this project was not SQL logic, but **environment setup**:

- Wrong role: my user didn’t have privileges on schema `public`  
- DBeaver kept failing silently on `CREATE TABLE` until I checked the server logs  
- CSV import initially broke because the header mapping didn’t match the table schema and the first line was being treated as data, not as header  

It sounds trivial on paper, but when you hit these problems at midnight after a long day, it’s easy to get discouraged.

Once I slowed down and treated the database like a real production system — checking roles, testing small queries, validating row counts — things became stable. At that point I could finally focus on **analysis instead of firefighting**.

---

# 📊 Structuring the Louisville Dataset

The original CSV contains thousands of rows with fields like year, employee name, department, job title, annual and year‑to‑date pay, plus overtime and allowances.

I modeled it into a single fact table:

```sql
CREATE TABLE salary_data (
id SERIAL PRIMARY KEY,
cal_year INT NOT NULL,
employee_name VARCHAR(255) NOT NULL,
department VARCHAR(100) NOT NULL,
job_title VARCHAR(150) NOT NULL,
annual_rate NUMERIC(10, 2),
regular_rate NUMERIC(10, 2),

```

---

# 🏆 Final Thoughts: The Other Side of the Dashboard

After being inside this project, I can say one thing: building dashboards and writing SQL queries was not easy, but the real challenge is understanding **what kind of world that data comes from**.

This dataset, as mentioned before, comes from the **U.S. banking market**, and you can feel it; why? Americans have a completely different relationship with money: **credit is not a danger**, it’s a tool: they borrow to invest and build; the debt, for them, is justified as part of growth.

In Europe (especially in Southern Europe) it’s the opposite story: **we save before spending**, we find it scary and dangerous.  

So while analyzing this dataset, I genuinely found myself thinking:

> “If these were European customers, half these behaviors would never appear.”

That’s the interesting part: the same SQL queries, the same segmentation logic, but a completely different **financial psychology** behind the numbers, a **context** that has to be understood.  

That's exactly the reason why I'm passionate about this work, because I start with columns, rows, queries and dashboard, and then I end up questioning **why people are doing this or that!!**

💬 *Next step?* Maybe I’ll rebuild this entire analysis using **European-style banking data**, to see what happens when “credit” becomes the exception, not the rule.

---

# ⚡ Credits

[![GitHub Profile](https://img.shields.io/badge/GitHub-DLPietro-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/DLPietro)
[![Email](https://img.shields.io/badge/Email-dileopie-d14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dileopie@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pietro-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/pietrodileo)

> _© 2025 Pietro Di Leo. From Operations to Data, one Commit at a Time._