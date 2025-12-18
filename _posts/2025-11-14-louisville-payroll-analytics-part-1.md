---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 1"
date: 2025-11-14 19:15:00 +0200
categories: public-sector
tags: [sql, postgresql, dataengineering, tableau, payroll, analytics]
---

# 🏙️ From Database Chaos to Structured Analytics

I was tired of looking at public data as a huge CSV and _not really understanding anything_: I wanted to go beyond “open data as a file” and build an actual **analytics pipeline** creating SQL queries, views, and a live dashboard.

> **Turn the raw public sector salaries of a city (starting with Louisville, a not-so-huge US city) into a clean PostgreSQL schema, with SQL views and a Tableau Public dashboard** that tell us the status about salaries, overtime and equity in the public sector of the American city.

---

# ⚽ Main Goals

> Setting up a working PostgreSQL environment (with DBeaver as SQL client)  
> Importing the real **Louisville Metro payroll CSV** into a proper table  
> Designing a SQL schema and views to support analytics (salary distribution, overtime, inequality)  
> Building a Tableau dashboard with at least 4 core views for analytics-style storytelling  
> Documenting everything in a GitHub repository to show the way how I'm working  

---

# 📋 Step by Step

📍 **Step 1 (ETA 1-2 days): Losing time on PostgreSQL permissions**  
Creating a simple table should be easy, but that's not: I hit `permission denied for schema public` more times than I can count; I had to fix roles, grants, and reconnecting from DBeaver. At least now I know how it handles users and schemas.

📍 **Step 2 (ETA 1-2 days): Designing the `salary_data` table and loading the CSV dataset**  
Built a clean table for the dataset. First attempt failed because of NOT NULL constraints and column mismatches, annd after adjusting the mapping _(especially `cal_year`, `ytd_total`, and overtime columns)_, the dataset finally landed.

📍 **Step 3 (ETA 1-2 days): Building queries**  
added indexes on `department`, `cal_year`, `job_title`, and `ytd_total` to keep queries fast. I created views for department summaries, top earners, and overtime analysis using aggregations and window functions with several queries.

📍 **Step 4 (ETA 1-2 days): Connecting Tableau Public and shaping the dashboard**  
The last mile was visualising within Tableau, divided by grioups: trend view (headcount + overtime %), salary‑by‑department chart, aovertime‑by‑department chart, and a pay‑range‑by‑job‑title view for equity analysis.

---

# ⚡ PostgreSQL & DBeaver: the biggest issue

The most time consuming part wasn;t writing right queries, but **environment setup**:

- DBeaver kept failing silently on `CREATE TABLE` until I amended the columns of the dataset;  
- at the first attempt, the header didn’t match the table schema and the first line was being treated as data, not as header  

Once I slowed down and treated the database like an Excel matrix to be studied, things became stable, being able finally to focus on **analysis instead of fighting against the cells**.

---

# 📊 Structuring the Louisville Dataset

The original CSV contains 41+K of rows with fields like year, employee name, department, job title, annual and YTD (Year‑To‑Date) pay, plus overtime and allowances, so I modeled it into a single fact table:

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

This separation (raw table + analytical views) made Tableau integration much simpler.

---

# 🔑 First Insights

Even with “just” some SQL queries and a couple of views, the first patterns jumped out:

> A small group of departments drives a huge share of total payroll and overtime (e.g. police department).  
> Within specific job titles, the pay range can be enormous, hinting at strong differences in seniority and responsibility (e.g. mayor, etc.).  

Turning a static CSV into a relational model made it much easier to ask questions like:

- _Which departments carry the highest payroll burden in 2024?_  
- _Is overtime structurally high or just occasional?_  
- _Which roles have the widest salary range within the same title?_

These are exactly the kinds of questions stakeholders ask in real organization datasets.

---

# 🎯 Next Steps

> Refine the SQL layer with additional views for equity metrics (salary range, standard deviation by job title).  
> Write a technical README and link both the GitHub repo and the Tableau Public dashboard so others can reproduce the whole pipeline.  

**_To be continued..._**