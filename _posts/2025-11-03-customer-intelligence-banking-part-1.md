---
layout: post
title: "💰 Customer Intelligence Analytics Banking - Part 1"
date: 2025-11-03 18:42:30 +0200
categories: banking
tags: [sql, postgresql, dataengineering, tableau, banking, analytics]
---

# 🌄 Setting the Dataset

After years of working in the banking industry, handling data in Excel, copying and pasting from reports, I realized that I wanted to truly **understand** the data and create actionable insights for the business: _This project is my way out!!!_

> The aim is to understand the customers: _what they do and what we could do to keep them!!_ 


# ⚽ Main Goals

> Set up the environment (PostgreSQL database with DBeaver)  
> Download and Work on the original **banking dataset**
> Ensure that the data follows the same **distribution and patterns** as the original dataset  
> Build a SQL schema to structure the data  
> Start analyzing **customer segmentation** and **risk analysis**

---

# 📋 Step by Step

📍 Step 1: Struggled with PostgreSQL setup in DBeaver (more on this later)  
📍 Step 2: Expanded the dataset from 5K to 100K customers using **Python** and **Jupyter Notebook**  
📍 Step 3: Applied SQL transformations to ensure consistency and structure  
📍 Step 4: Ran the first queries to explore customer behavior and loan data

# ⚡ The Struggle with DBeaver & PostgreSQL

At first, I encountered a few headaches: configuring the PostgreSQL database with **DBeaver** wasn’t as smooth as expected. I spent hours troubleshooting connections, but after some trial and error, I finally managed to set it up. 

Once the environment was working, I could finally focus on what mattered: _getting data into PostgreSQL and starting the analysis._

# 📊 Dataset Expansion

I used the **[Banking-Dataset by Ahsan Habib](https://github.com/ahsan084/Banking-Dataset)** as my base, a dataset containing 5,000 customers with various demographics, account details, loans, and credit card information. The challenge? **Scaling it to 100,000 customers** without losing the integrity of the original data.

I wrote a Python script in **Jupyter Notebook** to generate synthetic customer data, preserving the distribution and relationships in the original dataset. The final result was a **100K customer dataset** ready for SQL analysis.

# 🔑 Key Insights

> The expanded dataset allowed me to test a wider range of hypotheses, from customer segmentation to identifying risky loans.  
> The synthetic data generation process mirrored real-world banking dynamics while providing a robust dataset for deeper analysis.

# ⚙️ Code Snippet: Dataset Expansion with Python on Jupyter Notebook

```python
import pandas as pd
import numpy as np
from datetime import datetime, timedelta
import random

original_data = pd.read_csv('banking_database.csv')

target_rows = 100000
existing_rows = len(original_data)
new_rows_needed = target_rows - existing_rows

print(f"Generating {new_rows_needed} new customer records...")

# Defining sample data to append on the existing dataset
first_names = ['Joshua', 'Mark', 'Joseph', 'Kevin', 'Linda', 'Charles', 'Christopher', 'Daniel', 'William', 
```

# 🎯 Next Steps

> Run the first SQL queries on the expanded dataset, focusing on customer segmentation and loan analysis.
> Start building the Tableau dashboard to visualize and act on the data: understanding customers, spotting risks, and identifying upsell opportunities.