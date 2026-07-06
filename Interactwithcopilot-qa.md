# Lab: Interacting with GitHub Copilot using Ask Mode, Agent Mode, and Plan Mode

**Course:** GitHub Copilot for Software Testing



**Duration:** 45 Minutes

**Difficulty:** Intermediate

**Audience:**
- Manual Test Engineers
- Automation Test Engineers
- QA Leads
- SDETs

---

# Lab Overview

GitHub Copilot provides multiple interaction modes that help testers accomplish different kinds of work.

Each mode is designed for a different purpose:

| Mode | Purpose | Best For |
|-------|----------|----------|
| **Ask Mode** | Answer questions and generate content | Learning, generating test cases, explaining code |
| **Agent Mode** | Perform multi-step development tasks across files | Creating automation frameworks, refactoring tests, generating artifacts |
| **Plan Mode** | Analyze requirements and create an execution strategy before implementation | Test planning, automation planning, migration planning |

In this lab, you will learn when to use each mode and practice real-world testing scenarios.

---

# Learning Objectives

After completing this lab, you will be able to:

- Understand Ask Mode
- Understand Agent Mode
- Understand Plan Mode
- Know when each mode should be used
- Use GitHub Copilot effectively for Manual Testing
- Use GitHub Copilot effectively for Automation Testing
- Compare outputs from different interaction modes

---

# Prerequisites

- GitHub Copilot Chat enabled
- Visual Studio Code
- Sample Testing Project
- GitHub Copilot Agent Mode enabled
- Basic knowledge of software testing

---

# Lab Scenario

You are working on an **E-Commerce Application** containing:

- Login
- Registration
- Product Search
- Shopping Cart
- Checkout
- Payment
- Order History

You will interact with GitHub Copilot using three different modes.

---

# Understanding the Three Modes

## Ask Mode

**Purpose**

Use Ask Mode when you need information, explanations, suggestions, or content generation.

Examples:

- Explain a testing concept
- Generate test cases
- Explain Selenium code
- Generate SQL queries
- Create bug reports

Think of Ask Mode as interacting with an experienced QA engineer.

---

## Agent Mode

**Purpose**

Agent Mode can perform tasks on your behalf.

Examples:

- Create automation framework
- Generate multiple files
- Refactor automation scripts
- Update existing tests
- Create Page Object classes
- Execute multi-step coding tasks

Think of Agent Mode as working with another automation engineer.

---

## Plan Mode

**Purpose**

Plan Mode analyzes your request and proposes an implementation strategy before making changes.

Examples:

- Automation framework migration
- Regression strategy
- API automation architecture
- Test planning
- Framework redesign

Think of Plan Mode as discussing the solution with an architect before implementation.

---

# Part 1 – Ask Mode

## Objective

Use Ask Mode to ask questions and generate testing artifacts.

---

## Exercise 1 – Generate Manual Test Cases

Open GitHub Copilot Chat.

Switch to **Ask Mode**.

Prompt:

```text
Generate comprehensive manual test cases for Login functionality.

Business Rules

- Username is mandatory
- Password is mandatory
- Password minimum length is 8
- Account locks after 5 failed attempts

Output should include:

- Test ID
- Preconditions
- Test Steps
- Expected Result
- Priority
```

### Expected Outcome

- Positive test cases
- Negative test cases
- Boundary value tests
- Lock account scenarios

---

## Exercise 2 – Exploratory Testing

Prompt

```text
Generate an exploratory testing checklist for the Shopping Cart feature.

Include:

- Functional Testing
- Usability
- Accessibility
- Error Handling
- Security
```

---

## Exercise 3 – Bug Report

Prompt

```text
Create a professional bug report.

Issue:

The Checkout button remains disabled after removing an applied coupon.

Include:

- Summary
- Steps
- Expected Result
- Actual Result
- Severity
- Priority
```

---

## Exercise 4 – Automation Help

Prompt

```text
Explain the Page Object Model with a Selenium Java example.
```

Observe how Ask Mode explains concepts without modifying files.

---

# Part 2 – Agent Mode

## Objective

Allow GitHub Copilot to perform development and automation tasks across your project.

---

## Exercise 5 – Generate Selenium Framework

Switch to **Agent Mode**.

Prompt

```text
Create a Selenium Java TestNG automation framework.

Requirements

- Maven
- Page Object Model
- Base Test
- WebDriver Factory
- Explicit Wait
- Utilities
- Sample Login Test

Explain every file before creating it.
```

### Observe

Agent Mode should:

- Create multiple folders
- Generate multiple Java classes
- Add reusable methods
- Build the framework structure

---

## Exercise 6 – Add Automation for Registration

Prompt

```text
Extend the existing framework by adding automation for the Registration page.

Create:

- Registration Page Object
- Registration Test
- Test Data
- Assertions

Reuse existing framework components.
```

---

## Exercise 7 – Refactor Existing Tests

Prompt

```text
Review the current Selenium tests.

Identify duplicated code.

Refactor using reusable utility methods.

Update all affected files.
```

Observe how Agent Mode analyzes and updates multiple files.

---

## Exercise 8 – API Automation

Prompt

```text
Generate REST Assured automation for the Login API.

Create:

- API Base Class
- Login Request Model
- Login Response Validation
- Positive and Negative Test Cases
```

---

# Part 3 – Plan Mode

## Objective

Use Plan Mode to analyze requirements before implementation.

---

## Exercise 9 – Automation Strategy

Switch to **Plan Mode**.

Prompt

```text
We currently have only manual testing for our e-commerce application.

Create a phased automation strategy using Selenium and TestNG.

Include:

- Framework Design
- Folder Structure
- Test Prioritization
- CI/CD Integration
- Reporting
- Maintenance Strategy

Do not generate code yet.
```

### Expected Outcome

- Project roadmap
- Automation phases
- Risk analysis
- Recommendations

---

## Exercise 10 – Framework Migration

Prompt

```text
Our Selenium Java framework needs to be migrated to Playwright.

Analyze the existing approach.

Create a migration plan.

Include:

- Challenges
- Risks
- Required changes
- Estimated effort

Do not generate code.
```

---

## Exercise 11 – Regression Planning

Prompt

```text
Create a regression testing strategy for an online shopping application.

Include:

- Smoke Suite
- Sanity Suite
- Regression Suite
- Critical Business Flows
- Automation Priorities
```

---

## Exercise 12 – API Test Planning

Prompt

```text
Analyze the following APIs:

- Login
- Product Search
- Cart
- Checkout
- Payment

Create a complete API testing plan.

Include:

- Functional Tests
- Security Tests
- Performance Tests
- Negative Tests
- Automation Recommendations

Do not generate code.
```

---

# Challenge Exercise

A new **Wishlist** feature has been introduced.

Perform the following using different modes.

### Ask Mode

Generate manual test cases.

---

### Agent Mode

Implement Playwright automation for the Wishlist feature.

---

### Plan Mode

Create an automation rollout plan for the Wishlist feature and explain how it integrates with the existing regression suite.

---

# Comparison Activity

Complete the following table after performing all exercises.

| Feature | Ask Mode | Agent Mode | Plan Mode |
|----------|-----------|------------|-----------|
| Answers Questions | ✅ | ❌ | ❌ |
| Generates Test Cases | ✅ | ✅ | ❌ |
| Creates Files | ❌ | ✅ | ❌ |
| Modifies Multiple Files | ❌ | ✅ | ❌ |
| Explains Concepts | ✅ | Limited | Limited |
| Creates Implementation Strategy | ❌ | ❌ | ✅ |
| Best for Manual Testing | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐ |
| Best for Automation Testing | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Best for Architecture | ⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ |

---

# Best Practices

## Ask Mode

✅ Ask one question at a time

✅ Provide business rules

✅ Request structured output

✅ Ask for explanations

---

## Agent Mode

✅ Clearly define the objective

✅ Review generated changes before accepting

✅ Reuse existing framework components

✅ Let the agent work across multiple files

---

## Plan Mode

✅ Use before large implementations

✅ Ask for architecture recommendations

✅ Request phased implementation

✅ Validate assumptions before coding

---

# Common Mistakes

❌ Using Ask Mode to create entire frameworks

❌ Using Agent Mode for simple conceptual questions

❌ Skipping Plan Mode for large projects

❌ Asking Agent Mode to perform unrelated tasks in one prompt

❌ Not reviewing generated code before accepting changes

---

# Reflection Questions

1. Which mode was most useful for manual testing activities?

2. Which mode saved the most time for automation development?

3. When would you use Plan Mode instead of Agent Mode?

4. How can combining Ask, Plan, and Agent modes improve your daily testing workflow?

5. Which mode would you recommend for onboarding new QA team members?

---

# Lab Summary

In this lab, you explored the three primary GitHub Copilot interaction modes and learned when to use each effectively.

### Ask Mode
- Best for learning, asking questions, generating test cases, bug reports, and understanding concepts.
- Ideal for both manual testers and automation engineers during day-to-day tasks.

### Agent Mode
- Best for executing multi-step tasks across a codebase.
- Ideal for creating automation frameworks, generating Page Objects, refactoring tests, and implementing new automation features.

### Plan Mode
- Best for analyzing requirements and designing an implementation strategy before writing code.
- Ideal for automation roadmaps, framework migrations, regression planning, and architectural decisions.

By selecting the appropriate interaction mode, QA teams can improve productivity, generate higher-quality testing artifacts, reduce repetitive work, and collaborate more effectively with GitHub Copilot throughout the software testing lifecycle.
