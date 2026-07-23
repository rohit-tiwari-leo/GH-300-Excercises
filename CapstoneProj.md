
# GitHub Copilot Enterprise AI Assistant Capstone Project

> **Repository:** https://github.com/rohit-tiwari-leo/eShopOnWebITC
>
> **Course:** GitHub Copilot (GH-300)
>
> **Scope:** GitHub Copilot Agent Mode · Copilot Workspace · Skills · RAG · Text2SQL · Router Agent · GitHub Actions · Evaluation · Human-in-the-Loop

---

# Capstone Scenario

You are part of the engineering team responsible for enhancing the **eShopOnWebITC** application with an Enterprise AI Assistant.

The assistant must intelligently answer developer, support, and business questions by routing requests to the correct capability.

The solution should reuse everything built throughout Modules 6–9.

---

# Objectives

Build a production-ready AI Assistant capable of:

- Repository-aware code generation
- Enterprise knowledge retrieval (RAG)
- Business analytics using Text2SQL
- Intelligent routing using reusable SKILL.md files
- Automated AI evaluation in CI/CD
- Human-in-the-Loop governance

---

# Phase 1 – AI-Assisted Feature Development

Use GitHub Copilot Agent Mode to implement ONE enterprise feature.

Suggested features:

- Product Reviews
- Wishlist
- Recently Viewed Products
- Inventory Alerts
- Coupon Management

## Deliverables

- Multi-file implementation
- Prompt history
- Unit tests
- Documentation updates

---

# Phase 2 – Enterprise Knowledge Base

Create a RAG knowledge base using repository documentation.

Suggested content:

- docs/Architecture.md
- docs/API.md
- docs/DeveloperGuide.md
- docs/DeploymentGuide.md
- docs/ShippingPolicy.md
- docs/ReturnPolicy.md

## Deliverables

- Knowledge Base
- Chunking strategy
- Retrieval validation
- RAG evaluation report

---

# Phase 3 – Build Text2SQL

Support questions such as:

- Top 10 selling products
- Revenue by category
- Monthly sales
- Orders awaiting shipment
- Inventory status

## Deliverables

- SQL generation
- SQL execution
- Result validation
- Evaluation report

---

# Phase 4 – Build Router Agent

Reuse the skills created during Module 6.

```
.github/

skills/
    rag/
        SKILL.md

    text2sql/
        SKILL.md

router/
    router-agent.md
```

The Router Agent should:

- Classify intent
- Select the correct skill
- Invoke the appropriate tool
- Return grounded responses
- Log routing decisions

## Deliverables

- Router Agent
- Routing rules
- Sample routing log

---

# Phase 5 – Evaluation Pipeline

Reuse the Module 7 evaluation framework.

Measure:

- Routing Accuracy
- Tool-call Success
- Grounded Responses
- Hallucination Rate
- Overall Score

Integrate evaluation into GitHub Actions.

Fail Pull Requests when:

- Overall Score < 85%

## Deliverables

- Evaluation dataset
- GitHub Actions workflow
- Evaluation report

---

# Phase 6 – Human-in-the-Loop (HITL)

Implement reviewer workflow.

Reviewer actions:

- Approve
- Reject
- Override
- Redirect
- Request Clarification

Log all reviewer decisions.

## Deliverables

- HITL workflow
- Review log
- Reviewer guidelines

---

# Phase 7 – Documentation & Release

Use GitHub Copilot to generate:

- README.md
- Architecture documentation
- ADR
- Release Notes
- Pull Request description
- Conventional Commit messages

---

# Phase 8 – Manual vs Agentic Comparison

Repeat one selected implementation manually and then with GitHub Copilot.

Compare:

| Metric | Manual | Agentic | Delta |
|--------|--------|---------|------|
| Time to completion | | | |
| Prompts used | | | |
| Suggestion acceptance | | | |
| Defects found | | | |
| Cognitive Load (1–5) | | | |

Write a 400–600 word reflection discussing strengths, weaknesses, and productivity gains.

---

# Final Deliverables

- Working implementation
- Feature branch
- Pull Request
- Evaluation report
- HITL review log
- Documentation
- Reflection report

---

# Assessment Rubric

| Dimension | Weight |
|-----------|-------:|
| Prompt Engineering | 10% |
| Code Quality | 15% |
| RAG Quality | 15% |
| Text2SQL Accuracy | 15% |
| Router Agent Accuracy | 15% |
| Evaluation Pipeline | 10% |
| HITL Governance | 10% |
| Documentation | 5% |
| Reflection & Productivity Analysis | 5% |

---

# Passing Criteria

| Requirement | Threshold |
|-------------|----------:|
| Overall Score | >= 70% |
| Router Accuracy | >= 90% |
| Tool-call Success | >= 95% |
| Evaluation Score | >= 85% |
| Critical Hallucinations | 0 |

---

# Submission Checklist

- Repository URL
- Feature branch
- Pull Request
- Evaluation report
- Router evaluation dataset
- HITL review log
- Documentation
- Reflection report

> **Capstone Goal:** Deliver an enterprise-grade AI Assistant for the eShopOnWebITC application that demonstrates end-to-end GitHub Copilot capabilities, intelligent orchestration, automated evaluation, and responsible AI governance.
