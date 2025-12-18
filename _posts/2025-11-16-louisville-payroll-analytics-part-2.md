---
layout: post
title: "🏙️ Louisville Payroll Analytics – Part 2"
date: 2025-11-16 20:26:14 +0200
categories: public-sector
tags: [sql, postgresql, dbeaver, dataengineering, debugging]
---

# ⚡ PostgreSQL, DBeaver & Permission Hell

The second I tried to move from idea to implementation, reality hit: **PostgreSQL permissions + DBeaver configuration process messier than expected!!!** I thought I would “just create a database and a table”, and I spent evenings staring at the following status instead:

```sql
ERROR: permission denied for schema public
ERROR: relation "salary_data" does not exist
```

**Not exactly the fun, analytical work I had in mind, and that I thought this work was.**

---

# 🧱 What Went Wrong

- My PostgreSQL user didn’t have rights on the `public` schema.  
- DBeaver quietly kept failing to create tables until I read error messages.  
- I tried to import the CSV _BEFORE_ the table existed, and of course it wasn;t working.  

---

# 🛠️ Fixing the Environment

Once I slowed down and treated this like a real server, things clicked:

📍 **Step 1:** Understanding how to connext `postgres` superuser
📍 **Step 2:** **Grant proper privileges** to my user
📍 **Step 3:** Reconnect to the database in **DBeaver** using the `payroll_analyst` user.
📍 **Step 4:** Run a first test

```sql
GRANT ALL PRIVILEGES ON DATABASE louisville_payroll TO payroll_analyst;
GRANT ALL PRIVILEGES ON SCHEMA public TO payroll_analyst;

...

CREATE TABLE test_table (id INT);
DROP TABLE test_table;

```

Seeing this statement run **without errors**: A MIRACLE!!!!

---

# 🎯 Next Steps

> Prepare for analytical queries.

**_To be continued..._**