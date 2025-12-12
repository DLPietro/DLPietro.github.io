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

📍 **Step 1: Losing time on PostgreSQL permissions**  
Creating a simple table should be easy, right? It wasn’t. I hit `permission denied for schema public` more times than I can count. Fixing roles, grants, and reconnecting from DBeaver took longer than expected, but it forced me to really understand how PostgreSQL handles users and schemas.

📍 **Step 2: Designing the `salary_data` table and loading the CSV**  
Once permissions were fixed, I created a clean table for the dataset and used DBeaver’s import wizard. First attempt failed because of NOT NULL constraints and column mismatches. After adjusting the mapping (especially `cal_year`, `ytd_total`, and overtime columns), the dataset finally landed in PostgreSQL.

📍 **Step 3: Building indexes and analytical views**  
With data in place, I added indexes on `department`, `cal_year`, `job_title`, and `ytd_total` to keep queries fast. Then I created views for department‑level summaries, top earners, and overtime analysis using aggregations and window functions.

📍 **Step 4: Connecting Tableau Public and shaping the dashboard**  
The last mile was visual. I connected Tableau directly to the views, built a yearly trend view (headcount + overtime %), a salary‑by‑department chart, an overtime‑by‑department chart, and a pay‑range‑by‑job‑title view for equity analysis.

# ⚡ PostgreSQL & DBeaver

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

On top of this raw table I added:

- Indexes on `department`, `cal_year`, `job_title`, `ytd_total` for performance  
- A view `v_department_summary` aggregating payroll, average salary and overtime per department/year  
- A view `v_top_earners` ranking employees within each department/year using `ROW_NUMBER()`  
- A view `v_overtime_analysis` focusing on the weight of overtime vs gross pay  

This separation — raw table + analytical views — made Tableau integration much simpler.

---

# 🔑 First Insights

Even with “just” SQL and a couple of views, some patterns jumped out:

> A small group of departments drives a huge share of total payroll and overtime, especially public safety units.  
> Within specific job titles, the pay range can be enormous, hinting at strong differences in seniority, responsibility, or possible equity issues.  

Turning a static CSV into a relational model made it much easier to ask questions like:

- Which departments carry the highest payroll burden in 2024?  
- Where is overtime structurally high vs. just occasional?  
- Which roles have the widest salary range within the same title?

These are exactly the kinds of questions stakeholders ask in real organizations — just translated to a public‑sector dataset.

---

# ⚙️ Example: Department Summary View

One of the core pieces is a view that summarizes payroll per department and year:

```sql
CREATE VIEW v_department_summary AS
SELECT
cal_year,
department,
COUNT(*) AS employee_count,
ROUND(AVG(annual_rate), 2) AS avg_annual_rate,
ROUND(AVG(ytd_total), 2) AS avg_ytd_total,
ROUND(SUM(ytd_total), 2) AS total_payroll,
ROUND(AVG(overtime_rate), 2) AS avg_overtime
FROM salary_data
GROUP BY cal_year, department;
```


This view is the backbone for multiple charts in Tableau: ranking departments by total payroll, looking at average salary by year, or comparing overtime intensity across units.

---

# 🎯 Next Steps

> Refine the SQL layer with additional views for equity metrics (salary range, standard deviation by job title).  
> Polish the Tableau dashboard to make it **presentation‑ready** (clean color palette, consistent tooltips, clear titles).  
> Write a technical README and link both the GitHub repo and the Tableau Public dashboard so others can reproduce the whole pipeline.  

This project started with a messy CSV and a lot of trial‑and‑error in PostgreSQL. Now it’s a small but real analytics stack: database, SQL logic, BI layer, and documentation. Next posts will dive into the queries, the Tableau views, and the insights in more detail.