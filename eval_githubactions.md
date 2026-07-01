# Lab 2: Add a GitHub Actions Evaluation Gate Using Promptfoo

## Objective

In this lab, you will learn how to automate AI evaluation in a GitHub Actions workflow. The workflow will run Promptfoo evaluations whenever a Pull Request (PR) is opened or updated. If the evaluation pass rate is below **80%**, the workflow fails, preventing the PR from being merged.

**Estimated Duration:** 20 minutes

---

# Prerequisites

Before starting, ensure you have:

- A GitHub repository
- GitHub Copilot access
- Promptfoo evaluation created (Lab 1)
- GitHub Actions enabled in your repository

---

# Lab Scenario

Your development team uses GitHub Copilot to generate code.

To ensure code quality, every Pull Request should automatically run Promptfoo evaluations. If fewer than **80%** of the evaluation tests pass, the PR should fail until the issues are fixed.

---

# Step 1: Create the GitHub Actions Workflow

Inside your repository, create the following folder structure.

```text
.github/
└── workflows/
    └── promptfoo-eval.yml
```

---

# Step 2: Create the Workflow File

Open **.github/workflows/promptfoo-eval.yml** and add the following:

```yaml
name: Promptfoo Evaluation Gate

on:
  pull_request:

jobs:
  evaluate:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install Promptfoo
        run: npm install -g promptfoo

      - name: Run Promptfoo Evaluation
        run: promptfoo eval --max-failures 20
```

---

# Step 3: Configure the Evaluation Threshold

Update your **promptfooconfig.yaml** to specify the minimum pass rate.

```yaml
description: GitHub Copilot Evaluation

prompts:
  - file://prompts.txt

providers:
  - id: github:copilot

defaultTest:
  options:
    threshold: 0.8

tests:
  - assert:
      - type: contains
        value: "def reverse_string"

      - type: contains
        value: "[::-1]"
```

**What does `threshold: 0.8` mean?**

- At least **80%** of the evaluation tests must pass.
- If the pass rate is below **80%**, Promptfoo exits with a failure status.
- GitHub Actions marks the workflow as failed.
- The Pull Request cannot be merged (if branch protection rules require the workflow to pass).

---

# Step 4: Commit and Push

Commit your changes.

```bash
git add .
git commit -m "Add Promptfoo evaluation gate"
git push
```

---

# Step 5: Create a Pull Request

Open a Pull Request in GitHub.

GitHub Actions automatically starts the workflow.

Example:

```text
Pull Request Created

↓

GitHub Actions Triggered

↓

Promptfoo Evaluation Runs

↓

Pass Rate Calculated
```

---

# Step 6: Successful Evaluation

Suppose Promptfoo reports:

```text
Tests Passed : 8

Tests Failed : 2

Pass Rate : 80%
```

Since the pass rate is **80%**, the workflow succeeds.

Example output:

```text
✓ Promptfoo Evaluation Passed

Workflow Status:
SUCCESS
```

The Pull Request can now be merged.

---

# Step 7: Failed Evaluation

Suppose Promptfoo reports:

```text
Tests Passed : 6

Tests Failed : 4

Pass Rate : 60%
```

Since the pass rate is below **80%**, the workflow fails.

Example output:

```text
✗ Promptfoo Evaluation Failed

Workflow Status:
FAILED
```

The Pull Request remains blocked until the evaluation issues are resolved.

---

# Understanding the Evaluation Gate

| Pass Rate | Workflow Status | PR Status |
|-----------|-----------------|-----------|
| 100% | ✅ Success | Merge Allowed |
| 90% | ✅ Success | Merge Allowed |
| 80% | ✅ Success | Merge Allowed |
| 79% | ❌ Failed | Merge Blocked |
| 60% | ❌ Failed | Merge Blocked |

---

# Expected Workflow

```text
Developer Opens Pull Request
            │
            ▼
 GitHub Actions Starts
            │
            ▼
 Promptfoo Evaluates AI Outputs
            │
            ▼
 Pass Rate ≥ 80% ?
      │             │
     Yes           No
      │             │
      ▼             ▼
Workflow Passes   Workflow Fails
      │             │
      ▼             ▼
PR Can Merge     PR Blocked
```

---

# Lab Summary

In this lab, you:

- Created a GitHub Actions workflow.
- Automated Promptfoo evaluations for every Pull Request.
- Configured an evaluation gate with an **80% pass-rate threshold**.
- Learned how evaluation gates help enforce AI-generated code quality before merging changes.

This is a practical example of **Evaluation-Driven Development (EDD)**, where AI-generated outputs are automatically validated in the CI/CD pipeline, ensuring only high-quality code is merged into the main branch.
