# Project Type

DSA + Python Practical Project
# Main Goal of the Project

Build a terminal-based Python application where users can:

- add expenses,
- categorize spending,
- search transactions,
- sort expenses,
- analyze spending,
- and generate summaries.

The project should feel:

- practical,
- modern,
- beginner-friendly,
- and real-world relatable.

The focus is:

- learning DSA naturally,
- improving coding confidence,
- understanding project structure,
- and building logic.
# Core Features

## 1. Add Expense

Users can add:

- expense title,
- amount,
- category,
- date.

Example:

```
{    "title": "Pizza",    "amount": 250,    "category": "Food",    "date": "2026-05-12"}
```
## 2. Categorize Expense

Expense categories include:

- Food
- Travel
- Shopping
- Bills
- Recharge
- Entertainment
- Health
- Others

Purpose:

- organize expenses,
- generate summaries,
- analyze spending patterns.
## 3. Search Expense

Users can search:

- by title,
- by category,
- optionally by date later.

Concept used:

- Linear Search
## 4. Sort Highest Spending

Expenses can be sorted:

- highest to lowest,
- lowest to highest.

Sorting based on:

- amount.

Concepts used:

- Sorting algorithms
- Python sorted()
## 5. Monthly Summary

Generate:

- total spending,
- category-wise spending,
- highest spending category.

Example:

```
Total Spent: ₹5000Food: ₹2000Travel: ₹1000Shopping: ₹2000
```

Concepts used:

- Hashing
- Dictionaries
- Aggregation
## 6. Recent Transactions

Show:

- latest 5 expenses.

Concepts used:

- Array slicing
- Lists
## 7. Simple Analytics

Generate insights like:

- highest spending category,
- average expense,
- weekly spending,
- monthly spending trends.

Concepts used:

- Sliding Window
- Aggregation
- Traversal
## 8. Budget Warning System (Optional Upgrade)

Example:

```
⚠️ Warning: Food spending exceeded budget.
```

Purpose:

- make project feel smart and realistic.
# DSA Concepts Used

## Arrays / Lists

Used to:

- store all expenses.

Example:

```
expenses = []
```
## Dictionaries

Used to:

- store individual expense data.

Example:

```
{    "title": "Pizza",    "amount": 250}
```
## Searching

Used in:

- search expense feature.

Main concept:

- Linear Search
## Sorting

Used in:

- highest spending feature.

Topics:

- Bubble Sort (for teaching)
- Python sorted()
## Hashing

Used in:

- category summary,
- frequency counting.

Implemented using:

- Python dictionaries.
## Sliding Window

Used in:

- weekly spending analytics.

Purpose:

- optimize repeated calculations.
# Technologies Used

## Programming Language

- Python

## Development Tools

- VS Code
- Google Colab (optional)

## Storage

- JSON file

## Optional Libraries

- colorama (colored terminal)
- datetime
- json

# Final Project Structure

```
smart-expense-tracker/│├── main.py├── expense_manager.py├── analytics.py├── storage.py├── utils.py├── data.json├── README.md└── requirements.txt
```

# File Explanations
---
# main.py

Purpose:

- entry point of application.

Responsibilities:

- show menu,
- handle user interaction,
- call functions.
---
# expense_manager.py

Purpose:

- manage expenses.

Responsibilities:

- add expense,
- view expenses,
- search expense,
- sort expenses,
- delete expense.
---
# analytics.py

Purpose:

- generate insights.

Responsibilities:

- monthly summary,
- weekly analytics,
- spending reports,
- highest spending category.
---
# storage.py

Purpose:

- handle file storage.

Responsibilities:

- save JSON,
- load JSON.
---
# utils.py

Purpose:

- helper functions.

Responsibilities:

- validations,
- formatting,
- reusable logic.
---
# data.json

Purpose:

- permanent data storage.

Stores all expenses.

---
# README.md

Purpose:

- project documentation.

Contains:

- project explanation,
- setup guide,
- features,
- screenshots later.
---
# requirements.txt

Purpose:

- dependency management.

Example:

```
colorama
```
# Expense Data Structure

Each expense object:

```
{    "title": "Pizza",    "amount": 250,    "category": "Food",    "date": "2026-05-12"}
```

All expenses stored inside:

```
expenses = []
```
# Menu Structure

```
1. Add Expense2. View Expenses3. Search Expense4. Sort Expenses5. Monthly Summary6. Recent Transactions7. Analytics8. Exit
```

# Project Development Phases

---
# Phase 1 — Project Setup & Structure

Topics:

- folder structure,
- modular files,
- imports,
- initial expense list.

Learning:

- modular programming,
- project architecture.
---
# Phase 2 — Expense Data Model

Topics:

- expense dictionary,
- user input,
- CRUD basics.

Learning:

- dictionaries,
- lists,
- dynamic data.
---
# Phase 3 — Add Expense Feature

Topics:

- taking input,
- appending data.

Learning:

- lists,
- functions.
---
# Phase 4 — View Expenses

Topics:

- loops,
- displaying formatted data.

Learning:

- iteration,
- traversal.
---
# Phase 5 — Search Expense

Topics:

- linear search.

Learning:

- searching algorithms.
---
# Phase 6 — Sort Expenses

Topics:

- sorting logic,
- Python sorted().

Learning:

- sorting algorithms.
---
# Phase 7 — Category System

Topics:

- category management,
- filtering.

Learning:

- conditions,
- grouping.
---
# Phase 8 — Monthly Summary

Topics:

- category-wise totals,
- aggregations.

Learning:

- hashing,
- dictionaries.
---
# Phase 9 — Recent Transactions

Topics:

- slicing.

Learning:

- list indexing.
---
# Phase 10 — Weekly Analytics

Topics:

- spending trends,
- rolling calculations.

Learning:

- sliding window.
---
# Phase 11 — Budget Warning System

Topics:

- budget comparison,
- alert logic.

Learning:

- conditional logic.
---
# Phase 12 — Save Data using JSON

Topics:

- json.dump()

Learning:

- file handling,
- persistence.
---
# Phase 13 — Load Data from JSON

Topics:

- json.load()

Learning:

- data restoration.
---
# Phase 14 — Menu-Based CLI Application

Topics:

- infinite loop,
- user choices.

Learning:

- application flow.
---
# Phase 15 — Code Refactoring

Topics:

- clean coding,
- reusable functions.

Learning:

- software engineering basics.
---
# Phase 16 — Error Handling

Topics:

- invalid input,
- exception handling.

Learning:

- robust coding.
---
# Phase 17 — UI Improvements

Topics:

- colored terminal,
- emojis,
- formatting.

Learning:

- user experience basics.
---
# Phase 18 — Final Testing

Topics:

- bug fixing,
- testing all features.

Learning:

- debugging.
---
# Phase 19 — GitHub Upload

Topics:

- GitHub repository,
- README writing.

Learning:

- portfolio building.
---
# Phase 20 — Future AI Upgrade Ideas

Possible future upgrades:

- AI spending insights,
- spending prediction,
- chatbot assistant,
- voice expense input,
- ML analytics.

Purpose:

- connect DSA project with AI modules later.
---
# Future AI Integration Ideas

## AI Features Later

- AI financial advisor
- Spending prediction
- Expense chatbot
- Smart recommendations
- Voice assistant

This helps students understand:

- DSA + AI integration.