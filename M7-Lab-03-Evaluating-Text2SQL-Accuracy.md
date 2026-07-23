# Module 07 – Lab 03
# Evaluating Text2SQL Accuracy (Module 8 Preview)

> **Module:** M7 – Evaluation-Driven Development (EDD)  
> **Duration:** 60–75 Minutes  
> **Difficulty:** Intermediate

---

# Introduction

Text2SQL enables users to query databases using natural language. While GitHub Copilot and modern LLMs can generate SQL quickly, correctness cannot be assumed. A query may be syntactically valid yet return incorrect or incomplete results.

In this lab, you will apply **Evaluation-Driven Development (EDD)** to a Text2SQL scenario by defining expected SQL, comparing GitHub Copilot-generated SQL against the expected query, and analyzing the results. This serves as a preview for the complete Text2SQL solution developed in **Module 8**.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain why Text2SQL applications require evaluation.
- Create a SQL evaluation dataset.
- Compare expected and generated SQL.
- Validate SQL correctness.
- Interpret evaluation results and improve prompts.

---

# Background Concepts

## Why Evaluate Text2SQL?

Common failures include:

- Incorrect table selection
- Incorrect JOIN conditions
- Missing filters
- Wrong aggregation
- SQL syntax errors
- Correct syntax but incorrect business logic

---

## SQL Evaluation Metrics

| Metric | Description |
|--------|-------------|
| Syntax Validity | SQL executes without syntax errors |
| Semantic Correctness | Business logic is correct |
| Exact Match | Generated SQL matches the expected SQL |
| Execution Accuracy | Generated SQL returns the expected results |
| Result Match | Output matches the expected dataset |

---

# Enterprise Scenario

Contoso Retail uses GitHub Copilot to assist developers in generating SQL queries for business reporting.

Before deployment, every generated query must be validated against an approved SQL dataset.

---

# Evaluation Workflow

```text
Natural Language Request
          │
          ▼
 GitHub Copilot
          │
          ▼
 Generated SQL
          │
          ▼
Compare with Expected SQL
          │
          ▼
Execute & Validate
          │
          ▼
Evaluation Report
```

---

# Prerequisites

- GitHub Codespaces or Visual Studio Code
- GitHub Copilot
- Sample SQL database (SQLite or SQL Server)
- Basic SQL knowledge

---

# Exercise 1 – Create the Evaluation Dataset

Create a file:

```text
text2sql_eval.json
```

Example:

```json
{
  "question": "Show the top 5 customers by total sales.",
  "expected_sql": "SELECT TOP 5 CustomerName, SUM(TotalAmount) AS TotalSales FROM Orders GROUP BY CustomerName ORDER BY TotalSales DESC;"
}
```

Add at least five business reporting scenarios.

---

# Exercise 2 – Generate SQL with GitHub Copilot

Open GitHub Copilot Chat and use the following prompt:

```text
Generate a SQL query to show the top 5 customers by total sales.
```

Save the generated query.

> 📷 **Screenshot:** Copilot-generated SQL.

---

# Exercise 3 – Compare Generated SQL with Expected SQL

Verify:

- Tables
- Columns
- Filters
- JOIN conditions
- Aggregations
- ORDER BY clause

Document any differences.

---

# Exercise 4 – Validate Execution Results

Execute both queries against the sample database.

Compare:

- Number of rows
- Returned values
- Ordering
- Performance

Determine whether both queries produce equivalent business results.

---

# Exercise 5 – Interpret the Evaluation

Identify:

- Was the generated SQL correct?
- Did the SQL execute successfully?
- Did it return the expected business results?
- How could the prompt be improved?

Update the prompt, regenerate SQL, and repeat the evaluation.

---

# Validation Checklist

- [ ] Evaluation dataset created.
- [ ] Expected SQL documented.
- [ ] GitHub Copilot generated SQL.
- [ ] SQL compared and validated.
- [ ] Results interpreted.

---

# Challenge Exercise

Extend the evaluation dataset with scenarios involving:

- Multiple JOINs
- GROUP BY and HAVING
- Window functions
- Date filters
- Nested subqueries

Evaluate each generated query for syntax, semantics, and result accuracy.

---

# Best Practices

- Build representative business datasets.
- Validate business results, not just syntax.
- Use execution-based comparisons whenever possible.
- Store evaluation datasets in source control.
- Re-run evaluations after prompt changes.

---

# Knowledge Check

1. Why is execution accuracy more important than exact SQL matching?
2. What is the difference between syntax validity and semantic correctness?
3. Why should Text2SQL evaluations use real business scenarios?
4. How does EDD improve Text2SQL reliability?

---

# Summary

| Concept | Outcome |
|---------|---------|
| Text2SQL Evaluation | Measures SQL quality before deployment |
| Expected SQL | Defines the evaluation baseline |
| Execution Accuracy | Confirms business correctness |
| EDD | Prevents regressions in AI-generated SQL |

---

# Looking Ahead

In **Module 8**, you will build a complete Text2SQL application. The evaluation dataset and comparison techniques developed in this lab can be reused to validate future prompt and model improvements.
