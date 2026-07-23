
# Module 09 – Lab 05
# Human-in-the-Loop (HITL) Review for the Router Agent

> **Module:** M9 – Agentic AI Workflows with GitHub Copilot
>
> **Duration:** 60–75 Minutes
>
> **Difficulty:** Advanced

---

# Introduction

Even highly capable AI agents require human oversight before critical decisions are accepted. In enterprise environments, a **Human-in-the-Loop (HITL)** process ensures that AI-generated plans, routing decisions, and responses are reviewed before deployment or execution.

In this lab, you will implement a HITL workflow for the Router Agent developed in previous labs. Reviewers will be able to **approve**, **override**, or **redirect** the Router Agent before the final response is delivered.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain the purpose of Human-in-the-Loop (HITL)
- Review Router Agent decisions
- Approve, override, or redirect AI actions
- Capture reviewer feedback
- Improve agent reliability through human supervision

---

# Repository

```text
Repository:
eShopOnWebITC
```

---

# Prerequisites

- Module 6: Reusable SKILL.md definitions
- Module 7: Evaluation framework
- Module 8: RAG and Text2SQL implementation
- Module 9 Lab 3: Router Agent
- Module 9 Lab 4: Automated evaluation pipeline

---

# Enterprise Scenario

A customer support assistant receives the following request:

> "Show the products that generate the highest revenue and explain the return policy for those products."

The Router Agent must decide how to process the request.

A reviewer should determine whether to:

- Approve the selected route
- Override the selected tool
- Redirect the request to another skill
- Ask the user for clarification

---

# HITL Workflow

```text
User Request
      │
      ▼
Router Agent
      │
      ▼
Initial Routing Decision
      │
      ▼
Human Review
      │
 ┌────┼───────────────┐
 ▼    ▼               ▼
Approve Override  Redirect
      │
      ▼
Final Tool Execution
      │
      ▼
Grounded Response
```

---

# Suggested Repository Structure

```text
docs/
    hitl-review-guidelines.md

evaluations/
    hitl-review-log.csv

src/
    Agents/
        RouterAgent.cs
        ReviewDecision.cs
```

---

# Exercise 1 – Review the Routing Decision

Test the Router Agent with the following requests:

- Explain the shipping workflow.
- Show monthly sales by category.
- Which products have the highest return rate?
- Compare monthly revenue with customer return policies.

For each request, record:

- Selected Skill
- Reason for Routing
- Confidence (if available)

---

# Exercise 2 – Approve the Decision

Identify requests where the Router Agent selected the correct skill.

Approve the decision if:

- The correct tool was selected.
- The response is grounded.
- No policy violations exist.

Record the approval in the review log.

---

# Exercise 3 – Override the Decision

Review requests where the selected tool is incorrect.

Examples:

| User Request | Initial Route | Reviewer Action |
|--------------|---------------|-----------------|
| Explain revenue trends | RAG | Override → Text2SQL |
| Show product documentation | Text2SQL | Override → RAG |

Document why the override was necessary.

---

# Exercise 4 – Redirect the Request

Some requests require multiple capabilities or clarification.

Examples:

- Explain the products with the highest revenue.
- Which products are returned most frequently and why?

Possible reviewer actions:

- Redirect to another skill
- Request clarification
- Split into multiple tasks

Discuss which option produces the most reliable result.

---

# Exercise 5 – Capture Reviewer Feedback

Create a review log containing:

- User Question
- Initial Route
- Final Decision
- Reviewer Comments
- Outcome

Review common mistakes made by the Router Agent and identify opportunities for improvement.

---

# Validation Checklist

- [ ] Routing decisions reviewed
- [ ] Correct routes approved
- [ ] Incorrect routes overridden
- [ ] Ambiguous requests redirected
- [ ] Reviewer feedback recorded

---

# Challenge Exercise

Enhance the Router Agent so that it automatically requests human approval when:

- Confidence is below a defined threshold.
- Multiple skills appear equally appropriate.
- Sensitive business data is requested.
- The evaluation score from Lab 4 falls below the configured threshold.

Describe how this workflow improves responsible AI.

---

# Best Practices

- Keep humans involved in business-critical decisions.
- Record every override for future model improvements.
- Use evaluation metrics together with reviewer feedback.
- Escalate ambiguous requests instead of guessing.
- Treat HITL as a governance mechanism, not a bottleneck.

---

# Knowledge Check

1. Why is Human-in-the-Loop important for enterprise AI?
2. When should a reviewer override the Router Agent?
3. What types of requests should be redirected?
4. How can reviewer feedback improve future agent behavior?

---

# Summary

In this lab, you implemented a Human-in-the-Loop review process for the Router Agent. By introducing approval, override, and redirection workflows, you ensured that AI-assisted decisions remain transparent, auditable, and aligned with enterprise governance requirements.

---

# Module Summary

With Module 9 complete, you have built an end-to-end agentic workflow that includes:

- GitHub Copilot Agent Mode
- GitHub Copilot Workspace
- Router Agent orchestration
- Automated AI evaluation in GitHub Actions
- Human-in-the-Loop governance

Together, these capabilities demonstrate a production-ready approach to building, evaluating, and governing enterprise AI agents.
