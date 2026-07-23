# Module 08 – Lab 03
# Building and Evaluating a Text2SQL Solution with PostgreSQL

> **Module:** M8 – RAG · Text2SQL · CI/CD Integration  
> **Duration:** 75–90 Minutes  
> **Difficulty:** Advanced

---

# Introduction

Text2SQL allows users to retrieve information from relational databases using natural language. GitHub Copilot can generate SQL from business questions, but the generated queries must be validated before being used in production.

In this lab, you will generate SQL from five natural language questions, execute the queries against a PostgreSQL database, and evaluate the generated SQL using the evaluation techniques introduced in **Module 7**. The goal is to achieve an overall SQL correctness score of **90% or higher**.

---

# Learning Objectives

After completing this lab, you will be able to:

- Generate SQL from natural language using GitHub Copilot.
- Inject schema information into prompts for better SQL generation.
- Execute SQL queries against PostgreSQL.
- Compare generated SQL with expected SQL.
- Measure SQL correctness and execution accuracy.

---

# Background Concepts

## Text2SQL Workflow

```text
Business Question
       │
       ▼
GitHub Copilot
       │
       ▼
Generated SQL
       │
       ▼
PostgreSQL
       │
       ▼
Query Results
       │
       ▼
SQL Evaluation
```

## SQL Evaluation Criteria

- Syntax Validity
- Schema Awareness
- Semantic Correctness
- Execution Accuracy
- Result Match

---

# Enterprise Scenario

Contoso Retail maintains sales data in PostgreSQL. Business users ask questions in natural language while developers use GitHub Copilot to generate SQL. Before deployment, generated SQL must achieve a minimum evaluation score of **90%**.

---

# Prerequisites

- GitHub Codespaces or Visual Studio Code
- GitHub Copilot
- PostgreSQL
- Sample Contoso Retail database
- SQL evaluation dataset from Module 7

---

# Exercise 1 – Explore the Database Schema

Review the tables:

- Customers
- Orders
- OrderItems
- Products
- Employees

Ask GitHub Copilot:

```text
Explain the relationships between these PostgreSQL tables.
```

Identify primary keys, foreign keys, and important business entities.

---

# Exercise 2 – Generate SQL from Natural Language

Create SQL for the following questions:

1. Show the top 5 customers by total sales.
2. List monthly sales for the current year.
3. Show the ten best-selling products.
4. Find customers with no orders in the past six months.
5. Calculate total revenue by product category.

Use GitHub Copilot Chat to generate the SQL.

---

# Exercise 3 – Execute the Queries

Run each generated query against PostgreSQL.

Validate:

- SQL executes successfully.
- Results are returned.
- Output matches the business question.

Document any errors or unexpected results.

---

# Exercise 4 – Evaluate SQL Correctness

Compare each generated query with the expected SQL.

Evaluate:

- Table selection
- JOIN conditions
- Filters
- Aggregations
- ORDER BY
- Returned results

Complete the evaluation table.

| Question | Syntax | Result Match | Score |
|----------|:------:|:------------:|:-----:|
| Q1 | | | |
| Q2 | | | |
| Q3 | | | |
| Q4 | | | |
| Q5 | | | |

Target:

```text
Overall SQL Correctness ≥ 90%
```

---

# Exercise 5 – Improve the Prompt

Refine the prompt by providing additional schema context.

Example:

```text
Use the PostgreSQL schema containing Customers, Orders, OrderItems and Products. Generate an optimized SQL query using INNER JOINs where appropriate.
```

Regenerate the SQL and rerun the evaluation.

Compare the before and after scores.

---

# Validation Checklist

- [ ] Five natural language questions created.
- [ ] SQL generated using GitHub Copilot.
- [ ] Queries executed on PostgreSQL.
- [ ] SQL correctness evaluated.
- [ ] Overall score is at least 90%.

---

# Challenge Exercise

Create five additional questions involving:

- Window functions
- CTEs
- HAVING clauses
- Date calculations
- Multi-table joins

Evaluate the generated SQL using the same process.

---

# Best Practices

- Include schema details in prompts.
- Validate business results, not only syntax.
- Parameterize queries where applicable.
- Avoid SQL injection by using parameters in application code.
- Re-run evaluations whenever prompts or schemas change.

---

# Knowledge Check

1. Why is schema context important for Text2SQL?
2. Why is execution accuracy more valuable than exact SQL matching?
3. What causes incorrect SQL even when syntax is valid?
4. How does Evaluation-Driven Development improve Text2SQL reliability?

---

# Summary

| Concept | Outcome |
|---------|---------|
| Text2SQL | Natural language to SQL |
| Schema Injection | Improves SQL quality |
| PostgreSQL | Executes generated queries |
| SQL Evaluation | Measures correctness and accuracy |
| EDD | Prevents regressions before deployment |

---

# Looking Ahead

In **Lab 4**, you will package the RAG and Text2SQL solutions as reusable **SKILL.md** files so they can be discovered and orchestrated by the Router Agent introduced in Module 9.
