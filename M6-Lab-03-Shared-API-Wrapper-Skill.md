# Module 06 -- Lab 03

# Building a Shared API Wrapper Skill and Publishing it to a Team GitHub Repository

> **Module:** M6 -- Reusable Skills and Repository Instructions\
> **Duration:** 60--75 Minutes\
> **Difficulty:** Intermediate

------------------------------------------------------------------------

# Introduction

Enterprise development teams frequently consume the same REST APIs
across multiple applications. Although GitHub Copilot can generate API
integration code, developers often repeat prompts describing
authentication, error handling, retry logic, logging, and response
validation.

A reusable **API Wrapper Skill** captures these organizational standards
once, enabling every developer to generate consistent API client code.

In this lab, you will create a reusable API Wrapper Skill, validate it
locally, and publish it to a shared GitHub repository for team-wide
reuse.

------------------------------------------------------------------------

# Learning Objectives

After completing this lab, you will be able to:

-   Explain the purpose of reusable shared Skills.
-   Design an enterprise API Wrapper Skill.
-   Create a reusable `SKILL.md`.
-   Test the Skill using GitHub Copilot Chat.
-   Publish the Skill to a shared GitHub repository.
-   Reuse the Skill across multiple projects.

------------------------------------------------------------------------

# Why Create Shared Skills?

Instead of every developer writing their own prompts, organizations
maintain a centralized library of reusable Skills.

Benefits include:

-   Standardized code generation
-   Consistent API design
-   Reduced prompt duplication
-   Easier onboarding
-   Knowledge sharing across teams

------------------------------------------------------------------------

# Enterprise Scenario

**Contoso Retail** exposes internal Order, Inventory, and Customer APIs.

The architecture team has standardized API integrations using:

-   OAuth 2.0 authentication
-   Retry policies
-   Structured logging
-   Centralized exception handling
-   JSON serialization
-   Asynchronous programming

Rather than documenting these rules repeatedly, the team creates a
shared **API Wrapper Skill**.

------------------------------------------------------------------------

# Suggested Repository Structure

``` text
Shared-AI-Skills/
│
├── .github/
│   └── skills/
│       └── api-wrapper/
│           └── SKILL.md
│
├── README.md
└── LICENSE
```

------------------------------------------------------------------------

# Anatomy of the API Wrapper Skill

A well-designed Skill should describe:

-   Purpose
-   When to use
-   Authentication model
-   Request construction
-   Error handling
-   Retry strategy
-   Logging
-   Output format
-   Examples

------------------------------------------------------------------------

# Best Practices

-   Keep the Skill technology-agnostic where possible.
-   Include organization-specific conventions.
-   Encourage async programming.
-   Avoid embedding secrets.
-   Document expected outputs.

------------------------------------------------------------------------

# Exercise 1 -- Create the Skill

Create:

``` text
.github/skills/api-wrapper/SKILL.md
```

Add the following content.

``` markdown
# Enterprise API Wrapper

## Purpose

Generate enterprise-grade API wrapper code.

## When to Use

Use this Skill whenever creating or consuming REST APIs.

## Requirements

- OAuth 2.0 authentication
- Async methods
- Retry failed requests
- Structured logging
- Centralized exception handling
- Validate HTTP status codes
- Deserialize JSON responses

## Coding Standards

- Prefer HttpClientFactory
- Avoid hard-coded URLs
- Inject dependencies
- Follow SOLID principles

## Output

Generate production-ready code with comments and error handling.
```

> 📷 **Screenshot:** Completed API Wrapper Skill.

------------------------------------------------------------------------

# Exercise 2 -- Test the Skill

Open GitHub Copilot Chat.

Prompt:

``` text
Generate an API wrapper for the Customer API using the enterprise API Wrapper Skill.
```

Expected output should include:

-   Dependency injection
-   Async methods
-   Authentication placeholders
-   Logging
-   Retry logic
-   Exception handling

------------------------------------------------------------------------

# Exercise 3 -- Publish to GitHub

Create a new GitHub repository named:

``` text
Shared-AI-Skills
```

Commit the Skill.

``` bash
git add .
git commit -m "Add Enterprise API Wrapper Skill"
git push origin main
```

> 📷 **Screenshot:** GitHub repository containing the shared Skill.

------------------------------------------------------------------------

# Exercise 4 -- Reuse the Skill

Clone the shared repository into another sample project.

Verify that GitHub Copilot continues using the same API Wrapper Skill
for API generation.

Discuss:

-   How does a shared Skill improve consistency?
-   What changes if the Skill is updated centrally?

------------------------------------------------------------------------

# Validation Checklist

-   [ ] API Wrapper Skill created.
-   [ ] Skill generates consistent API code.
-   [ ] Shared repository created.
-   [ ] Skill committed to GitHub.
-   [ ] Skill reused from another project.

------------------------------------------------------------------------

# Challenge Exercise

Extend the Skill to support:

-   GraphQL APIs
-   gRPC services
-   API versioning
-   Distributed tracing
-   OpenTelemetry
-   Circuit Breaker pattern

Test each enhancement with GitHub Copilot.

------------------------------------------------------------------------

# Knowledge Check

1.  Why should API guidance be stored as a reusable Skill?
2.  What information belongs in an API Wrapper Skill?
3.  Why should Skills avoid hard-coded secrets?
4.  What are the advantages of a centralized Skill repository?

------------------------------------------------------------------------

# Summary

  Concept             Outcome
  ------------------- ---------------------------------------
  Shared Skills       Team-wide reuse
  API Wrapper         Standardized integrations
  GitHub Repository   Centralized maintenance
  Benefits            Consistency, governance, productivity

------------------------------------------------------------------------

# Key Takeaways

You created a reusable API Wrapper Skill, validated it with GitHub
Copilot, published it to a shared GitHub repository, and learned how
centralized Skills promote consistent enterprise development practices.
