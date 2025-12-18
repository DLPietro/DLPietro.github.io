---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 3"
date: 2025-11-20 18:17:44 +0200
categories: public-sector
tags: [sql, postgresql, dbeaver, dataengineering, debugging]
---

#  🔍 First Queries & Insights

Before opening Tableau, I wanted to squeeze as much understanding as possible directly from SQL, in particular to understand how salaries, departments and overtime actually behave.

# 👥 Salary Distribution by Department

```sql
SELECT
department,
COUNT(*) AS employee_count,
ROUND(MIN(annual_rate), 2) AS min_annual,
ROUND(AVG(annual_rate), 2) AS avg_annual,

...

```


This query showed:

> A small set of departments _(police, fireman, public works, large services...)_ dominating total payroll.  
> Departments with similar headcount but very different average salaries and pay variance.

---

# 🔥 Overtime by Department

```sql
SELECT department,
COUNT(*) AS employees_with_ot,
ROUND(SUM(overtime_rate), 2) AS total_ot_cost,
ROUND(AVG(overtime_rate), 2) AS avg_ot_per_employee,
ROUND(
SUM(overtime_rate) / NULLIF(SUM(ytd_total), 0) * 100,
2
) AS ot_percent_of_gross
FROM salary_data
WHERE ...
```

A brief overview:

> A handful of departments (especially police department) carry the majority of overtime costs.  
> In some units, overtime reaches **20–30% of total payroll**, which is huge and immediately suggests staffing or scheduling issues.

---

# ⚖️ Pay Inequality Within Job Titles

To study internal equity, I focused on pay ranges within the same job title and department.

```sql
SELECT job_title,
COUNT() AS total_employees,
ROUND(AVG(annual_rate), 2) AS avg_rate,
ROUND(MIN(annual_rate), 2) AS min_rate,
ROUND(MAX(annual_rate), 2) AS max_rate,
ROUND(MAX(annual_rate) - MIN(annual_rate), 2) AS salary_range,
ROUND(STDDEV(annual_rate), 2) AS stddev_rate

...

```

This highlighted job titles where people with the same job name had massive pay differences; this doesn’t mean unfairness automatically, but it’s exactly the kind of pattern that needs more attention and care.

---

# 🔑 Takeaways Before Data Visualization with Tableau

SQL alone is already enough to surface which departments dominate payroll, where overtime is structurally high, and the further queries I wrote for the anayltics. With a mental model of the dataset, it's easier to create a dashboard with Tableau, and to focus on the **storytelling and accessibility** of dataset just anaysed.

---

# 🎯 Next Steps

> Connect Tableau Public directly to the PostgreSQL views.  
> Design a small set of focused worksheets: yearly trend, salary by department, overtime by department, pay range by job title.  

**_To be continued..._**