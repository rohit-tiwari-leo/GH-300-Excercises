# Module 06 -- Lab 01

# Authoring a Reusable `SKILL.md` for Data Validation

> **Module:** M6 -- Reusable Skills and Repository Instructions\
> **Duration:** 45--60 Minutes\
> **Difficulty:** Intermediate

------------------------------------------------------------------------

# Introduction

As organizations adopt **GitHub Copilot** across multiple teams,
developers often repeat the same prompts for common tasks such as
validation, code review, documentation, and API generation.

A **Skill** allows you to package domain knowledge into a reusable
Markdown file (`SKILL.md`) so GitHub Copilot can apply consistent
guidance whenever the task is relevant. Instead of repeatedly typing
lengthy prompts, teams can encapsulate best practices once and reuse
them across repositories.

In this lab you will create a reusable **Data Validation Skill** and
invoke it from GitHub Copilot Chat.

------------------------------------------------------------------------

# Learning Objectives

After completing this lab, you will be able to:

-   Explain the purpose of GitHub Copilot Skills.
-   Differentiate between prompts, Skills, and repository instructions.
-   Create a reusable `SKILL.md`.
-   Organize Skills within a repository.
-   Invoke the Skill from GitHub Copilot Chat.
-   Validate structured business data using the reusable Skill.

------------------------------------------------------------------------

# GitHub Copilot Skills

A **Skill** is a reusable Markdown document that contains task-specific
instructions, examples, constraints, and expected output formats. It
helps Copilot provide more consistent and organization-specific
responses.

## Why use Skills?

-   Reuse prompt engineering across projects.
-   Standardize AI-assisted development.
-   Capture organizational knowledge.
-   Reduce repetitive prompting.
-   Improve consistency across development teams.

------------------------------------------------------------------------

# Prompt vs Skill vs Repository Instructions

  ------------------------------------------------------------------------------
  Feature   Prompt         Skill (`SKILL.md`)     `copilot-instructions.md`
  --------- -------------- ---------------------- ------------------------------
  Scope     One            Reusable task          Entire repository
            conversation                          

  Shared    No             Yes                    Yes

  Purpose   One-off        Domain expertise       Coding standards
            request                               

  Best Use  Quick          Repeatable workflows   Team-wide conventions
            questions                             
  ------------------------------------------------------------------------------

------------------------------------------------------------------------

# Repository Structure

GitHub Copilot discovers reusable skills from the `.github/skills`
folder.

``` text
OrderManagement/
│
├── .github/
│   └── skills/
│       └── data-validation/
│           └── SKILL.md
└── src/
```

------------------------------------------------------------------------

# Anatomy of a SKILL.md

A well-designed Skill typically includes:

## Purpose

Explains what the Skill is designed to accomplish.

## When to Use

Describes scenarios where Copilot should apply the Skill.

## Validation Rules

Defines business logic and constraints.

## Examples

Shows expected inputs and outputs.

## Constraints

States what the Skill should not do.

## Output Format

Ensures structured and repeatable responses.

------------------------------------------------------------------------

# Best Practices

✅ Keep one responsibility per Skill.

✅ Provide realistic examples.

✅ Clearly define the output format.

✅ Keep business rules deterministic.

❌ Avoid combining unrelated tasks into one Skill.

❌ Do not duplicate repository-wide coding standards.

------------------------------------------------------------------------

# Enterprise Scenario

**Contoso Retail** processes thousands of customer orders every day.
Different teams implement validation logic across APIs, web
applications, and background services.

To ensure consistent validation, the architecture team decides to create
a reusable **Data Validation Skill** that every developer can invoke
through GitHub Copilot Chat.

------------------------------------------------------------------------

# Lab Architecture

``` text
Developer
    │
    ▼
GitHub Copilot Chat
    │
    ▼
SKILL.md
    │
    ▼
Validation Rules
    │
    ▼
Structured Validation Result
```

------------------------------------------------------------------------

# Exercise 1 -- Create the Repository Structure

Create the following directory structure.

``` text
OrderManagement/
└── .github/
    └── skills/
        └── data-validation/
            └── SKILL.md
```

> 📷 **Screenshot:** Repository structure after creating the folders.

------------------------------------------------------------------------

# Exercise 2 -- Author the Skill

Create `.github/skills/data-validation/SKILL.md`.

Use the following template.

``` markdown
# Data Validation Assistant

## Purpose

Validate customer and order information before processing.

## When to Use

Use this skill whenever validating customer records or sales orders.

## Validation Rules

### Customer Name
- Required
- Minimum 3 characters

### Email
- Required
- Valid email format

### Phone
- Country code required

### Country
Allowed:
- India
- USA
- UK
- Canada
- Australia

### Postal Code
Validate according to country.

### Order Amount
- Greater than 0
- Warn if greater than 100000

## Response Format

Validation Status

Errors

Warnings

Recommendations
```

> 📷 **Screenshot:** Completed `SKILL.md`.

------------------------------------------------------------------------

# Exercise 3 -- Invoke the Skill

Open GitHub Copilot Chat.

Prompt:

``` text
Validate the following customer order using the data-validation skill.

Customer Name: John
Email: john.gmail.com
Phone: 9876543210
Country: India
Postal Code: ABC123
Order Amount: -250
```

Expected observations:

-   Invalid email
-   Missing country code
-   Invalid postal code
-   Negative order amount

------------------------------------------------------------------------

# Exercise 4 -- Validate a Correct Record

``` text
Customer Name: Alice Smith
Email: alice@example.com
Phone: +1 9876543210
Country: USA
Postal Code: 90210
Order Amount: 450
```

Expected:

``` text
Validation Status: PASS
```

------------------------------------------------------------------------

# Experiment

Remove the **Response Format** section from the Skill and repeat the
prompt.

Observe how the response becomes less structured.

Discuss:

-   Why did the output change?
-   Why are examples and formatting instructions important?

------------------------------------------------------------------------

# Validation Checklist

-   [ ] Skill created successfully.
-   [ ] Repository structure is correct.
-   [ ] Copilot uses the reusable Skill.
-   [ ] Invalid data generates meaningful errors.
-   [ ] Valid data passes validation.

------------------------------------------------------------------------

# Challenge Exercise

Create an additional reusable Skill named **Payment Validation**.

Include:

-   Credit Card Number
-   CVV
-   Expiry Date
-   Currency
-   Payment Amount

Invoke it from Copilot Chat and compare the responses.

------------------------------------------------------------------------

# Knowledge Check

1.  What problem do reusable Skills solve?
2.  Where should `SKILL.md` be stored?
3.  When would you use a repository instruction instead of a Skill?
4.  Why should a Skill define an output format?

------------------------------------------------------------------------

# Summary

  Concept                Outcome
  ---------------------- -----------------------------------------
  Skills                 Encapsulate reusable prompt engineering
  SKILL.md               Stores task-specific knowledge
  Repository Structure   Enables discovery by Copilot
  Benefits               Consistency, governance, productivity

------------------------------------------------------------------------

# Key Takeaways

You learned how to:

-   Create a reusable GitHub Copilot Skill.
-   Structure Skills for enterprise repositories.
-   Invoke Skills through GitHub Copilot Chat.
-   Build reusable AI guidance instead of repeating prompts.
