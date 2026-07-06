# Lab: Using GitHub Copilot Prompt Files

## Course
GitHub Copilot for Manual & Automation Testing

**Duration:** 45 Minutes

**Difficulty:** Intermediate

**Audience**

- Manual Test Engineers
- Automation Test Engineers
- QA Engineers
- SDETs

---

# Lab Objective

In this lab, you will learn how to create and use **GitHub Copilot Prompt Files** to standardize common testing activities.

Instead of repeatedly typing the same prompts, you will create reusable prompt files that your entire QA team can use.

By the end of this lab, you will be able to:

- Create Prompt Files
- Store Prompt Files inside your repository
- Use Prompt Files for Manual Testing
- Use Prompt Files for Automation Testing
- Improve consistency across your team
- Reduce repetitive prompting

---

# Prerequisites

- Visual Studio Code
- GitHub Copilot Chat
- GitHub Copilot Prompt Files enabled
- Sample Testing Project

---

# Lab Scenario

You are working on an **E-Commerce Web Application**.

Features include

- Login
- Registration
- Product Search
- Shopping Cart
- Checkout
- Payment
- Order History

Your QA team performs repetitive tasks every day.

Instead of writing prompts repeatedly, you will build reusable Prompt Files.

---

# Repository Structure

```
.github
└── prompts
    ├── manual-test-cases.prompt.md
    ├── exploratory-testing.prompt.md
    ├── bug-report.prompt.md
    ├── selenium-generator.prompt.md
    ├── playwright-generator.prompt.md
    ├── api-testing.prompt.md
    ├── code-review.prompt.md
    └── regression-suite.prompt.md
```

---

# Exercise 1 – Create Your First Prompt File

## Objective

Create a reusable prompt for generating manual test cases.

---

### Step 1

Create the following folder

```
.github/prompts
```

---

### Step 2

Create a file

```
manual-test-cases.prompt.md
```

---

### Step 3

Add the following content

````text
# Manual Test Case Generator

## Goal

Generate comprehensive manual test cases.

Include

- Positive Tests
- Negative Tests
- Boundary Value Tests
- Validation Tests

Output Format

- Test ID
- Title
- Preconditions
- Test Steps
- Expected Result
- Test Data
- Priority

Follow ISTQB Best Practices.

Ask clarifying questions if requirements are incomplete.
