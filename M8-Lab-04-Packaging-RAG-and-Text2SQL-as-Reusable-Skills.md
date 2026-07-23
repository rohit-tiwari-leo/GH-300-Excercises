# Module 08 – Lab 04
# Packaging RAG and Text2SQL as Reusable Skills for Router Agents

> **Module:** M8 – RAG · Text2SQL · CI/CD Integration  
> **Duration:** 75–90 Minutes  
> **Difficulty:** Advanced

---

# Introduction

In the previous labs you built a Retrieval-Augmented Generation (RAG) solution and a Text2SQL solution. Rather than invoking these capabilities through ad-hoc prompts, enterprise AI applications package them as **reusable Skills**.

In this lab, you will create two **SKILL.md** files that describe the RAG and Text2SQL capabilities. These skills will later be discovered and orchestrated by the **Router Agent** introduced in **Module 9**.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain the purpose of reusable GitHub Copilot Skills.
- Package RAG as a reusable skill.
- Package Text2SQL as a reusable skill.
- Validate that the skills are discoverable.
- Prepare the project for Router Agent orchestration.

---

# Background Concepts

## Why Skills?

Skills encapsulate a capability so it can be reused across repositories and AI workflows.

Benefits include:

- Reusability
- Standardization
- Easier maintenance
- Better prompt consistency
- Agent discoverability

---

## Enterprise Scenario

Contoso Retail has completed two AI capabilities:

- Enterprise Knowledge Base (RAG)
- Sales Analytics (Text2SQL)

Both capabilities must now be published as reusable skills that can later be selected automatically by a Router Agent.

---

# Repository Structure

```text
.github/
│
├── skills/
│   ├── rag/
│   │   └── SKILL.md
│   ├── text2sql/
│   │   └── SKILL.md
│   └── router/
│       └── router-agent.md   (Module 9)
```

---

# Prerequisites

- Completed Lab 2 (RAG)
- Completed Lab 3 (Text2SQL)
- GitHub Copilot
- GitHub Codespaces or Visual Studio Code

---

# Exercise 1 – Create the RAG Skill

Create:

```text
.github/skills/rag/SKILL.md
```

Describe:

- Purpose
- Supported questions
- Required inputs
- Expected outputs
- Usage examples
- Limitations

Verify that GitHub Copilot can explain the skill.

---

# Exercise 2 – Create the Text2SQL Skill

Create:

```text
.github/skills/text2sql/SKILL.md
```

Document:

- Business purpose
- Database schema assumptions
- Natural language inputs
- SQL outputs
- Security considerations
- Sample prompts

Validate the generated documentation.

---

# Exercise 3 – Discover and Test the Skills

Use GitHub Copilot Chat to:

- Explain the RAG skill
- Explain the Text2SQL skill
- Suggest when each skill should be used

Confirm the skills are discoverable and understandable.

---

# Exercise 4 – Prepare for Router Agent Integration

Create:

```text
.github/router/router-agent.md
```

Define routing rules such as:

- Enterprise policy questions → RAG Skill
- Database reporting questions → Text2SQL Skill

Document expected routing behavior.

> This routing configuration will be used in Module 9.

---

# Exercise 5 – Validate the End-to-End Workflow

Test the following prompts:

- "What is our travel reimbursement policy?"
- "Show the top 10 products by revenue."

Confirm:

- RAG answers policy questions.
- Text2SQL generates SQL for reporting questions.
- Skills are ready for Router Agent orchestration.

---

# Validation Checklist

- [ ] RAG SKILL.md created.
- [ ] Text2SQL SKILL.md created.
- [ ] Skills documented.
- [ ] Skills validated with GitHub Copilot.
- [ ] Router configuration prepared.

---

# Challenge Exercise

Extend the solution by adding:

- API Wrapper Skill
- Code Generation Skill
- Documentation Skill

Update the routing configuration to support all skills.

---

# Best Practices

- Keep skills focused on one responsibility.
- Provide clear inputs and outputs.
- Include realistic examples.
- Version-control every SKILL.md.
- Re-evaluate skills whenever underlying capabilities change.

---

# Knowledge Check

1. Why should enterprise AI capabilities be packaged as reusable skills?
2. What information should every SKILL.md contain?
3. Why is discoverability important for Router Agents?
4. How do reusable skills improve maintainability?

---

# Summary

| Concept | Outcome |
|---------|---------|
| RAG Skill | Reusable enterprise knowledge capability |
| Text2SQL Skill | Reusable analytics capability |
| SKILL.md | Standardized capability definition |
| Router Preparation | Enables intelligent orchestration |
| Module 9 | Dynamic routing across multiple skills |

---

# Looking Ahead

In **Module 9**, you will build a Router Agent that automatically selects the appropriate skill based on user intent, enabling intelligent orchestration across RAG, Text2SQL, and future enterprise AI capabilities.
