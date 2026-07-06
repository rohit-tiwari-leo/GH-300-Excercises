# Lab: Create a GitHub Copilot Custom Agent for Manual & Automation Testing

**Course:** GitHub Copilot for Software Testing  
 
**Duration:** 75–90 Minutes  
**Difficulty:** Intermediate  
**Audience:** Manual Testers, QA Engineers, SDETs, Automation Testers

---

# Lab Overview

GitHub Copilot can act as a specialized testing expert by creating **Custom Agents**. Instead of repeatedly explaining your role, testing standards, frameworks, and project conventions, you can build an agent that already understands your testing responsibilities.

In this lab, you will create two custom Copilot agents:

1. **Manual Testing Expert**
2. **Automation Testing Expert**

These agents will help generate:

- Test cases
- Test scenarios
- Exploratory testing checklists
- Bug reports
- Selenium automation
- Playwright automation
- API testing
- Regression suites
- Test data
- Test documentation

---

# Learning Objectives

After completing this lab, you will be able to:

- Understand GitHub Copilot Custom Agents
- Create reusable testing agents
- Define agent instructions
- Configure agent capabilities
- Use custom agents for testing tasks
- Compare outputs with generic Copilot Chat

---

# Prerequisites

- GitHub Copilot Enterprise or GitHub Copilot Business
- GitHub Copilot Chat enabled
- Visual Studio Code
- GitHub repository
- Sample web application

---

# Lab Scenario

You are working as a QA Engineer for an online shopping application.

Features include:

- Login
- Registration
- Search Products
- Shopping Cart
- Checkout
- Payment
- Order History

Instead of writing long prompts every time, you will create dedicated testing agents.

---

# Architecture

```
                   GitHub Copilot

                          │

             ┌────────────┴────────────┐

             │                         │

     Manual Testing Agent      Automation Agent

             │                         │

      Test Cases               Selenium

      Bug Reports              Playwright

      Exploratory              Cypress

      Test Plans               API Tests

      Regression               Unit Tests
```

---

# Part 1 – Create a Manual Testing Agent

---

## Step 1

Open your project in Visual Studio Code.

---

## Step 2

Open GitHub Copilot Chat.

---

## Step 3

Create a new **Custom Agent**.

Example:

```
Manual Testing Expert
```

---

## Step 4

Provide the following system instructions.

---

# Manual Testing Agent Instructions

```text
You are an experienced Senior QA Manual Tester.

Your responsibilities include:

- Functional Testing
- Regression Testing
- Smoke Testing
- Sanity Testing
- Boundary Value Analysis
- Equivalence Partitioning
- Exploratory Testing
- Security Testing
- Accessibility Testing
- Usability Testing

Always:

Generate complete manual test cases.

Include:

- Test ID
- Title
- Preconditions
- Test Steps
- Expected Result
- Priority
- Test Data

Generate positive, negative and edge cases.

Follow ISTQB testing practices.

When requirements are unclear, ask clarifying questions before generating results.

Always organize output into tables.

Do not generate automation code.
```

---

## Save the Agent

Example Name

```
Manual Testing Expert
```

---

# Exercise 1

Ask your agent

```
Generate complete manual test cases for Login functionality.

Business Rules

Username mandatory

Password mandatory

Minimum password length 8

Account locks after 5 failed attempts
```

---

Expected Output

- Functional tests
- Negative tests
- Boundary tests
- Lock account tests

---

# Exercise 2

Prompt

```
Generate exploratory testing checklist for Shopping Cart.
```

---

Expected Output

- UI Testing

- Error Handling

- Security

- Browser Compatibility

- Accessibility

---

# Exercise 3

Prompt

```
Generate a bug report.

Issue

Checkout button is disabled after removing a coupon.
```

---

Expected Output

Professional defect report.

---

# Part 2 – Create Automation Testing Agent

---

## Create Another Agent

Agent Name

```
Automation Testing Expert
```

---

# Automation Agent Instructions

```text
You are a Senior Test Automation Engineer.

Your expertise includes

- Selenium Java
- Playwright TypeScript
- Cypress
- REST Assured
- Postman
- API Testing
- TestNG
- JUnit
- Page Object Model
- BDD
- Cucumber
- CI/CD

Always generate

Production-ready automation code.

Use

Reusable methods

Explicit waits

Assertions

Page Object Model

Best coding practices

Meaningful comments

Avoid Thread.sleep()

If selectors are missing, ask for HTML before generating code.

Always explain assumptions.
```

---

Save the agent.

---

# Exercise 4

Prompt

```
Generate Selenium Java automation for Login.

Requirements

Java

TestNG

Page Object Model

Explicit Wait

Assertions
```

---

Expected Output

- Login Page

- Test Class

- Base Class

- Assertions

---

# Exercise 5

Prompt

```
Generate Playwright TypeScript automation for Product Search.

Include

Fixtures

Page Objects

Reusable methods
```

---

# Exercise 6

Prompt

```
Generate Cypress automation for Checkout.
```

---

# Exercise 7

Prompt

```
Generate REST Assured automation for Login API.

Methods

POST

Assertions

Status Code

Response Validation
```

---

# Part 3 – Compare Generic Copilot vs Custom Agent

Ask normal Copilot

```
Generate Login test cases.
```

Observe

- Generic output

---

Now ask Manual Testing Agent

```
Generate Login test cases.
```

Observe

- Structured output

- Better coverage

- More edge cases

- Better formatting

---

# Exercise 8

Compare both outputs.

Record observations.

| Criteria | Generic Copilot | Manual Testing Agent |
|-----------|----------------|----------------------|
| Test Coverage | | |
| Edge Cases | | |
| Structure | | |
| Readability | | |
| Reusability | | |

---

# Bonus Exercise

Modify your Manual Testing Agent.

Add

```
Always include

Accessibility testing

Localization testing

Performance considerations

Risk analysis
```

Run the same prompt again.

Observe the improvements.

---

# Challenge Exercise

Create a third agent.

Suggested name

```
API Testing Expert
```

Responsibilities

- API Test Cases

- OpenAPI Specification

- Postman Collections

- REST Assured

- Contract Testing

- OAuth

- JWT

- Security Testing

Generate

- Positive tests

- Negative tests

- Boundary tests

- Invalid payload tests

- Authorization tests

---

# Reflection Questions

1. How did the custom agent improve response quality?

2. Which testing tasks benefited the most?

3. How much prompt writing was reduced?

4. Would multiple specialized agents be better than one generic agent?

5. What additional instructions would you add for your team?

---

# Best Practices

✅ Create one agent per role

✅ Keep instructions specific

✅ Define expected output formats

✅ Include project standards

✅ Include testing methodologies

✅ Encourage clarifying questions

✅ Reuse agents across projects

---

# Common Mistakes

❌ One agent for every possible task

❌ Very long instructions

❌ Missing testing standards

❌ No output formatting rules

❌ Mixing manual and automation responsibilities

❌ Not defining assumptions

---

# Lab Summary

In this lab, you created two specialized GitHub Copilot Custom Agents:

### Manual Testing Expert
- Generates structured manual test cases
- Creates exploratory testing checklists
- Produces bug reports
- Applies ISTQB testing practices
- Focuses on functional, regression, accessibility, and usability testing

### Automation Testing Expert
- Generates production-ready automation code
- Supports Selenium, Playwright, Cypress, and REST Assured
- Uses Page Object Model, explicit waits, assertions, and reusable components
- Encourages best practices and maintainable automation

By creating reusable custom agents, testers can significantly reduce repetitive prompting, improve the consistency of AI-generated outputs, and accelerate both manual and automated testing workflows.
