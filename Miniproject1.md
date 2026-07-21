# GitHub Copilot Mini Project
## AI-Assisted Development with Prompt Engineering and Copilot Best Practices

---

# Objective

In this mini project, you will build a small application while learning how to effectively collaborate with GitHub Copilot.

Instead of focusing only on coding, you will practice:

- Writing effective prompts
- Using different GitHub Copilot modes
- Creating Copilot Instructions
- Iteratively improving AI-generated code
- Reviewing and validating AI suggestions
- Understanding when to use Chat, Edit, Agent, and Plan modes

---

# Learning Outcomes

By the end of this lab, participants should be able to:

- Write high-quality prompts using prompt engineering best practices
- Use GitHub Copilot as an AI pair programmer
- Create reusable Copilot Instructions
- Select the appropriate Copilot mode for different tasks
- Generate production-quality code with AI assistance
- Critically review AI-generated output
- Improve developer productivity using GitHub Copilot

---



# Problem Statement

Choose **any existing application** that you are familiar with.

Examples:

- E-Commerce-https://github.com/rohit-tiwari-leo/eShopOnWebITC.git
- Employee Management
- Hospital Management
- Banking
- Library Management
- Student Management
- Inventory System
- Food Delivery
- CRM
- Expense Tracker
- Travel Booking

> **Important:** You are NOT required to create a new application from scratch.
>
> You can use:
>
> - an existing project
> - your organization's internal project (if allowed)
> - a sample application
> - a previous training project
> - a personal project

Your goal is to complete the following activities using GitHub Copilot.

---

# Suggested Features

Implement **4–6 features** such as:

- CRUD operations
- Search
- Filtering
- Pagination
- Authentication
- Dashboard
- Reports
- File Upload
- REST APIs
- Unit Tests
- Error Handling
- Logging

---

# Phase 1 — Understand the Requirement

## Task

Ask GitHub Copilot to understand the project.

### Example Prompt

```
Explain the architecture of this project.

Identify:
- frontend
- backend
- database
- important modules
- external dependencies
- API flow

Provide the explanation in simple language.
```

---

### Learning

Use **Chat Mode**

Purpose:

- Understanding code
- Learning architecture
- Exploring unfamiliar projects

---

# Phase 2 — Prompt Engineering

Before asking Copilot to generate code, improve your prompts.

Use the following principles.

## Best Practices

### 1. Be Specific

Instead of

```
Create login
```

Use

```
Create a secure login API using JWT authentication.
Validate email and password.
Return proper HTTP status codes.
Use clean architecture.
```

---

### 2. Provide Context

Mention

- Framework
- Language
- Existing files
- Coding standards

Example

```
This project uses ASP.NET Core 9 Web API.

Follow repository pattern.

Use Entity Framework Core.

Do not change existing API routes.
```

---

### 3. Define Constraints

Example

```
Do not introduce new libraries.

Reuse existing services.

Write clean, maintainable code.

Follow SOLID principles.
```

---

### 4. Define Output

Example

```
Generate:

- Controller
- Service
- Repository
- Unit Tests
- API Documentation
```

---

# Exercise

Rewrite three poor prompts into effective prompts.

---

# Phase 3 — Copilot Chat Mode

Use Chat Mode for:

- Code explanation
- Architecture understanding
- Refactoring suggestions
- Bug explanation
- API explanation
- SQL explanation

Example prompts

```
Explain this service.

Suggest performance improvements.

Explain this LINQ query.

Explain this React component.

Find potential bugs.
```

---

# Phase 4 — Copilot Edit Mode

Use Edit Mode for making controlled changes.

Tasks

- Rename variables
- Improve readability
- Add comments
- Improve logging
- Improve exception handling
- Optimize code

Example prompt

```
Refactor this method.

Improve readability.

Do not change functionality.
```

---

# Phase 5 — Copilot Agent Mode

Use Agent Mode for larger development tasks.

Example Tasks

- Build an entire feature
- Generate CRUD operations
- Add authentication
- Create unit tests
- Build APIs
- Create documentation

Example prompt

```
Implement Product Management.

Requirements

- CRUD APIs
- Validation
- Repository Pattern
- Unit Tests
- Swagger Documentation

Update all required files.
```

Observe how Agent Mode:

- plans work
- edits multiple files
- creates new files
- asks for approval when necessary

---

# Phase 6 — Copilot Plan Mode

Use Plan Mode before implementing a feature.

Example

```
We need to implement Order Management.

Create an implementation plan.

Include:

- affected files
- APIs
- database changes
- testing strategy
- risks
- estimated effort
```

Review the generated plan before implementation.

---

# Phase 7 — Create Copilot Instructions

Create a project-specific Copilot Instructions file.

Example:

```
Always generate production-ready code.

Use C#.

Use .NET 9.

Follow Clean Architecture.

Use Repository Pattern.

Use Dependency Injection.

Add XML comments.

Handle exceptions properly.

Write async methods.

Use meaningful variable names.

Write unit tests.

Do not introduce unnecessary NuGet packages.

Follow SOLID principles.

Use existing project structure.

Generate clean, readable code.
```

Verify whether Copilot follows these instructions in subsequent prompts.

---

# Phase 8 — Improve Generated Code

Review every AI-generated response.

Check:

- Readability
- Performance
- Security
- Naming conventions
- Error handling
- Code duplication
- Logging
- Testability

Ask Copilot:

```
Review the generated code.

Identify improvements.

Suggest best practices.

Point out security issues.

Suggest performance optimizations.
```

---

# Phase 9 — Generate Tests

Ask Copilot to create tests.

Example

```
Generate unit tests.

Cover

- success cases

- validation failures

- exceptions

- edge cases
```

---

# Phase 10 — Documentation

Generate documentation using Copilot.

Example

```
Generate README.

Include

Installation

Architecture

Folder Structure

API Endpoints

Prerequisites

How to Run

Testing

Known Limitations
```

---

# Deliverables

Each participant should submit:

- Updated application
- Copilot Instructions file
- List of prompts used
- Screenshots of Chat, Edit, Agent, and Plan modes
- README
- Unit Tests
- Reflection document

---

# Reflection Questions

1. Which Copilot mode did you use the most?
2. Which mode saved the most time?
3. Which prompts produced the best results?
4. How did Copilot Instructions improve responses?
5. What AI suggestions did you reject?
6. What manual changes were required?
7. What prompt engineering techniques worked best?
8. What limitations did you observe?

---

# Success Criteria

Participants should demonstrate that they can:

- Use effective prompt engineering
- Select the correct Copilot mode
- Create and use Copilot Instructions
- Review AI-generated code critically
- Improve generated code before accepting it
- Generate documentation and tests
- Deliver a working feature using GitHub Copilot

---

# Bonus Challenges

Choose one or more advanced activities:

- Ask Copilot to identify security vulnerabilities and suggest fixes.
- Generate integration tests or end-to-end tests for a selected feature.
- Refactor a legacy module into a cleaner architecture while preserving functionality.
- Add structured logging and centralized exception handling.
- Improve database query performance and explain the optimizations.
- Generate API documentation and sequence diagrams.
- Create a GitHub Actions workflow for build, test, and code quality checks.
- Compare the outputs from Chat, Edit, Agent, and Plan modes for the same task and document when each mode is most effective.
- Create reusable prompt templates for common development tasks in your team.

---


# Key Takeaways

- AI is most effective when guided by clear, contextual, and specific prompts.
- Use the right Copilot mode for the task: Chat for understanding, Edit for targeted changes, Plan for design, and Agent for multi-file implementation.
- Copilot Instructions help enforce consistent coding standards across a project.
- Always review, test, and validate AI-generated code before merging it into production.
- Treat GitHub Copilot as an AI pair programmer—not a replacement for engineering judgment.
