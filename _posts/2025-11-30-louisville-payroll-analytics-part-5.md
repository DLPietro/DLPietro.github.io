---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 6: Retrospective, Mistakes & Lessons"
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

# ❤️ What I Learned (Personal Side)

This project reminded me that:

- It’s okay if “hello world” with a new stack takes days instead of minutes.  
- Real progress looks like: _it doesn’t work → I read logs → I try again → it works one step further_.  
- Satisfaction hits when you finally run a complex query, refresh the dashboard, and the numbers make sense.

I wanted to move from “I watched a tutorial” to “I built something end‑to‑end”.  
This repo and the Louisville dashboard are my proof of that.

---

# 🔗 Links

- **GitHub Repository:** `https://github.com/...`  
- **Tableau Public Dashboard:** `https://public.tableau.com/...`  

---

# 🎯 What’s Next

> Reuse this pattern (PostgreSQL + SQL views + BI tool + README) for other domains (banking, iGaming, customer intelligence).  
> Keep improving the Louisville project: maybe add forecasting, more advanced equity metrics, or scenario analysis.  
> Bring these skills into real interviews and real work.

If you’re reading this because you’re on a similar path: don’t underestimate the value of one solid, honest project that actually runs end‑to‑end.  
This is mine.

---

# ⚡ Credits

[![GitHub Profile](https://img.shields.io/badge/GitHub-DLPietro-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/DLPietro)
[![Email](https://img.shields.io/badge/Email-dileopie-d14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dileopie@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pietro-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/pietrodileo)

> _© 2025 Pietro Di Leo. From Operations to Data, one Commit at a Time._