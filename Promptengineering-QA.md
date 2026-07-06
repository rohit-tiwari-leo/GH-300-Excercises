# Lab: Writing Effective Prompts for GitHub Copilot
**Audience:** Manual Testers & Automation Testers  
**Duration:** 45–60 Minutes  
**Difficulty:** Beginner  
**Prerequisites:**
- GitHub Copilot enabled in Visual Studio Code
- GitHub Copilot Chat extension installed
- Basic understanding of testing concepts

---

# Lab Objective

In this lab, you will learn how to write **effective prompts** for GitHub Copilot using the **4S Prompting Framework**.

By the end of this lab, you will be able to:

- Write prompts that generate better results
- Reduce unnecessary back-and-forth with Copilot
- Generate manual test cases faster
- Generate automation scripts with higher accuracy
- Understand why some prompts work better than others

---

# Learning Outcomes

After completing this lab, participants will be able to:

- Apply the 4S prompting framework
- Convert vague prompts into effective prompts
- Generate manual testing artifacts
- Generate automation code
- Refine prompts based on Copilot responses

---

# The 4S Prompting Framework

An effective GitHub Copilot prompt should follow four principles.

| Principle | Description |
|------------|-------------|
| **Single** | Ask Copilot to perform one task at a time |
| **Specific** | Clearly describe requirements, expected output, constraints, technologies, etc. |
| **Short** | Keep prompts concise and avoid unnecessary information |
| **Surround (Context)** | Provide surrounding code, requirements, UI flow, APIs, or business rules |

Think of it as:

> **One Task + Clear Details + Short Prompt + Enough Context**

---

# Why This Matters

Poor Prompt

> Write test cases.

Copilot has no idea:

- Which application?
- Which feature?
- Positive or negative?
- UI or API?
- Functional or Security?

Result:
Generic output.

---

Good Prompt

> Generate positive and negative manual test cases for a login page containing Username, Password and Login button. Include Preconditions, Steps, Expected Result and Priority.

Result:
Much better and more usable output.

---

# Exercise 1 — Single

## Objective

Learn to ask one task at a time.

---

## Poor Prompt

```
Generate test cases, automation scripts, bug report, API tests and performance scenarios for Login.
```

Problem

Too many requests in one prompt.

---

## Better Prompt

```
Generate positive and negative manual test cases for the Login page.
```

---

## Your Task

Open GitHub Copilot Chat.

Ask:

```
Generate manual test cases for a password reset page.
```

---

### Observe

Did Copilot stay focused?

---

## Challenge

Now ask

```
Generate automation code also.
```

Notice how Copilot starts mixing outputs.

---

# Exercise 2 — Specific

## Objective

Provide detailed requirements.

---

## Poor Prompt

```
Write Selenium tests.
```

---

## Better Prompt

```
Generate Selenium Java TestNG test cases for a Login page with Username, Password and Login button.

Use:
- Selenium WebDriver
- Java
- TestNG
- Page Object Model
- Explicit Wait
- Assertions
```

---

### Observe

Notice how Copilot generates:

- Better class structure
- Imports
- Assertions
- Better waits

---

# Exercise 3 — Short

## Objective

Avoid long unnecessary prompts.

---

## Poor Prompt

```
I am working on an application that was developed by my company last year. My manager has asked me to automate the login feature because users are facing issues...
```

Very long.

---

## Better Prompt

```
Generate Playwright TypeScript automation for Login page using Page Object Model.
```

---

## Your Task

Rewrite this prompt in under 30 words.

```
Generate test automation for Login page using Cypress including assertions and reusable methods.
```

---

# Exercise 4 — Surround (Context)

## Objective

Provide surrounding context.

Copilot performs much better when it sees nearby code.

---

## Example HTML

```html
<form>

<input id="username">

<input id="password">

<button id="login">

Login

</button>

</form>
```

---

## Poor Prompt

```
Write Selenium code.
```

---

## Better Prompt

```
The following HTML belongs to a Login page.

Generate Selenium Java Page Object Model code using these element IDs.

(username,password,login)
```

---

Notice how Copilot uses the correct locators.

---

# Manual Tester Exercises

---

# Exercise 5 — Generate Test Cases

Requirement

```
Feature:
User Login

Fields

Username

Password

Login button

Business Rules

Username mandatory

Password mandatory

Password minimum 8 characters

Account locks after 5 failed attempts
```

---

Prompt

```
Generate positive and negative manual test cases.

Output should include:

Test ID

Title

Preconditions

Steps

Expected Result

Priority
```

---

Expected Outcome

- Positive tests
- Boundary tests
- Validation tests
- Lock account scenarios

---

# Exercise 6 — Exploratory Testing

Prompt

```
Create an exploratory testing checklist for Login functionality.

Focus on:

Usability

Accessibility

Security

Error handling

Cross-browser testing
```

---

Expected Output

- Checklist
- Risks
- Exploratory ideas

---

# Exercise 7 — Bug Report

Scenario

```
Password accepts only six characters but requirement says minimum eight.
```

Prompt

```
Generate a professional bug report.

Include:

Summary

Environment

Steps

Expected Result

Actual Result

Severity

Priority
```

---

# Exercise 8 — Boundary Value Analysis

Prompt

```
Generate Boundary Value Analysis test cases for Password field.

Rules

Minimum length = 8

Maximum length = 20
```

---

Expected

- 7
- 8
- 9
- 19
- 20
- 21

---

# Automation Tester Exercises

---

# Exercise 9 — Selenium

Prompt

```
Generate Selenium Java TestNG automation for Login page.

Requirements

Page Object Model

Explicit Wait

Assertions

Reusable methods
```

---

# Exercise 10 — Playwright

Prompt

```
Generate Playwright TypeScript automation for Login page.

Use:

Fixtures

Page Objects

Expect Assertions

Reusable methods
```

---

# Exercise 11 — Cypress

Prompt

```
Generate Cypress automation for Login page.

Include:

Fixtures

Custom Commands

Assertions

Reusable methods
```

---

# Exercise 12 — API Testing

Requirement

```
POST /login

Body

email

password

Returns

200

401

400
```

Prompt

```
Generate Postman API test cases for Login API.

Include:

Positive

Negative

Boundary

Authorization

Invalid payload

Assertions
```

---

# Bonus Exercise — Improve the Prompt

Below are poor prompts.

Rewrite them using the 4S Framework.

---

Prompt 1

```
Write tests.
```

---

Prompt 2

```
Create automation.
```

---

Prompt 3

```
Generate login tests.
```

---

Prompt 4

```
Help me test this application.
```

---

# Reflection Questions

1. Which prompts produced the best output?

2. How did adding context improve Copilot's response?

3. Was a shorter prompt easier for Copilot to understand?

4. Did asking a single task reduce hallucinations?

5. Which principle had the biggest impact?

---

# Best Practices

✅ Ask one task at a time

✅ Mention framework and language

✅ Mention expected output format

✅ Include requirements

✅ Provide surrounding code

✅ Keep prompts under 3–5 lines

✅ Refine prompts iteratively

---

# Common Mistakes

❌ Asking multiple tasks together

❌ No application context

❌ Missing business rules

❌ Extremely long prompts

❌ No expected output format

❌ No technology specified

---

# Lab Summary

In this lab you learned how to create high-quality GitHub Copilot prompts using the **4S Prompting Framework**:

- **Single** – Focus on one clear task.
- **Specific** – Provide explicit requirements, technologies, and expected output.
- **Short** – Keep prompts concise and easy to understand.
- **Surround (Context)** – Include relevant code, requirements, or business rules to improve Copilot’s suggestions.

By consistently applying these principles, both manual and automation testers can generate more accurate test cases, higher-quality automation code, structured bug reports, and other testing artifacts while reducing prompt iterations and improving overall productivity.
