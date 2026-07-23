# Module 07 – Lab 04
# Automating AI Evaluation with GitHub Actions

> **Module:** M7 – Evaluation-Driven Development (EDD)  
> **Duration:** 60–75 Minutes  
> **Difficulty:** Intermediate

---

# Introduction

Modern AI applications should automatically validate prompts and AI outputs before code is merged. By integrating evaluation into a CI/CD pipeline, organizations can prevent regressions and maintain consistent AI quality.

In this lab, you will configure a **GitHub Actions** workflow that runs **promptfoo** evaluations on every Pull Request and blocks the merge when the evaluation **pass rate is below 80%**.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain AI quality gates in CI/CD.
- Create a GitHub Actions workflow for AI evaluation.
- Execute promptfoo automatically.
- Configure pass/fail thresholds.
- Prevent Pull Requests from being merged when evaluation scores are too low.

---

# Background Concepts

## Why AI Evaluation Gates?

Traditional CI validates source code.

AI-enabled CI validates:

- Prompt quality
- LLM responses
- Regression tests
- Evaluation metrics
- Pass-rate thresholds

---

# Enterprise Scenario

Contoso Retail requires every Pull Request containing prompt changes to pass automated AI evaluations before merging into the `main` branch.

Quality policy:

- Pass Rate **≥ 80%** → PR may proceed.
- Pass Rate **< 80%** → PR is blocked.

---

# Workflow

```text
Developer
   │
   ▼
Pull Request
   │
   ▼
GitHub Actions
   │
   ▼
promptfoo eval
   │
   ▼
Pass Rate >= 80% ?
   │
 ┌─┴─────────────┐
 ▼               ▼
PASS          FAIL
Merge         Block PR
```

---

# Prerequisites

- GitHub repository
- GitHub Codespaces or VS Code
- GitHub Copilot
- promptfoo installed
- Existing `promptfooconfig.yaml`

---

# Exercise 1 – Create the Workflow

Create:

```text
.github/workflows/ai-evaluation.yml
```

---

# Exercise 2 – Configure GitHub Actions

Use GitHub Copilot to generate a workflow that:

- Runs on Pull Requests
- Installs Node.js
- Installs promptfoo
- Executes `promptfoo eval`

Example prompt:

```text
Generate a GitHub Actions workflow that runs promptfoo evaluation for every pull request.
```

---

# Exercise 3 – Configure the Evaluation Gate

Update the workflow so the job fails when the pass rate is below 80%.

Example logic:

```bash
promptfoo eval

if [ "$PASS_RATE" -lt 80 ]; then
  exit 1
fi
```

> 📷 Screenshot: Workflow with evaluation gate.

---

# Exercise 4 – Test the Workflow

Create a feature branch.

Modify a prompt so at least one evaluation fails.

Commit and push the changes.

Create a Pull Request.

Observe the GitHub Actions workflow.

Expected result:

```text
Pass Rate : 60%

Workflow Status : Failed

Pull Request : Blocked
```

---

# Exercise 5 – Fix and Re-run

Improve the prompt until the evaluation succeeds.

Re-run the workflow.

Expected result:

```text
Pass Rate : 100%

Workflow Status : Success

Pull Request : Ready for Review
```

---

# Validation Checklist

- [ ] Workflow created.
- [ ] promptfoo executes automatically.
- [ ] Threshold configured.
- [ ] PR blocked when pass rate is below 80%.
- [ ] Successful run after prompt improvements.

---

# Challenge Exercise

Enhance the workflow to:

- Publish evaluation reports as workflow artifacts.
- Execute RAGAS evaluations.
- Execute Text2SQL evaluations.
- Post evaluation summaries to the Pull Request.

---

# Best Practices

- Treat AI evaluation failures like failing unit tests.
- Keep evaluation datasets under version control.
- Use the same evaluation pipeline locally and in CI.
- Gradually tighten thresholds as quality improves.
- Automate every prompt change.

---

# Knowledge Check

1. Why should AI evaluations run during Pull Requests?
2. What happens when the pass rate falls below the configured threshold?
3. How do GitHub Actions support Evaluation-Driven Development?
4. Why should evaluation datasets be version-controlled?

---

# Summary

| Concept | Outcome |
|---------|---------|
| GitHub Actions | Automates AI evaluations |
| AI Quality Gate | Blocks low-quality changes |
| promptfoo | Executes prompt evaluations |
| Pass Threshold | Prevents regressions |
| EDD | Continuous AI quality assurance |

---

# Looking Ahead

In **Module 8**, the same GitHub Actions workflow can be extended to evaluate complete **RAG** and **Text2SQL** applications, providing continuous validation throughout the AI development lifecycle.
