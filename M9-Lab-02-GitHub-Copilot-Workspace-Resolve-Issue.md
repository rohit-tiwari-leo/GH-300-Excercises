
# Module 09 – Lab 02
# GitHub Copilot Workspace – Resolve a GitHub Issue End-to-End

> **Module:** M9 – Agentic AI Workflows with GitHub Copilot
>
> **Duration:** 75–90 Minutes
>
> **Difficulty:** Intermediate–Advanced

---

# Introduction

GitHub Copilot Workspace extends GitHub Copilot from code generation to **end-to-end software delivery**. It helps developers understand an issue, create an implementation plan, propose code changes, generate tests, and prepare work for a Pull Request.

In this lab, you will use **GitHub Copilot Workspace** to resolve a GitHub Issue in the **eShopOnWebITC** repository with minimal manual intervention.

---

# Learning Objectives

After completing this lab, you will be able to:

- Open and analyze a GitHub Issue
- Generate an implementation plan
- Review AI-generated code changes
- Validate generated tests
- Prepare a Pull Request for review
- Understand the role of Human-in-the-Loop (HITL)

---

# Repository

```text
Repository:
eShopOnWebITC
```

---

# Prerequisites

- GitHub account
- GitHub Copilot license
- Access to GitHub Copilot Workspace (or equivalent preview experience)
- eShopOnWebITC repository
- Visual Studio Code with GitHub Copilot

---

# Enterprise Scenario

A Product Manager has created the following issue:

**Title:** Add Product Rating and Review Summary

**Requirements**

- Display average product rating.
- Show total number of reviews.
- Update product details page.
- Add unit tests.
- Update project documentation.

Your goal is to resolve this issue using GitHub Copilot Workspace.

---

# End-to-End Workflow

```text
GitHub Issue
      │
      ▼
Copilot Workspace
      │
      ├── Understand Issue
      ├── Generate Plan
      ├── Modify Code
      ├── Generate Tests
      ├── Validate Changes
      └── Prepare Pull Request
      │
      ▼
Developer Review
      │
      ▼
Merge
```

---

# Exercise 1 – Open the GitHub Issue

1. Open the eShopOnWebITC repository.
2. Navigate to **Issues**.
3. Create or open the sample issue.
4. Review the business requirements.
5. Identify acceptance criteria.

Deliverable:
- A clearly understood feature request.

---

# Exercise 2 – Generate an Implementation Plan

Use GitHub Copilot Workspace to:

- Analyze the issue
- Identify affected files
- Propose implementation steps
- Estimate required changes

Review the generated plan before continuing.

Questions:

- Does the plan satisfy the requirements?
- Are any tasks missing?
- Would you reorganize the implementation?

---

# Exercise 3 – Generate the Solution

Allow Copilot Workspace to:

- Modify source code
- Update multiple files
- Generate tests
- Update documentation

Observe:

- Which files were modified?
- Were existing project patterns reused?
- Did the agent explain its decisions?

---

# Exercise 4 – Validate the Changes

Run:

```bash
dotnet build
dotnet test
```

Verify:

- Build succeeds
- Tests pass
- Feature works correctly
- Documentation updated

---

# Exercise 5 – Review the Proposed Pull Request

Inspect:

- Code changes
- Test coverage
- Commit summary
- Pull Request description

Discuss:

- Would you approve the PR?
- What additional review comments would you leave?
- Which changes require manual improvement?

---

# Exercise 6 – Human-in-the-Loop Review

As the reviewer:

- Approve correct changes
- Reject unnecessary modifications
- Request improvements
- Ask Copilot Workspace to regenerate specific sections

Remember:

AI assists development—the final responsibility remains with the engineering team.

---

# Validation Checklist

- [ ] GitHub Issue analyzed
- [ ] Implementation plan generated
- [ ] Multi-file changes completed
- [ ] Tests generated
- [ ] Application builds successfully
- [ ] Pull Request prepared
- [ ] Human review completed

---

# Challenge Exercise

Create another GitHub Issue, for example:

- Add Recently Viewed Products
- Support Product Tags
- Add Wishlist Notifications

Resolve it using the same workflow and compare the generated implementation plan.

---

# Best Practices

- Write clear GitHub Issues with acceptance criteria.
- Review implementation plans before generating code.
- Validate builds and tests before approving a PR.
- Keep humans involved in architectural and security decisions.
- Use Workspace to accelerate—not replace—engineering judgment.

---

# Knowledge Check

1. How does Copilot Workspace differ from Agent Mode?
2. Why should implementation plans be reviewed?
3. What artifacts can Workspace generate besides code?
4. Why is Human-in-the-Loop important before merging?

---

# Summary

In this lab, you used GitHub Copilot Workspace to complete the lifecycle of a GitHub Issue—from planning through implementation, testing, documentation, and Pull Request preparation—while maintaining developer oversight.

---

# Looking Ahead

In **Lab 3**, you will build a **Router Agent** that classifies natural language requests and intelligently routes them to either the RAG Skill or the Text2SQL Skill created in previous modules.
