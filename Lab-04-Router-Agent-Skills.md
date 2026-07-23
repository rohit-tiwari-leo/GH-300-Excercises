# Module 06 -- Lab 04

# Wrapping a RAG Pipeline and Text2SQL Tool as Reusable Skills for a Router Agent

> **Module:** M6 -- Reusable Skills and Repository Instructions\
> **Duration:** 75--90 Minutes\
> **Difficulty:** Advanced

------------------------------------------------------------------------

# Introduction

Enterprise AI applications rarely rely on a single capability. Instead,
they orchestrate multiple specialized components such as
Retrieval-Augmented Generation (RAG), database query tools, APIs, and
business workflows.

Rather than exposing these capabilities directly to users, organizations
use a **Router Agent** to determine which capability should be invoked
based on the user's intent.

In this lab, you will package a **RAG Pipeline** and a **Text2SQL Tool**
as reusable GitHub Copilot Skills and prepare them for use by a Router
Agent introduced in Module 9.

------------------------------------------------------------------------

# Learning Objectives

After completing this lab, you will be able to:

-   Explain the role of specialized Skills in enterprise AI.
-   Understand intent-based routing.
-   Create reusable Skills for a RAG workflow.
-   Create reusable Skills for a Text2SQL workflow.
-   Configure a Router Agent to select the correct Skill.
-   Validate routing behavior using GitHub Copilot Chat.

------------------------------------------------------------------------

# Background Concepts

## Retrieval-Augmented Generation (RAG)

RAG enhances LLM responses by retrieving relevant information from
external knowledge sources before generating an answer.

Typical workflow:

``` text
User Question
      │
      ▼
Vector Search
      │
      ▼
Relevant Documents
      │
      ▼
Large Language Model
      │
      ▼
Grounded Response
```

### Best suited for

-   Knowledge bases
-   Product documentation
-   Internal policies
-   Technical manuals

------------------------------------------------------------------------

## Text2SQL

Text2SQL converts natural language into SQL statements that query
structured relational databases.

Example:

**User**

``` text
Show total sales for last month.
```

Generated SQL

``` sql
SELECT SUM(Total)
FROM Orders
WHERE OrderDate >= DATEADD(month,-1,GETDATE());
```

### Best suited for

-   Reporting
-   Analytics
-   Dashboards
-   Business Intelligence

------------------------------------------------------------------------

## Router Agent

A Router Agent determines which specialized capability should handle a
request.

Example:

``` text
User Question
      │
      ▼
Router Agent
 ┌───────────────┐
 │               │
 ▼               ▼
RAG Skill    Text2SQL Skill
 │               │
 └──────┬────────┘
        ▼
    Final Response
```

Benefits:

-   Better accuracy
-   Modular architecture
-   Easier maintenance
-   Independent evolution of Skills

------------------------------------------------------------------------

# Enterprise Scenario

Contoso Retail provides an AI assistant for internal employees.

The assistant should:

-   Search company policies using RAG.
-   Query sales databases using Text2SQL.
-   Automatically choose the appropriate capability based on user
    intent.

------------------------------------------------------------------------

# Repository Structure

``` text
OrderManagement/

.github/
└── skills/
    ├── rag-assistant/
    │   └── SKILL.md
    └── text2sql/
        └── SKILL.md
```

------------------------------------------------------------------------

# Exercise 1 -- Create the RAG Skill

Create:

``` text
.github/skills/rag-assistant/SKILL.md
```

Example template:

``` markdown
# Enterprise RAG Assistant

## Purpose

Answer questions using enterprise documentation.

## When to Use

- Product documentation
- HR policies
- Knowledge articles
- Technical manuals

## Instructions

Retrieve the most relevant documents before generating a response.

Always cite retrieved information.

State when sufficient evidence cannot be found.

## Output

Summary

Sources

Confidence
```

------------------------------------------------------------------------

# Exercise 2 -- Create the Text2SQL Skill

Create:

``` text
.github/skills/text2sql/SKILL.md
```

Example template:

``` markdown
# Enterprise Text2SQL

## Purpose

Convert natural language into optimized SQL queries.

## Requirements

Generate parameterized SQL.

Avoid destructive statements.

Never execute generated SQL.

Explain the query before returning it.

## Output

Business Interpretation

Generated SQL

Explanation
```

------------------------------------------------------------------------

# Exercise 3 -- Configure the Router Agent

Define routing rules.

  User Intent         Selected Skill
  ------------------- ----------------
  Company policy      RAG
  Product manual      RAG
  Sales report        Text2SQL
  Revenue analysis    Text2SQL
  Database question   Text2SQL

Discuss how intent classification determines the selected Skill.

------------------------------------------------------------------------

# Exercise 4 -- Validate Routing

Test the following prompts.

### Prompt 1

``` text
What is our employee leave policy?
```

Expected:

**RAG Skill**

------------------------------------------------------------------------

### Prompt 2

``` text
Show quarterly revenue by region.
```

Expected:

**Text2SQL Skill**

------------------------------------------------------------------------

### Prompt 3

``` text
Explain the warranty process.
```

Expected:

**RAG Skill**

------------------------------------------------------------------------

### Prompt 4

``` text
List the top 10 customers by annual sales.
```

Expected:

**Text2SQL Skill**

------------------------------------------------------------------------

# Validation Checklist

-   [ ] RAG Skill created.
-   [ ] Text2SQL Skill created.
-   [ ] Router logic documented.
-   [ ] Correct Skill selected for each prompt.
-   [ ] Structured responses generated.

------------------------------------------------------------------------

# Challenge Exercise

Extend the Router Agent with additional Skills:

-   Code Review
-   API Generation
-   Security Review
-   Documentation Assistant
-   Test Case Generator

Design routing rules for each capability.

------------------------------------------------------------------------

# Knowledge Check

1.  Why should RAG and Text2SQL be separate Skills?
2.  What problem does a Router Agent solve?
3.  Which requests should be routed to RAG?
4.  Which requests should be routed to Text2SQL?
5.  Why is modular AI architecture beneficial?

------------------------------------------------------------------------

# Summary

  Concept          Outcome
  ---------------- ----------------------------------------------
  RAG Skill        Grounded responses from enterprise knowledge
  Text2SQL Skill   Natural language to SQL conversion
  Router Agent     Intent-based orchestration
  Benefits         Modular, scalable enterprise AI

------------------------------------------------------------------------

# Key Takeaways

You learned how to package enterprise AI capabilities as reusable Skills
and prepare them for orchestration through a Router Agent. This modular
approach improves maintainability, governance, and scalability while
enabling specialized AI capabilities to work together seamlessly.
