# Module 08 – Lab 02
# Building a GitHub Copilot Extension with a Custom Knowledge Base and Evaluating with RAGAS

> **Module:** M8 – RAG · Text2SQL · CI/CD Integration  
> **Duration:** 90 Minutes  
> **Difficulty:** Advanced

---

# Introduction

Enterprise AI assistants become significantly more useful when they can answer questions using an organization's own documentation instead of relying only on a foundation model.

This lab introduces **Retrieval-Augmented Generation (RAG)** using a **GitHub Copilot Extension** backed by a custom Knowledge Base (KB). You will then reuse the **RAGAS evaluation harness** created in **Module 7** to measure **Faithfulness** before and after improving the knowledge base.

This lab demonstrates the complete **Evaluation-Driven Development (EDD)** cycle:

```text
Create Knowledge Base
        │
        ▼
Build Copilot Extension
        │
        ▼
Ask Questions
        │
        ▼
Run RAGAS Evaluation
        │
        ▼
Improve KB
        │
        ▼
Run Evaluation Again
```

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain how GitHub Copilot Extensions enable enterprise RAG.
- Build a Copilot Extension using a custom knowledge base.
- Query enterprise documentation from GitHub Copilot Chat.
- Reuse the RAGAS evaluation harness from Module 7.
- Measure Faithfulness before and after tuning the knowledge base.

---

# Background Concepts

## Retrieval-Augmented Generation (RAG)

A RAG application combines:

- Knowledge Base
- Retriever
- Large Language Model
- Generated Response

Instead of relying only on model knowledge, relevant documents are retrieved and used as grounding context.

---

## Knowledge Base Quality

High-quality RAG depends on:

- Coverage
- Accuracy
- Freshness
- Chunking strategy
- Metadata quality
- Refresh cadence

Poor KB quality leads to hallucinations and lower faithfulness scores.

---

## Enterprise Scenario

Contoso Retail wants an internal AI assistant that answers employee questions about:

- HR policies
- Leave policy
- Travel policy
- Security standards
- IT support procedures

The assistant should answer only from approved company documentation.

---

# Solution Architecture

```text
GitHub Copilot Chat
          │
          ▼
 GitHub Copilot Extension
          │
          ▼
Enterprise Knowledge Base
          │
          ▼
Vector Search
          │
          ▼
Retrieved Context
          │
          ▼
LLM Response
          │
          ▼
RAGAS Evaluation
```

---

# Prerequisites

- GitHub Copilot
- GitHub Codespaces or VS Code
- Sample enterprise documents
- RAGAS evaluation harness from Module 7
- Python environment

---

# Exercise 1 – Create a Custom Knowledge Base

Create a knowledge base containing documents such as:

- Employee Handbook
- Leave Policy
- Expense Policy
- Security Guidelines
- IT Support Guide

Verify that the documents are indexed and available for retrieval.

> 📷 Screenshot: Knowledge base created.

---

# Exercise 2 – Build the GitHub Copilot Extension

Create a GitHub Copilot Extension that can retrieve information from the custom knowledge base.

Validate that users can ask questions such as:

```text
What is the annual leave policy?
```

and receive answers grounded in enterprise documentation.

> 📷 Screenshot: Extension responding from the knowledge base.

---

# Exercise 3 – Run the Baseline RAGAS Evaluation

Reuse the evaluation dataset and harness from **Module 7 – Lab 2**.

Run:

```bash
python evaluate_rag.py
```

Record the Faithfulness score.

Example:

```text
Faithfulness : 0.78
```

Document observations:

- Missing context
- Hallucinations
- Incomplete answers

---

# Exercise 4 – Improve the Knowledge Base

Tune the RAG solution by:

- Adding missing documents
- Improving document chunking
- Updating stale content
- Improving metadata
- Expanding coverage

Run the evaluation again.

Example:

```text
Before Tuning : 0.78
After Tuning  : 0.93
```

Compare the results.

---

# Exercise 5 – Analyze the Improvement

Complete the comparison table.

| Metric | Before | After |
|--------|-------:|------:|
| Faithfulness | | |
| Answer Relevancy | | |
| Context Precision | | |
| Context Recall | | |

Discuss:

- Which tuning change had the greatest impact?
- Which questions still need improvement?
- What additional documents should be added?

---

# Validation Checklist

- [ ] Knowledge base created.
- [ ] Copilot Extension configured.
- [ ] Enterprise questions answered successfully.
- [ ] RAGAS evaluation executed.
- [ ] Faithfulness improved after tuning.

---

# Challenge Exercise

Extend the knowledge base with:

- Product documentation
- Release notes
- API documentation
- Troubleshooting guides

Measure the effect on:

- Faithfulness
- Answer Relevancy
- Context Precision
- Context Recall

---

# Best Practices

- Continuously refresh the knowledge base.
- Keep documents version controlled.
- Evaluate after every significant KB update.
- Use representative enterprise questions.
- Track RAGAS metrics over time.

---

# Knowledge Check

1. Why is Faithfulness a key RAG metric?
2. How does a knowledge base affect answer quality?
3. Why should RAGAS evaluations be rerun after KB updates?
4. Which knowledge base improvements typically increase Faithfulness?

---

# Summary

| Concept | Outcome |
|---------|---------|
| GitHub Copilot Extension | Enterprise AI interface |
| Custom Knowledge Base | Provides grounded context |
| RAGAS | Measures RAG quality |
| Faithfulness | Indicates grounding in retrieved content |
| EDD | Validate before releasing AI features |

---

# Looking Ahead

In **Lab 3**, you will build a **Text2SQL** solution, generate SQL from natural language, execute the queries against PostgreSQL, and evaluate SQL correctness using the evaluation techniques introduced in Module 7.
