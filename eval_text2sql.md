# Lab 3: Evaluate Text-to-SQL Generation Using GitHub Copilot

## Objective

In this lab, you will evaluate GitHub Copilot's ability to generate SQL queries from a natural language request (Text2SQL). You will provide the database schema as context, generate SQL using GitHub Copilot, define the expected SQL (golden answer), create a SQL correctness evaluation using Promptfoo, run the evaluation, and compare the generated SQL with the expected SQL.

**Estimated Duration:** 20 minutes

---

# Learning Outcomes

By the end of this lab, you will be able to:

- Provide database schema as context for Text2SQL
- Write a Text2SQL prompt
- Generate SQL using GitHub Copilot
- Define the expected SQL (golden answer)
- Create a SQL correctness evaluation
- Run the evaluation using Promptfoo
- Compare Copilot SQL with the expected SQL
- Interpret the evaluation results

---

# Prerequisites

Before starting, ensure you have:

- Visual Studio Code
- GitHub Copilot enabled
- Node.js installed
- Promptfoo installed

Install Promptfoo if it is not already installed:

```bash
npm install -g promptfoo
```

---

# Lab Scenario

Your organization is building an AI-powered reporting assistant that converts natural language questions into SQL queries. To ensure the generated SQL is accurate, you will provide the database schema as context and automatically evaluate the generated SQL against an expected (golden) SQL query.

---

# Step 1: Create the Project

Create a new folder for the lab.

```text
text2sql-eval/
│
├── prompts.txt
└── promptfooconfig.yaml
```

---

# Step 2: Define the Database Schema

Instead of connecting to a real database, provide the schema as context in the prompt.

Open **prompts.txt** and add the following:

```text
You are an SQL assistant.

Database Schema

Table: Employees

Columns:
- EmployeeID (INT)
- Name (VARCHAR)
- Department (VARCHAR)
- Salary (DECIMAL)

Task:
Generate a SQL query to retrieve the names of employees who work in the IT department.

Return only the SQL query.
```

The schema helps GitHub Copilot understand the available tables and columns before generating the SQL query.

---

# Step 3: Generate SQL Using GitHub Copilot

1. Open **prompts.txt** in Visual Studio Code.
2. Place the cursor after the prompt.
3. Invoke GitHub Copilot Chat or inline completion.
4. Ask Copilot to generate the SQL query.

An example response is shown below.

```sql
SELECT Name
FROM Employees
WHERE Department = 'IT';
```

---

# Step 4: Define the Expected SQL (Golden Answer)

The expected SQL for this business request is:

```sql
SELECT Name
FROM Employees
WHERE Department = 'IT';
```

This SQL is the **golden answer** used to evaluate Copilot's generated SQL.

---

# Step 5: Create the SQL Correctness Evaluation

Create a file named **promptfooconfig.yaml**.

Add the following configuration:

```yaml
description: Text2SQL SQL Correctness Evaluation

prompts:
  - file://prompts.txt

providers:
  - id: github:copilot

tests:
  - description: Retrieve IT employee names

    assert:
      - type: contains
        value: "SELECT Name"

      - type: contains
        value: "FROM Employees"

      - type: contains
        value: "WHERE Department = 'IT'"
```

### Evaluation Criteria

The generated SQL should:

- Select the **Name** column
- Read data from the **Employees** table
- Filter employees whose department is **IT**

---

# Step 6: Run the Evaluation

Open a terminal in the project folder.

Execute:

```bash
promptfoo eval
```

Example output:

```text
Running 1 test...

Prompt:
Generate a SQL query to retrieve the names of employees who work in the IT department.

Provider:
GitHub Copilot

Assertions

✓ contains "SELECT Name"
✓ contains "FROM Employees"
✓ contains "WHERE Department = 'IT'"

PASS
```

---

# Step 7: Compare Copilot SQL vs Expected SQL

### Expected SQL

```sql
SELECT Name
FROM Employees
WHERE Department = 'IT';
```

### Copilot SQL (Correct)

```sql
SELECT Name
FROM Employees
WHERE Department = 'IT';
```

### Evaluation

| Evaluation Check | Result |
|------------------|--------|
| Correct SELECT clause | ✅ |
| Correct table | ✅ |
| Correct WHERE clause | ✅ |

**Overall Result:** ✅ PASS

---

### Copilot SQL (Incorrect Example)

```sql
SELECT *
FROM Employees;
```

### Evaluation

| Evaluation Check | Result |
|------------------|--------|
| Correct SELECT clause | ❌ |
| Correct table | ✅ |
| Correct WHERE clause | ❌ |

**Overall Result:** ❌ FAIL

---

# Step 8: Interpret the Results

Use the following table to interpret the evaluation.

| Evaluation Result | Interpretation |
|-------------------|----------------|
| All assertions pass | ✅ SQL matches the expected query |
| Missing SELECT column | ❌ Incorrect SQL |
| Wrong table | ❌ Incorrect SQL |
| Missing WHERE clause | ❌ Incorrect SQL |
| Incorrect filter condition | ❌ Incorrect SQL |

---

# Expected Workflow

```text
Define Database Schema
          │
          ▼
Write Text2SQL Prompt
          │
          ▼
Generate SQL using GitHub Copilot
          │
          ▼
Define Expected SQL (Golden Answer)
          │
          ▼
Create SQL Correctness Evaluation
          │
          ▼
Run promptfoo eval
          │
          ▼
Compare Copilot SQL vs Expected SQL
          │
          ▼
Interpret PASS / FAIL Results
```

---

# Lab Summary

In this lab, you provided a database schema as context for a Text2SQL prompt, generated SQL using GitHub Copilot, defined an expected SQL (golden answer), created a SQL correctness evaluation using Promptfoo, ran the evaluation, and compared the generated SQL with the expected SQL. This demonstrates how Evaluation-Driven Development (EDD) can be used to automatically validate AI-generated SQL before it is used in production applications.
