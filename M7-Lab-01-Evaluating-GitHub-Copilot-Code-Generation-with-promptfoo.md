# Module 07 – Lab 01
# Evaluating GitHub Copilot Code Generation using promptfoo

> **Module:** M7 – Evaluation-Driven Development (EDD)  
> **Duration:** 60 Minutes  
> **Difficulty:** Intermediate

---

# Introduction

Traditional software testing verifies deterministic code. AI-generated code is **non-deterministic**, meaning the same prompt can produce different outputs over time as models, prompts, or context evolve.

**Evaluation-Driven Development (EDD)** addresses this by defining evaluation criteria **before** building or refining an AI solution.

> **EDD Principle:** Write the evaluation first, then build or improve the AI system until it consistently passes.

In this lab, you will use **promptfoo** to evaluate a GitHub Copilot code-generation prompt, define pass/fail criteria, execute the evaluation, and interpret the results.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain Evaluation-Driven Development (EDD).
- Understand why AI applications require automated evaluations.
- Create a `promptfoo` evaluation configuration.
- Define assertions and pass/fail criteria.
- Execute evaluations.
- Interpret evaluation reports.
- Improve prompts based on evaluation results.

---

# Background Concepts

## Why AI Systems Need Evaluations

Unlike traditional software, AI systems can suffer from:

- Non-deterministic responses
- Hallucinations
- Prompt regressions
- Model drift
- Context sensitivity

Evaluations provide measurable quality checks before AI features reach production.

---

## What is promptfoo?

**promptfoo** is an open-source framework for evaluating prompts and LLM applications.

It enables you to:

- Compare prompts
- Define expected behavior
- Create regression tests
- Automate AI quality checks
- Integrate evaluations into CI/CD pipelines

---

## Evaluation Workflow

```text
Write Evaluation
        │
        ▼
Execute Prompt
        │
        ▼
Compare Output
        │
        ▼
PASS / FAIL
        │
        ▼
Improve Prompt
```

---

## Common Assertion Types

- Contains expected text
- JSON validity
- Regex match
- Similarity scoring
- LLM rubric evaluation
- JavaScript assertions

---

# Enterprise Scenario

Contoso Retail is using GitHub Copilot to generate REST API controllers.

The architecture team wants every generated controller to:

- Validate input
- Return proper HTTP status codes
- Include exception handling
- Use asynchronous programming
- Generate XML documentation

Before developers rely on Copilot-generated code, the prompt must pass an automated evaluation.

---

# Prerequisites

- Visual Studio Code
- Node.js (LTS)
- GitHub Copilot
- Git installed

---

# Exercise 1 – Install promptfoo

```bash
npm install -g promptfoo
```

Verify the installation:

```bash
promptfoo --version
```

> 📷 **Screenshot:** Successful installation.

---

# Exercise 2 – Create the Evaluation Configuration

Create a file named:

```text
promptfooconfig.yaml
```

Example:

```yaml
description: GitHub Copilot Code Generation Evaluation

prompts:
  - |
    Generate an ASP.NET Core Web API controller for managing customers.

providers:
  - openai:gpt-4.1

tests:
  - vars: {}
    assert:
      - type: contains
        value: HttpGet
      - type: contains
        value: async
      - type: contains
        value: IActionResult
      - type: contains
        value: try
```

> 📷 **Screenshot:** Completed configuration file.

---

# Exercise 3 – Define Pass/Fail Criteria

The evaluation should pass only if:

- Controller contains HTTP endpoints.
- Uses asynchronous methods.
- Returns `IActionResult`.
- Includes exception handling.
- Does not contain TODO placeholders.

Example additional assertion:

```yaml
- type: not-contains
  value: TODO
```

---

# Exercise 4 – Run the Evaluation

Execute:

```bash
promptfoo eval
```

Sample output:

```text
Tests: 5
Passed: 4
Failed: 1

Pass Rate: 80%
```

> 📷 **Screenshot:** promptfoo evaluation report.

---

# Exercise 5 – Interpret the Results

Review the report and identify:

- Which assertion failed?
- Was the failure caused by the prompt or generated code?
- How could the prompt be improved?

Modify the prompt to explicitly request:

- XML documentation
- Proper exception handling
- Async methods
- Input validation

Re-run the evaluation and compare the results.

---

# Validation Checklist

- [ ] promptfoo installed successfully.
- [ ] Evaluation configuration created.
- [ ] Pass/fail criteria defined.
- [ ] Evaluation executed.
- [ ] Report interpreted.
- [ ] Prompt refined based on results.

---

# Challenge Exercise

Extend the evaluation to verify:

- Dependency Injection
- Logging
- Authorization attributes
- Model validation
- Swagger annotations

Run the evaluation again and compare the pass rate.

---

# Best Practices

- Write evaluations before refining prompts.
- Keep assertions focused and measurable.
- Maintain evaluation datasets in source control.
- Treat evaluation failures like failing unit tests.
- Automate evaluations in CI/CD pipelines.

---

# Knowledge Check

1. Why is Evaluation-Driven Development important for AI applications?
2. What problem does promptfoo solve?
3. Why should pass/fail criteria be defined before prompt optimization?
4. How can promptfoo help prevent regressions?

---

# Summary

| Concept | Outcome |
|---------|---------|
| EDD | Test AI before deployment |
| promptfoo | Automated prompt evaluation |
| Assertions | Define measurable quality |
| Pass Rate | Quantify AI performance |
| Regression Testing | Prevent quality degradation |

---

# Looking Ahead

In **Lab 2**, you will evaluate a Retrieval-Augmented Generation (RAG) system using **RAGAS**, applying the same Evaluation-Driven Development principles to measure **faithfulness**, **groundedness**, and **answer quality**.

