---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 3"
date: 2025-11-15 18:17:44 +0200
categories: public-sector
tags: [sql, postgresql, dbeaver, dataengineering, debugging]
---

# ⚡ PostgreSQL, DBeaver & Permission Hell

The second I tried to move from idea to implementation, reality hit:  
**PostgreSQL permissions + DBeaver configuration were way messier than expected.**

I thought I would “just create a database and a table”. Instead I spent evenings staring at:

```sql
ERROR: permission denied for schema public
ERROR: relation "salary_data" does not exist
```

Not exactly the fun, analytical work I had in mind.

---

# 🧱 What Went Wrong

- My PostgreSQL user didn’t have rights on the `public` schema.  
- DBeaver quietly failed to create tables until I opened the actual error messages.  
- I tried to import the CSV before the table existed, which of course broke everything.  

It was frustrating, but also very real. This is the stuff that never appears in polished tutorials.

---

# 🛠️ Fixing the Environment

Once I slowed down and treated this like a real server, things clicked:

1. **Connect as `postgres` superuser** and create the working database
2. **Grant proper privileges** to my user
3. Reconnect to the database in **DBeaver** using the `payroll_analyst` user.
4. Run a tiny smoke test

createdb louisville_payroll

