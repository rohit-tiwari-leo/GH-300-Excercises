
# Module 09 – Lab 04
# Evaluation Gate for Router Agent using GitHub Actions

> **Module:** M9 – Agentic AI Workflows with GitHub Copilot
>
> **Duration:** 75–90 Minutes
>
> **Difficulty:** Advanced

---

# Introduction

Enterprise AI systems should not be deployed based solely on successful builds. They must also satisfy quality gates for **routing accuracy**, **tool-call success**, and **grounded responses**.

In this lab, you will reuse the evaluation approach from **Module 7** to automatically evaluate the Router Agent. A GitHub Actions workflow will fail if the overall score is below the required threshold.

---

# Learning Objectives

After completing this lab, you will be able to:

- Evaluate Router Agent behavior automatically.
- Measure routing accuracy.
- Measure tool-call success.
- Integrate AI evaluation into a CI pipeline.
- Block Pull Requests that do not meet quality standards.

---

# Repository

```text
Repository:
eShopOnWebITC
```

---

# Prerequisites

- Module 6: SKILL.md definitions
- Module 7: Evaluation framework
- Module 8: RAG and Text2SQL
- Module 9 Lab 3: Router Agent
- GitHub Actions enabled

---

# Enterprise Scenario

Every Pull Request must prove that the Router Agent:

- Selects the correct skill.
- Successfully invokes the selected tool.
- Produces grounded responses.

If the overall evaluation score is below **85%**, the PR must not be merged.

---

# Evaluation Pipeline

```text
Pull Request
      │
      ▼
GitHub Actions
      │
      ▼
Run Agent Evaluation
      │
      ├── Routing Accuracy
      ├── Tool-call Success
      ├── Grounded Response Validation
      └── Safety Checks
      │
      ▼
Overall Score
      │
      ├── >= 85%  → PASS
      └── < 85%   → FAIL PR
```

---

# Suggested Repository Structure

```text
.github/
└── workflows/
    └── agent-evaluation.yml

evaluations/
└── router/
    ├── dataset.json
    ├── expected-results.json
    └── evaluation-report.md
```

---

# Exercise 1 – Prepare the Evaluation Dataset

Create a dataset containing:

- User Question
- Expected Skill
- Expected Tool
- Expected Outcome

Example questions:

- What is the return policy?
- Explain the shipping process.
- Show monthly sales.
- Top 10 products by revenue.

---

# Exercise 2 – Define Evaluation Metrics

Measure:

| Metric | Description |
|---------|-------------|
| Routing Accuracy | Correct skill selected |
| Tool-call Success | Tool executed successfully |
| Grounded Response | Answer supported by retrieved context or SQL results |
| Overall Score | Combined evaluation score |

Suggested Threshold:

| Metric | Target |
|---------|--------|
| Routing Accuracy | 90% |
| Tool-call Success | 95% |
| Overall Score | 85% |

---

# Exercise 3 – Create GitHub Actions Workflow

Create:

```text
.github/workflows/agent-evaluation.yml
```

Workflow responsibilities:

1. Build the project.
2. Execute automated tests.
3. Run Router Agent evaluation.
4. Generate evaluation report.
5. Compare results with configured thresholds.
6. Fail the workflow if the overall score is below 85%.

> Hint: Reuse the evaluation scripts developed in Module 7.

---

# Exercise 4 – Execute the Pipeline

Create a Pull Request.

Observe the GitHub Actions workflow.

Verify:

- Dataset executed.
- Metrics calculated.
- Evaluation report generated.
- PASS or FAIL status displayed.

---

# Exercise 5 – Investigate Failures

If the workflow fails:

- Review incorrect routing decisions.
- Identify failed tool invocations.
- Improve routing rules.
- Improve SKILL.md descriptions.
- Re-run the workflow.

Repeat until the evaluation passes.

---

# Validation Checklist

- [ ] Evaluation dataset created
- [ ] GitHub Actions workflow created
- [ ] Routing Accuracy measured
- [ ] Tool-call Success measured
- [ ] Evaluation report generated
- [ ] PR blocked below 85%
- [ ] PR passes above threshold

---

# Challenge Exercise

Enhance the evaluation by adding:

- Ambiguous user questions
- Multi-turn conversations
- Safety policy validation
- Hallucination detection
- Performance metrics (latency)

---

# Best Practices

- Evaluate every Pull Request.
- Keep evaluation datasets under source control.
- Expand datasets as new skills are added.
- Monitor trends instead of single scores.
- Treat AI evaluation like automated testing.

---

# Knowledge Check

1. Why should AI agents be evaluated in CI?
2. What does Routing Accuracy measure?
3. Why is Tool-call Success important?
4. Why should PRs be blocked below the quality threshold?

---

# Summary

In this lab, you integrated automated AI evaluation into GitHub Actions. Every Pull Request is validated for routing quality, successful tool execution, and grounded responses before merge approval, helping ensure production-ready agent behavior.

---

# Looking Ahead

In the next lab, you will introduce a **Human-in-the-Loop (HITL)** approval stage where reviewers can approve, reject, override, or redirect the Router Agent before deployment.
