# Module 08 – Lab 01
# Using Project Context for Intelligent Code Generation

> **Module:** M8 – RAG · Text2SQL · CI/CD Integration  
> **Duration:** 60–75 Minutes  
> **Difficulty:** Intermediate

---

# Introduction

GitHub Copilot produces significantly better results when it has access to **project context** rather than relying on a single prompt. Repository structure, existing code, interfaces, documentation, and naming conventions all help Copilot generate code that is more accurate and consistent with the application.

In this lab, you will compare **non-contextual** code generation with **context-aware** generation to understand how repository context improves code quality.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain how GitHub Copilot uses repository and workspace context.
- Generate code with and without project context.
- Compare generated outputs for consistency and quality.
- Apply best practices for context-aware prompting.

---

# Background Concepts

## Types of Context

GitHub Copilot can leverage:

- Current file context
- Open editor tabs
- Repository source code
- Project documentation (README)
- Interfaces and models
- Existing coding patterns

## Why Context Matters

Context-aware generation improves:

- Naming consistency
- Architectural alignment
- API usage
- Reuse of existing classes
- Reduced duplicate code

---

# Enterprise Scenario

Contoso Retail is developing an Order Management application. The project already contains:

- `Customer.cs`
- `ICustomerRepository.cs`
- `CustomerRepository.cs`
- `README.md`
- Coding standards

A new developer must implement `CustomerService.cs` using GitHub Copilot.

---

# Repository Structure

```text
Contoso-OrderManagement/
│
├── README.md
├── Models/
│   └── Customer.cs
├── Repositories/
│   ├── ICustomerRepository.cs
│   └── CustomerRepository.cs
└── Services/
```

---

# Prerequisites

- GitHub Codespaces or Visual Studio Code
- GitHub Copilot Chat
- Sample repository
- Git installed

---

# Exercise 1 – Generate Code Without Context

Create:

```text
Services/CustomerService.cs
```

Prompt Copilot:

```text
Generate a CustomerService class for managing customer records.
```

Review the generated code and note:

- Method names
- Dependency injection
- Error handling
- Coding style

> 📷 **Screenshot:** Initial generated code.

---

# Exercise 2 – Explore the Repository

Open:

- README.md
- Customer.cs
- ICustomerRepository.cs
- CustomerRepository.cs

Ask Copilot:

```text
Explain the architecture of this project.
```

Identify:

- Naming conventions
- Dependency injection pattern
- Existing business logic
- Folder organization

---

# Exercise 3 – Generate Code Using Project Context

With the project files open, ask Copilot:

```text
Generate CustomerService.cs that follows the existing repository pattern and uses ICustomerRepository through dependency injection.
```

Verify that the generated code:

- Uses existing interfaces
- Matches project conventions
- Reuses existing models
- Avoids duplicate implementations

> 📷 **Screenshot:** Context-aware generated code.

---

# Exercise 4 – Compare the Results

Complete the following comparison.

| Attribute | Without Context | With Context |
|-----------|-----------------|--------------|
| Naming conventions | | |
| Dependency injection | | |
| Code reuse | | |
| Consistency | | |
| Overall quality | | |

Discuss:

- Which version required fewer edits?
- Which version aligned better with the project?

---

# Exercise 5 – Refine the Prompt

Enhance the prompt by adding requirements such as:

- XML documentation
- Logging
- Input validation
- Asynchronous methods
- Exception handling

Generate the service again and compare the output.

---

# Validation Checklist

- [ ] Code generated without context.
- [ ] Repository explored.
- [ ] Context-aware generation completed.
- [ ] Outputs compared.
- [ ] Prompt refined.

---

# Challenge Exercise

Extend the service to include:

- Unit-test friendly design
- Pagination support
- Logging with ILogger
- Validation using existing project standards

Use GitHub Copilot to generate the implementation while maintaining repository consistency.

---

# Best Practices

- Open relevant files before prompting.
- Reference existing interfaces and models.
- Ask Copilot to follow repository conventions.
- Keep README documentation up to date.
- Prefer incremental generation over large one-shot prompts.

---

# Knowledge Check

1. What types of repository context improve GitHub Copilot responses?
2. Why is context-aware generation more reliable?
3. How can existing interfaces improve generated code?
4. Why should prompts reference project architecture?

---

# Summary

| Concept | Outcome |
|---------|---------|
| Repository Context | Improves code generation quality |
| Existing Code | Provides architectural guidance |
| Context-Aware Prompting | Produces more consistent implementations |
| GitHub Copilot | Generates code aligned with project standards |

---

# Looking Ahead

In **Lab 2**, you will build a **GitHub Copilot Extension** backed by a custom knowledge base, then evaluate its responses using the **RAGAS** evaluation framework introduced in Module 7.
