---
layout: post
title: "🎯 iGaming Retention Test - Part 4"
date: 2025-10-25 18:24:52 +0200
categories: igaming
tags: [machinelearning, sklearn, churn, modeling, python]
---

# Predicting Churn with Logistic Regression

Now that we’ve confirmed retention uplift, let’s try to **predict churn** to understand which factors drive player loss.

# Main Goals of the day

- Train a **Logistic Regression** model to predict churn  
- Use sessions, deposits, and feature usage as predictors  
- Evaluate accuracy, recall, and precision  
- Interpret feature coefficients  

# Step by Step

📍 Step 1: Encoded features and target (`churn`)  
📍 Step 2: Split dataset into train/test  
📍 Step 3: Fitted logistic regression with `sklearn`  
📍 Step 4: Evaluated model performance metrics  

# Insights

> The model performs slightly above random:  
> AUC = 0.547, Accuracy = 54%, Recall = 52%  
>  
> Early churn models often struggle due to class imbalance — still, it reveals interesting patterns.


# Code Snippet

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import roc_auc_score

X = df[['sessions', 'deposits', 'feature_used']]
y = df['churn']

model = LogisticRegression()
model.fit(X, y)
auc = roc_auc_score(y, model.predict_proba(X)[:,1])
print("AUC:", auc)
```
# Next Step

> Add SQL-based aggregation to structure metrics and retention KPIs
> 
> Enrich the dataset with session-level metrics before retraining
