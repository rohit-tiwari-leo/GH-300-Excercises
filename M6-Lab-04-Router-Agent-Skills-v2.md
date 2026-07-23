# Module 06 – Lab 04
# Wrapping a RAG Pipeline and Text2SQL Tool as Reusable Skills for a Router Agent

> **Module:** M6 – Reusable Skills and Repository Instructions
> **Duration:** 75–90 Minutes
> **Difficulty:** Advanced

---

# Introduction

Enterprise AI applications orchestrate multiple specialized capabilities rather than relying on a single workflow. A **Router Agent** determines which capability should handle a user's request based on its intent.

In this lab, you will package a **RAG** workflow and a **Text2SQL** workflow as reusable GitHub Copilot Skills. You will then create a **Router Agent configuration** that documents routing rules. In **Module 9**, these rules will be implemented by an actual Router Agent.

---

# Learning Objectives

- Explain intent-based routing.
- Create reusable Skills for RAG and Text2SQL.
- Define routing policies for specialized Skills.
- Validate routing decisions using GitHub Copilot Chat.
- Prepare reusable Skills for orchestration in Module 9.

---

# Why a Router Agent?

```text
                    User Request
                         │
                         ▼
                  Intent Classification
                         │
                         ▼
                   Router Agent
         ┌──────────────┴──────────────┐
         ▼                             ▼
 Enterprise RAG Skill         Enterprise Text2SQL Skill
         │                             │
         └──────────────┬──────────────┘
                        ▼
                  Final Response
```

---

# Repository Structure

```text
OrderManagement/
└── .github/
    ├── skills/
    │   ├── rag-assistant/
    │   │   └── SKILL.md
    │   └── text2sql/
    │       └── SKILL.md
    └── router/
        └── router-agent.md
```

---

# Exercise 1 – Create the Enterprise RAG Skill

Create:

```text
.github/skills/rag-assistant/SKILL.md
```

Include:
- Purpose
- When to Use
- Retrieval instructions
- Source citation guidance
- Output format

---

# Exercise 2 – Create the Enterprise Text2SQL Skill

Create:

```text
.github/skills/text2sql/SKILL.md
```

Include:
- Purpose
- SQL generation rules
- Safety constraints
- Explanation requirements
- Output format

---

# Exercise 3 – Create the Router Configuration

Create:

```text
.github/router/router-agent.md
```

Add the following:

````markdown
# Router Agent Configuration

## Purpose

Route enterprise requests to the most appropriate reusable Skill.

## Routing Rules

### Enterprise RAG Skill

Use when requests involve:

- Company policies
- Product documentation
- HR procedures
- Knowledge base articles
- User manuals
- FAQs

### Enterprise Text2SQL Skill

Use when requests involve:

- Revenue
- Sales
- Orders
- Inventory
- SQL
- Reports
- Customer analytics

## Priority Rules

- Documentation questions → Enterprise RAG Skill
- Structured business data → Enterprise Text2SQL Skill
- If both are required, retrieve documentation first and then generate SQL.

## Router Output

Return:
- Selected Skill
- Reason for Selection
- Confidence Level
````

---

# Exercise 4 – Validate the Routing Rules

## Prompt 1

```text
What is the company's annual leave policy?
```

Expected:

```text
Selected Skill: Enterprise RAG
Reason: Company policy request
Confidence: High
```

## Prompt 2

```text
Show total sales by region for the previous quarter.
```

Expected:

```text
Selected Skill: Enterprise Text2SQL
Reason: Business analytics request
Confidence: High
```

## Prompt 3

```text
Explain the warranty replacement process.
```

Expected:

Enterprise RAG

## Prompt 4

```text
Generate a SQL query showing the top ten customers by revenue.
```

Expected:

Enterprise Text2SQL

---

# Validation Checklist

- [ ] RAG Skill created.
- [ ] Text2SQL Skill created.
- [ ] Router configuration created.
- [ ] Routing rules documented.
- [ ] Copilot responses match expected routing.

---

# Challenge Exercise

Extend the Router configuration to support:

- Code Review
- API Generation
- Security Review
- Documentation Assistant
- Test Case Generator

---

# Looking Ahead

In this lab you manually documented routing rules. In **Module 9**, you will replace this Markdown configuration with a true Router Agent that dynamically selects and invokes the appropriate Skill.

---

# Summary

| Concept | Outcome |
|---------|---------|
| RAG Skill | Enterprise knowledge retrieval |
| Text2SQL Skill | Natural language to SQL |
| Router Configuration | Intent-based routing policy |
| Module 9 | Dynamic Router Agent implementation |
