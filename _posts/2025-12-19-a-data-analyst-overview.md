---
layout: post
title: "🧾 Dev Log - From theory to data analytics"
date: 2025-12-19 01:00:00 +0200
categories: portfolio
tags: [sql, python, postgresql, tableau, banking, payroll, analytics, freelancing]
---

# ⏳ From late summer till now

I measured the time from August to the end of 2025 in:

> Struggling with theory and programming basics
> Getting mad to understand the differences between Jupyter notebook and a terminal
> How to Install Debian on my old laptop TO SAVE IT
> failed `CREATE TABLE` statements 
> broken CSV imports  
> Github running commits for the blog that said “failed” on Actions sections


It started with a simple idea:  

> _Stop living in Excel empty formulas and start building real, reproducible data projects.

What followed was a sequence of not marked steps: programming, Python and SQL basics, statistic theory and Maths, datasets, and finally a decent project that refused to let me sleep: **Louisville Metro Public Payroll**.

This post is a recap of that journey: **what I built, broke, learned, and where I’m going next.**

---

# 🧱 Recent Projects Built (and Survived with myself as well)

## Banking Customer Intelligence analytics (Jupyter Notebook + PostgreSQL + Tableau)

The first big step was **Customer Intelligence Analytics – Banking**.

> Took a raw banking dataset and **scaled it** from 5K to 100K customers using Python and Jupyter.  
> Designed a PostgreSQL schema, loaded everything through DBeaver, and wrote SQL to explore:
  - customer segments  
  - loan status  
  - risk and churn  
> Built the first dashboards in Tableau: nothing fancy, but real **customer intelligence** instead of “just pivots”.

I wanted to understand _behavior_: who are the good customers, who is about to leave, and who is quietly becoming risk?

It was my way of saying:  
> “I can do more than SELECT * FROM table.”

---

## Louisville Metro Public Payroll Analytics

For the last project, I moved from simulation to **reality**.

- **40,000+** salary records from an American city (Louisville)  
- **5+ years** of history  
- Several departments and job titles  
- Overtime, allowances, inequality baked into the numbers

What I built:
- A clean `salary_data` table in PostgreSQL.  
- Indexes and analytical views:
  - department‑level payroll and overtime  
  - top earners per department/year with window functions  
  - overtime intensity and salary spread by job title  
- A **Tableau Public dashboard** that actually feels like something a city manager, journalist, or citizen could use.

This was the project where everything came together:
- SQL skills from the banking work  
- lessons learned from the cruise simulation  
- and a very stubborn decision to get it right, even if PostgreSQL permissions and CSV imports fought back for days.

---

# 🧠 What I Actually Learned

Beyond the code, these were the real lessons:

### 1. Python and SQL are not syntax, but thinking

I stopped writing Python or SQL like “Ok, I do copy-paste and that's it" and started writing it like “Let's add something from mine.”

### 2. Tools are boring… until they break

DBeaver, PostgreSQL, Jupyter, Tableau, VS Code, Git.  
They sound like a checklist. They’re actually a battlefield.

I went from:
- “Why is DBeaver not creating my table?”  
to  
- “Check role, schema, grants, then import, then validate row counts.”

Environment issues are not glamorous, but they’re **part of the job**.

### 3. Dashboards are the final 20%, but 80% of the perception

No one sees:
- the four iterations of the schema  
- the broken import where `cal_year` was NULL  
- the mistake where overtime was summed as a rate instead of a cost.

They see:
- a clean yearly trend  
- a ranking of departments  
- and maybe a headline like “Top 10% employees capture 28% of total pay”.

I learned to accept that:
> _The code is for me. The dashboard is for them._

---

# 🧳 Portfolio Status (December 2025)

Right now, my portfolio has a **GitHub Structure** that is finally not a random graveyard of notebooks.

> Is it perfect? No.  
> Is it enough to say “Maybe I'm not a professional, but I'm trying to make as I'm one”? Yes.

---

# 🧭 What’s Next (Skills & Freelance Direction)

Going into 2026, I want to move in two parallel directions.

### 1. Technical depth

- Stronger **statistics**: hypothesis testing, confidence intervals, basic modeling (logistic regression for churn, LTV estimation).  
- More **Python in production mode**: cleaner scripts, not just notebooks; small ETL/ELT jobs.  
- Better **data storytelling**: fewer noisy charts, more “this matters because…”.

### 2. Freelance‑ready projects

I want to design projects that look like real client work, not just portfolio experiments:

- A **small business dashboard**: sales, invoices, cash flow, built so a non‑technical owner can use it.  
- A **churn/retention analysis** for a subscription‑style dataset.  
- A **“data audit” project template**: take someone’s messy Excel, turn it into a database + dashboard, document everything.

The idea is simple:
> Start small, solve real problems, and show it in public.

---

# 🚀 Closing the Loop

From August/September to now, it felt like one long sprint:
- from Excel to Jupyter Notebook and PostgreSQL  
- from random CSVs to structured schemas  
- from “I hope this works” to “that's an overview from the first data mess you provided”.

I’m not “done”: I’m at a better starting point.

The next moves are about turning this into:
- more **client‑like projects**  
- more **writing about the process**  
- and, slowly, a **freelance profile** that is built on real work, not buzzwords.

---

# ⚡ Credits

[![GitHub Profile](https://img.shields.io/badge/GitHub-DLPietro-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/DLPietro)
[![Email](https://img.shields.io/badge/Email-dileopie-d14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dileopie@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pietro-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/pietrodileo)

> _© 2025 Pietro Di Leo. From Operations to Data, one Commit at a Time._