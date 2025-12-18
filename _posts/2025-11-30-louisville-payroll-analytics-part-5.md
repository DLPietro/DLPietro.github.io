---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 5"
date: 2025-11-30 18:19:42 +0200
categories: public-sector
tags: [sql, tableau, portfolio, learning, retrospective]
---

# 🔁 Looking Back at the Project

From the outside, this repository now looks clean:  
SQL scripts, views, a Tableau dashboard, and a README.

From the inside, it was **a month of small battles**:

- PostgreSQL permissions and `pg_hba.conf` headaches  
- DBeaver import failures and mis‑mapped columns  
- Wrong joins, missing rows, and totals that made no sense the first time  
- Iterating structure and naming until things finally felt right  

And that’s exactly why this project matters to me. It’s not just “a finished dashboard”, it’s the proof that I can hold through the boring and frustrating parts until I get to insight.

---

# 🧨 Biggest Surprises

- **Environment problems took longer than SQL logic.**  
  Setting up roles, granting schema privileges, and getting DBeaver to cooperate cost more time than writing the core queries.

- **Simple checks saved me.**  
  Row counts before and after joins, sum of payroll by year, basic sanity checks—these caught most of my early mistakes.

- **Views are underrated.**  
  Moving logic into views made Tableau simpler and made the overall architecture feel more like a real BI stack.

---

# 💡 What I Learned (Technically)

- How to **design a fact table** (`salary_data`) that is friendly for analytics.  
- How to use **indexes** to keep queries fast on real data.  
- How to build **window‑function‑based views** (rankings, running totals, variance analysis).  
- How to **structure a Tableau dashboard** around a narrative, not just charts.  
- How to keep everything **version‑controlled and reproducible** via GitHub.

---

# ❤️ What I Learned

This project thaught me two things:

> More difficult than expected
> Satisfaction hits when you finally run a complex query, refresh the dashboard, and the numbers make sense.

---

# 📊 Tableau Visual: Links

<img src="https://github.com/DLPietro/DLPietro.github.io/raw/main/assets/img/louisville_dashboard.png" alt="Customer Value by Tier">
<p><em>The dashboard shows the overall budget by department, overtime per department, salary ranking per job title, and the yearly trend comparing number of employees and average overtime rate.</em></p>

🔗 **[View the Live Dashboard 👉](https://public.tableau.com/views/LouisvilleMetroPayrollAnalytics-PublicSectorSalaryDashboard/Dashboard1?:language=it-IT&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

---

# 🎯 What’s next now?

> General review about what I made so far and my future projects.

---

# ⚡ Credits

[![GitHub Profile](https://img.shields.io/badge/GitHub-DLPietro-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/DLPietro)
[![Email](https://img.shields.io/badge/Email-dileopie-d14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dileopie@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pietro-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/pietrodileo)

> _© 2025 Pietro Di Leo. From Operations to Data, one Commit at a Time._