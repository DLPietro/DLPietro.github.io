---
layout: post
title: "📖 Day 3 – Python Essentials"
date: 2025-08-26 18:41:36 +0200
categories: roadmap
tags: [python, roadmap, analytics]
---

# Inputs, Conditions, Loops & Strings

I focused on practising the fundamentals of Python programming: inputs, conditions, loops, and string manipulation. Basically, the essential building block, not only for basics, but also for financial analysis tasks (e.g., validating inputs, iterating over datasets, etc.).

# Main Goals:

- Generating numbers: learned how to handle user input (input()) and convert it into numeric types
- Using conditionals (if / elif / else)
- Loops like for and while cycles
- String methods, and patterns with them

# Step by Step
📍 Exercise 1: Inputs & Arithmetic
I asked the user for two integers (that I can type after the code runs), and applied basic operations (sum, difference, product, division):

<pre>
```python
a = int(input("Primo Numero: "))
b = int(input("Secondo Numero: "))
risultati = {"somma": a+b, "differenza": a-b, "prodotto": a*b, "divisione": round(a/b, 2)}
print(risultati)

```
</pre>

📍 Exercise 2: Conditions.
Using if / elif / else, I built a simple grading system; a logic that can be useful in finance as well (e.g., categorizing risk scores like in a rating agency).

📍 Exercise 3: For Loop
Printed numbers from 1 to n, reinforcing iteration basics.

📍 Exercise 4 – While Loop
Calculated the sum of integers from 1 to n with a while loop — a great exercise in understanding loop termination conditions.

📍 Exercise 5 – Strings
Cleaned a user-input sentence: removed spaces, converted to lowercase, and replaced vowels with "*". This simulates text preprocessing.

📍 Exercise 6 – Palindrome Check
Checked if a word reads the same backward — practicing indexing and string slicing ([::-1]).


# Challenges / Insights

- Remembering to convert input() from string to integer before doing math (int() casting).
- Ensuring loops terminate correctly (avoiding infinite loops).
- Understanding string immutability: every transformation creates a new string.
- Seen how simple conditions and loops could translate directly into financial logic (e.g., thresholds for buy/sell signals).

# Code Snippet Final

<pre>
```python
# Example: while loop sum
numero = int(input("Numero positivo: "))
contatore, somma = 1, 0

while contatore <= numero:
    somma += contatore
    contatore += 1

print(f"La somma da 1 a {numero} è: {somma}")
```
</pre>

# Next Step
👉 Combine these fundamentals with financial use cases — applying conditions and loops to stock returns and building simple logic for portfolio signals.

# You'll find my projects here:
- 🔗 [GitHub Repository](https://github.com/DLPietro/learning-roadmap)
- 📊 [Google Colab](https://colab.research.google.com/github/DLPietro/learning-roadmap/blob/main/week-1/exercises.ipynb)
