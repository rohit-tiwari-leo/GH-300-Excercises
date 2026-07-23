# Module 06 -- Lab 02

# Creating `copilot-instructions.md` to Enforce UAT Module Boundaries

> **Module:** M6 -- Reusable Skills and Repository Instructions\
> **Duration:** 45--60 Minutes\
> **Difficulty:** Intermediate

------------------------------------------------------------------------

# Introduction

As GitHub Copilot becomes part of day-to-day software development,
organizations need a way to ensure AI-generated code follows team
standards. While reusable **Skills** capture task-specific expertise,
**Repository Instructions** establish coding conventions, architectural
guidelines, and project constraints that apply across the entire
repository.

In this lab, you will create a `copilot-instructions.md` file that
restricts development to **User Acceptance Testing (UAT)** modules and
observe how GitHub Copilot's suggestions change before and after the
instructions are introduced.

------------------------------------------------------------------------

# Learning Objectives

After completing this lab, you will be able to:

-   Explain the purpose of repository instructions.
-   Differentiate repository instructions from Skills.
-   Create and maintain `copilot-instructions.md`.
-   Guide Copilot toward organization-specific development standards.
-   Compare Copilot responses before and after repository instructions.

------------------------------------------------------------------------

# What are Repository Instructions?

`copilot-instructions.md` is a repository-level guidance file that
provides persistent instructions to GitHub Copilot.

Unlike prompts or Skills, repository instructions apply to **every
Copilot interaction** within the repository, helping teams enforce:

-   Coding standards
-   Architecture decisions
-   Naming conventions
-   Technology stack
-   Security practices
-   Project-specific constraints

------------------------------------------------------------------------

# Skills vs Repository Instructions

  Feature   SKILL.md           copilot-instructions.md
  --------- ------------------ ---------------------------
  Scope     Task-specific      Entire repository
  Purpose   Domain knowledge   Team conventions
  Trigger   Relevant task      Repository context
  Example   Data validation    Use only approved modules

------------------------------------------------------------------------

# Enterprise Scenario

**Contoso Retail** has separate environments for Development, QA, UAT,
and Production.

The architecture team has decided that developers working in the **UAT
branch** should modify only approved UAT modules. GitHub Copilot should
avoid suggesting changes outside the approved list.

------------------------------------------------------------------------

# Repository Structure

``` text
OrderManagement/
│
├── .github/
│   ├── skills/
│   └── copilot-instructions.md
└── src/
```

------------------------------------------------------------------------

# Best Practices

-   Keep instructions concise and unambiguous.
-   Focus on repository-wide guidance.
-   Avoid duplicating task-specific logic from Skills.
-   Update instructions whenever architecture changes.
-   Review instructions as part of code reviews.

------------------------------------------------------------------------

# Exercise 1 -- Observe Baseline Behavior

Before creating repository instructions, open GitHub Copilot Chat and
ask:

``` text
Generate a feature to update customer information across all application modules.
```

Observe that Copilot may suggest changes across multiple layers without
considering UAT restrictions.

> 📷 **Screenshot:** Copilot response before repository instructions.

------------------------------------------------------------------------

# Exercise 2 -- Create Repository Instructions

Create the following file:

``` text
.github/copilot-instructions.md
```

Add the following content:

``` markdown
# Repository Instructions

## Project Context

This repository is currently in the UAT phase.

## Allowed Modules

- Customer.API
- Order.API
- Validation.Service
- UAT.Tests

## Restrictions

- Do not modify Production modules.
- Do not generate code for Experimental features.
- Follow existing project architecture.
- Preserve API contracts.

## Coding Standards

- Use C#
- Follow SOLID principles.
- Prefer asynchronous programming.
- Generate XML documentation for public methods.

## Testing

Generate unit tests for all new business logic.
```

Save the file.

> 📷 **Screenshot:** Completed `copilot-instructions.md`.

------------------------------------------------------------------------

# Exercise 3 -- Test Copilot Again

Repeat the original prompt:

``` text
Generate a feature to update customer information across all application modules.
```

Observe how the response changes.

Expected observations:

-   Suggestions focus on approved UAT modules.
-   Production modules are excluded.
-   Code follows repository standards.
-   Testing guidance is included.

------------------------------------------------------------------------

# Exercise 4 -- Experiment with Additional Constraints

Update the instructions by adding:

``` markdown
## Security

Never generate hard-coded secrets.

Always validate user input.

Use parameterized database queries.
```

Ask Copilot:

``` text
Create an API endpoint for updating customer details.
```

Verify that security recommendations are incorporated.

------------------------------------------------------------------------

# Validation Checklist

-   [ ] Repository instructions created.
-   [ ] Stored in `.github`.
-   [ ] Copilot behavior changes after adding instructions.
-   [ ] Responses respect approved UAT modules.
-   [ ] Security guidance appears in generated code.

------------------------------------------------------------------------

# Challenge Exercise

Enhance the repository instructions to include:

-   Logging standards
-   Error handling policy
-   API versioning
-   Branch naming conventions
-   Commit message format

Test each enhancement using Copilot Chat.

------------------------------------------------------------------------

# Knowledge Check

1.  Why are repository instructions different from Skills?
2.  Where should `copilot-instructions.md` be stored?
3.  What types of guidance belong in repository instructions?
4.  Why should repository instructions remain concise?

------------------------------------------------------------------------

# Summary

  Concept                   Outcome
  ------------------------- --------------------------------------
  Repository Instructions   Apply repository-wide AI guidance
  Scope                     Entire project
  Benefits                  Consistency, governance, compliance
  Use Cases                 Standards, architecture, constraints

------------------------------------------------------------------------

# Key Takeaways

You learned how to:

-   Create repository-wide GitHub Copilot instructions.
-   Restrict AI suggestions to approved UAT modules.
-   Influence Copilot behavior without rewriting prompts.
-   Combine repository instructions with reusable Skills for
    enterprise-scale AI-assisted development.
