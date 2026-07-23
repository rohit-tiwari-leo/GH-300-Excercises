
# Module 09 – Lab 03
# Build a Router Agent for Intelligent Tool Selection

> **Module:** M9 – Agentic AI Workflows with GitHub Copilot
>
> **Duration:** 90–120 Minutes
>
> **Difficulty:** Advanced

---

# Introduction

Modern AI applications rarely rely on a single model or capability. Instead, an **Agent** determines the user's intent and routes the request to the most appropriate tool.

In this lab, you will build a **Router Agent** that classifies a natural language request and invokes either the **RAG Skill** or the **Text2SQL Skill** created in earlier modules. The Router Agent will use the **SKILL.md** files from Module 6 as the tool interface.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain the role of a Router Agent.
- Reuse SKILL.md as tool definitions.
- Classify natural language queries.
- Route requests to the correct AI capability.
- Return grounded answers.
- Prepare the solution for automated evaluation in Module 7.

---

# Repository

```text
Repository:
eShopOnWebITC
```

---

# Prerequisites

- Module 6 completed (SKILL.md files)
- Module 7 completed (Evaluation Harness)
- Module 8 completed (RAG and Text2SQL)
- GitHub Copilot
- VS Code or GitHub Codespaces

---

# Enterprise Scenario

The eShopOnWebITC AI Assistant supports two capabilities:

### RAG Skill

Answers documentation and policy questions.

Examples:

- What is the return policy?
- Explain the application architecture.
- How does the shipping process work?

### Text2SQL Skill

Answers reporting and analytics questions.

Examples:

- Show the top 10 products by revenue.
- Monthly sales by category.
- Orders awaiting shipment.

The Router Agent must automatically select the correct capability.

---

# Solution Architecture

```text
User Question
      │
      ▼
 Router Agent
      │
      ├───────────────┐
      ▼               ▼
RAG SKILL.md     Text2SQL SKILL.md
      │               │
      ▼               ▼
 Knowledge Base    PostgreSQL
      │               │
      └──────┬────────┘
             ▼
      Grounded Response
```

---

# Suggested Repository Structure

```text
.github/

├── skills/
│   ├── rag/
│   │     SKILL.md
│   ├── text2sql/
│   │     SKILL.md
│   └── router/
│         router-agent.md

src/

evaluations/

docs/
```

---

# Exercise 1 – Review the Available Skills

Open:

```text
.github/skills/rag/SKILL.md
```

Review:

- Purpose
- Inputs
- Outputs
- Examples
- Limitations

Repeat for:

```text
.github/skills/text2sql/SKILL.md
```

Discuss:

How does the Router Agent decide which skill to invoke?

---

# Exercise 2 – Create the Router Agent

Create:

```text
.github/router/router-agent.md
```

Define:

- Purpose
- Available Skills
- Routing Logic
- Priority Rules
- Fallback Behavior

Suggested routing rules:

| User Intent | Skill |
|-------------|-------|
| Product policy | RAG |
| Documentation | RAG |
| Architecture | RAG |
| Sales analytics | Text2SQL |
| Revenue reports | Text2SQL |
| Inventory reporting | Text2SQL |

---

# Exercise 3 – Test Query Classification

Test the Router Agent with the following prompts:

### RAG

- What is the product return policy?
- Explain the shipping workflow.
- How is authentication implemented?

### Text2SQL

- Show top 10 products by revenue.
- Monthly sales report.
- Customers with highest spending.

Record:

- Selected Skill
- Reason for Routing
- Response Quality

---

# Exercise 4 – Return a Grounded Response

Verify that:

For RAG:

- Retrieved documents are used.
- Citations are available.
- No hallucinations are introduced.

For Text2SQL:

- SQL is generated.
- SQL executes successfully.
- Results are returned.
- No unsupported SQL is produced.

---

# Exercise 5 – Handle Ambiguous Requests

Examples:

- Which products are returned most frequently?
- Explain monthly revenue trends.
- What products are eligible for free shipping?

Determine:

- Which skill should be selected?
- Should the Router Agent ask a clarification question?
- Can multiple skills be combined?

Document your decision.

---

# Exercise 6 – Prepare for Automated Evaluation

Store routing examples in:

```text
evaluations/router/
```

Create a dataset containing:

- User Question
- Expected Skill
- Actual Skill
- Expected Result

This dataset will be used in Lab 4 for automated evaluation.

---

# Validation Checklist

- [ ] SKILL.md files reused
- [ ] Router Agent created
- [ ] Queries correctly classified
- [ ] Correct skill invoked
- [ ] Grounded responses returned
- [ ] Evaluation dataset prepared

---

# Challenge Exercise

Extend the Router Agent by adding another skill:

Examples:

- Inventory Forecasting
- Product Recommendation
- Documentation Search
- Code Generation

Update the routing rules and validate the new capability.

---

# Best Practices

- Keep each skill focused on a single responsibility.
- Make routing rules explicit.
- Ask clarification questions when intent is ambiguous.
- Log routing decisions.
- Evaluate routing accuracy continuously.

---

# Knowledge Check

1. What is the role of a Router Agent?
2. Why are SKILL.md files used as tool interfaces?
3. When should the Router Agent ask for clarification?
4. Why should routing decisions be evaluated?

---

# Summary

In this lab, you built a Router Agent that classifies natural language requests, selects the appropriate reusable skill, and returns grounded responses. This demonstrates how multiple AI capabilities can be orchestrated into a single intelligent assistant.

---

# Looking Ahead

In Lab 4, you will automate the evaluation of the Router Agent using GitHub Actions. Pull Requests will be blocked if routing accuracy, tool-call success, or overall evaluation scores fall below the required threshold.
