
# Module 06 - Lab 01
# Authoring a Reusable `SKILL.md` for Data Validation and Invoking it from GitHub Copilot Chat

## Lab Overview

**Module:** M6 – Reusable Skills and Repository Instructions

**Lab Duration:** 35–45 Minutes

**Difficulty:** Intermediate

---

## Lab Objectives

By the end of this lab, you will be able to:

- Understand the purpose of reusable `SKILL.md` files.
- Create a reusable data validation skill.
- Organize skills inside a repository.
- Invoke the skill from GitHub Copilot Chat.
- Validate Copilot responses using the custom skill.

---

## Scenario

Your development team is building an **Order Management System**.

Developers repeatedly ask GitHub Copilot to validate incoming customer records before they are processed. Instead of rewriting the prompt every time, the team wants to create a reusable skill that standardizes validation rules.

The reusable skill should verify:

- Customer Name
- Email Address
- Phone Number
- Country
- Postal Code
- Order Amount

The skill should return:

- Validation Result
- Errors
- Warnings
- Suggested Fixes

---

# Prerequisites

- Visual Studio Code
- GitHub Copilot and Copilot Chat enabled
- GitHub account
- Sample project folder

Example:

```text
OrderManagement/
```

---

# Exercise 1 – Create the Skill Folder

Inside your repository create the following structure.

```text
OrderManagement/
│
├── .github/
│   └── skills/
│       └── data-validation/
│           └── SKILL.md
│
└── src/
```

---

# Exercise 2 – Create the Skill

Create a file named:

```text
.github/skills/data-validation/SKILL.md
```

Add the following content.

````markdown
# Data Validation Assistant

## Purpose

Validate incoming customer and order information before processing.

## Validation Rules

### Customer Name

- Required
- Minimum 3 characters

### Email

- Required
- Must follow RFC compliant email format

### Phone

- Country code required

### Country

Allowed values

- India
- USA
- UK
- Canada
- Australia

### Postal Code

Validate according to country.

### Order Amount

- Must be greater than 0
- Warn if greater than 100000

## Response Format

### Validation Status

PASS or FAIL

### Errors

List all validation failures.

### Warnings

List non-blocking issues.

### Recommendations

Suggest corrected values whenever possible.
````

Save the file.

---

# Exercise 3 – Open Copilot Chat

Open GitHub Copilot Chat in Visual Studio Code.

Ask:

```text
Validate the following customer order using the data-validation skill.

Customer Name: John

Email: john.gmail.com

Phone: 9876543210

Country: India

Postal Code: ABC123

Order Amount: -250
```

---

# Exercise 4 – Observe the Response

A typical response should include:

- Invalid email format
- Missing country code in phone number
- Invalid postal code
- Negative order amount

Example:

```text
Validation Status : FAIL

Errors

• Email format invalid

• Phone number missing country code

• Postal Code invalid

• Order Amount must be greater than zero

Warnings

None

Recommendations

john@gmail.com

+91 9876543210

Valid Indian PIN

Positive Order Amount
```

---

# Exercise 5 – Test Another Record

Try another prompt.

```text
Customer Name: Alice Smith

Email: alice@example.com

Phone: +1 9876543210

Country: USA

Postal Code: 90210

Order Amount: 450
```

Expected result:

```text
Validation Status : PASS
```

---

# Validation Checklist

- Repository contains the skill.
- Copilot recognizes the validation instructions.
- Invalid records produce errors.
- Valid records pass validation.

---

# Challenge Exercise

Extend the skill to validate:

- GST Number
- PAN Number
- Currency Code
- Order Date
- Shipping Address

Test the updated skill with additional prompts.

---

# Key Takeaways

In this lab you learned how to:

- Build a reusable `SKILL.md`
- Store skills in a repository
- Standardize Copilot prompts
- Improve response consistency across the development team

---

## Expected Outcome

You successfully created a reusable GitHub Copilot skill that validates customer and order data and can be invoked from Copilot Chat to produce consistent, structured validation results.
