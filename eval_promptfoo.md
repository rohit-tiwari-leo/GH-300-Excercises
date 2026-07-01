# Lab 1: Evaluating a GitHub Copilot Code Generation Prompt Using Promptfoo

## Objective

In this lab, you will learn how to evaluate a simple GitHub Copilot code generation prompt using Promptfoo.

By the end of this lab, you will be able to:

- Create a simple code-generation prompt
- Configure Promptfoo for evaluation
- Define pass/fail criteria
- Run the evaluation
- Interpret the results

**Estimated Duration:** 15 minutes

---

# Prerequisites

Before starting, ensure you have:

- Node.js installed
- GitHub Copilot access
- Promptfoo installed

Install Promptfoo if needed:

```bash
npm install -g promptfoo
```

---

# Lab Scenario

Your team wants to verify that GitHub Copilot consistently generates a Python function that reverses a string.

Instead of manually reviewing every response, you'll automate the validation using Promptfoo.

---

# Step 1: Create the Project

Create a new folder.

```text
copilot-eval-lab
```

Navigate into the folder and create the following files:

```text
copilot-eval-lab/
│
├── promptfooconfig.yaml
└── prompts.txt
```

---

# Step 2: Create the Prompt

Open **prompts.txt** and add the following prompt:

```text
Write a Python function named reverse_string that accepts a string and returns the reversed string.
```

Save the file.

---

# Step 3: Configure Promptfoo

Create a file named **promptfooconfig.yaml**.

Add the following configuration:

```yaml
description: GitHub Copilot Code Generation Evaluation

prompts:
  - file://prompts.txt

providers:
  - id: github:copilot

tests:
  - vars: {}

    assert:
      - type: contains
        value: "def reverse_string"

      - type: contains
        value: "[::-1]"
```

### What are we testing?

Promptfoo will verify that GitHub Copilot generates code that:

- Defines a function named `reverse_string`
- Uses Python slicing (`[::-1]`) to reverse the string

---

# Step 4: Run the Evaluation

Open a terminal inside the project folder.

Run:

```bash
promptfoo eval
```

Example output:

```text
Running 1 test...

✓ Passed

Prompt:
Write a Python function named reverse_string...

Assertions

✓ contains "def reverse_string"

✓ contains "[::-1]"
```

---

# Step 5: Understanding Pass and Fail

## Example 1 – PASS

Generated code:

```python
def reverse_string(text):
    return text[::-1]
```

### Why did it pass?

- Function name is correct ✅
- Uses slicing (`[::-1]`) ✅

**Result:** PASS

---

## Example 2 – FAIL

Generated code:

```python
print("Hello")
```

### Why did it fail?

The generated code does not contain the required function.

**Result:** FAIL

---

## Example 3 – FAIL

Generated code:

```python
def reverse_string(text):
    return reversed(text)
```

### Why did it fail?

Although the function works, the evaluation expected the implementation to contain:

```python
[::-1]
```

Since the expected text is missing, the test fails.

---

# Step 6: Interpreting the Results

| Assertion | Expected | Result |
|------------|----------|--------|
| Function definition | `def reverse_string` | ✅ Pass |
| Uses slicing | `[::-1]` | ✅ Pass |
| Missing function | No | ❌ Fail |
| Different implementation | No | ❌ Fail |

---

# Expected Copilot Output

```python
def reverse_string(text):
    return text[::-1]
```

---

# Lab Summary

In this lab, you:

- Created a GitHub Copilot code-generation prompt.
- Configured Promptfoo to evaluate the generated code.
- Defined pass/fail assertions.
- Executed the evaluation using `promptfoo eval`.
- Learned how to interpret the evaluation results.

This demonstrates the basic concept of **Evaluation-Driven Development (EDD)**, where AI-generated code is automatically validated against predefined quality criteria instead of relying solely on manual review.

---

# Key Takeaways

- Promptfoo automates the evaluation of AI-generated outputs.
- Assertions define what makes an output successful.
- Evaluations help ensure consistent code quality.
- Automated testing builds confidence when using GitHub Copilot in software development.
