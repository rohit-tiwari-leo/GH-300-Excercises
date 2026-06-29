# GitHub Copilot Lab — Prompt Engineering Best Practices

## Objective

This lab teaches how to write effective prompts for GitHub Copilot using four key principles:

- **Single** → One clear task
- **Specific** → Clear requirements and constraints
- **Short** → Concise and focused
- **Surround (Context)** → Provide relevant code or context

By the end of this lab you will also be able to:

- Write **reproducible, scope-safe prompts** that produce consistent output across multiple runs
- **Identify prompt anti-patterns** that lead to UAT regression, unintended file changes, and broken test suites

---

## Prerequisites

- Visual Studio Code with GitHub Copilot and GitHub Copilot Chat extensions installed and signed in
- Python 3.10+ available in your terminal (`python --version`)
- A working Git repository for tracking changes
- Basic knowledge of Python and REST API concepts

---

# SECTION 1 — SINGLE (One Task at a Time)

## Goal: Avoid combining multiple tasks in one prompt

Combining multiple tasks in one prompt forces Copilot to make assumptions about priority, order, and scope. Each assumption is a potential regression point.

---

### ❌ Poor Prompt

```
Create an API, add authentication, connect to database, and write tests
```

**Why this is dangerous:**

- Copilot decides which framework to use (Flask? FastAPI? Django?)
- Authentication logic may be injected into files that shouldn't own it
- Database connection strings may be hardcoded
- Generated tests may overwrite or conflict with existing ones
- A single prompt produces 4 unreviewed feature areas simultaneously

**Anti-pattern:** *Task bundling* — combining unrelated concerns in a single prompt causes Copilot to generate code that spans multiple files and layers without a defined scope boundary.

---

### ✅ Good Prompt

```
Create a GET endpoint /users in FastAPI that returns a hardcoded list of users
```

**Why this works:**

- One framework, one endpoint, one behaviour
- No side effects on auth, database, or tests
- Output is predictable and reviewable in under a minute

---

### Hands-on Task

#### Step 1 — Set up the lab file

Create `user_api.py` and add this starting code:

```python
# user_api.py
from fastapi import FastAPI

app = FastAPI()

# Lab Exercise 1 — add your endpoint below this line
```

#### Step 2 — Apply the prompt

Type the following comment on the next line and let Copilot complete it:

```python
# Create a POST endpoint /users that accepts name and email and returns HTTP 201 Created
```

#### Step 3 — Scope check

Before accepting the suggestion, verify:

- [ ] Did Copilot add any imports beyond `fastapi`?
- [ ] Did it touch anything above the comment line?
- [ ] Is the response limited to a single endpoint?

Run a git diff to confirm only `user_api.py` was modified:

```bash
git diff --stat HEAD
```

> **Expected:** Only `user_api.py` in the diff. Any other file = scope violation.



---

# SECTION 2 — SPECIFIC (Clear Requirements)

## Goal: Provide detailed and unambiguous instructions

Vague prompts produce plausible-looking code that may not match your actual requirements — and will often pass a casual review before failing in UAT.

---

### ❌ Poor Prompt

```
Create a user API
```

**Anti-patterns embedded in this prompt:**

| Anti-pattern | Risk |
|---|---|
| No framework specified | Copilot may choose Django, Flask, or FastAPI — potentially conflicting with your project |
| No field definition | Generated fields (`id`, `username`, `password`?) may not match your schema |
| No response format | JSON assumed but not enforced — structure may vary |
| No error handling | 404 / 422 / 500 behaviour left to Copilot's discretion |
| No scope boundary | Copilot may generate a full project structure, models, and database config |

**Regression risk:** If this prompt generates a `models.py` or `database.py` that conflicts with existing files, your application may silently break at import time — often not caught until integration testing.

---

### ✅ Good Prompt

```
Create a FastAPI PUT endpoint /users/{user_id} that updates name and email.
Use a Pydantic model for the request body. Return 404 with detail message if user not found.
Do not add any database connection — use an in-memory dict called USER_STORE.
```

**Why this works:**

- Framework is locked (FastAPI)
- Request body structure is explicit (Pydantic model)
- Error handling is specified (404 + detail message)
- Storage mechanism is defined and scoped (in-memory dict, not a new DB file)
- No side effects on other files

---

### Hands-on Task

#### Step 1 — Write a specific, scope-safe prompt

Add the following to `user_api.py` beneath your Exercise 1 code:

```python
# USER_STORE: in-memory store for lab exercises — do not replace with a database
USER_STORE = {
    1: {"id": 1, "name": "Alice", "email": "alice@example.com"},
    2: {"id": 2, "name": "Bob",   "email": "bob@example.com"},
}

# Task: Create a PUT endpoint /users/{user_id} to update name and email
# Scope: This function only — do not modify USER_STORE definition or any endpoint above
# Constraint: Use a Pydantic BaseModel for the request body
#             Return HTTP 404 with detail="User not found" if user_id not in USER_STORE
#             Return the updated user dict with HTTP 200
#             Do NOT add any import that is not already in this file
```

#### Step 2 — Validate specificity produced correct output

Check each requirement against the generated code:

- [ ] Pydantic `BaseModel` used for request body?
- [ ] `USER_STORE` referenced (not a new variable)?
- [ ] 404 returned when user not in store?
- [ ] 200 returned with updated user data?
- [ ] No new imports added?
- [ ] No other endpoints modified?

#### Step 3 — Identify the anti-pattern in this prompt and fix it

The following prompt was used by a developer last sprint and caused a P1 regression:

```
Add error handling to the user API
```

**Exercise:** In your worksheet, answer:

1. Which files could Copilot modify with this prompt?
2. Could it remove or change existing error handling?
3. What assumptions does Copilot make about which errors to handle?
4. Rewrite this prompt so it is specific, scoped, and non-destructive.

**Reference safe rewrite:**

```python
# Task: Add a try/except block inside the existing get_user() function only
# Scope: get_user() function — lines inside this function, no other function
# Constraint: Catch KeyError only — do not add a broad Exception handler
#             Return HTTP 404 with detail="User {user_id} not found"
#             Do not change the function signature or any other function
```

---

# SECTION 3 — SHORT (Concise Prompts)

## Goal: Avoid unnecessary verbosity — length does not equal quality

Verbose prompts introduce ambiguity. When a prompt contains contradictory qualifiers or multiple implied requirements, Copilot must resolve the conflict — and its resolution may not match yours.

---

### ❌ Poor Prompt

```
I am building a very large enterprise-grade scalable Python microservice and I need you
to help me generate a simple API endpoint which should ideally return a list of users
in JSON format and should be written using FastAPI with best practices and also include
proper error handling and maybe some logging as well if possible
```

**Anti-patterns in this prompt:**

| Phrase | Problem |
|---|---|
| "enterprise-grade scalable" | Copilot may add dependency injection, middleware, or config layers |
| "ideally" | Signals optionality — Copilot may or may not include it |
| "best practices" | Undefined standard — may generate logging, tracing, metrics you don't want |
| "maybe some logging as well if possible" | Copilot will add logging — now you own log format decisions you didn't make |
| Compound sentence structure | Multiple implied tasks in one sentence |

**Regression risk:** The phrase "best practices" alone can cause Copilot to add `structlog`, `opentelemetry`, or custom middleware imports — breaking existing apps that don't have those dependencies installed.

---

### ✅ Good Prompt

```
Create a GET /users endpoint in FastAPI returning a JSON list from USER_STORE
```

Eleven words. One task. One file. One return value. No ambiguity.

---

### Hands-on Task

#### Step 1 — Short prompt, clean output

Add this comment to `user_api.py` and accept Copilot's suggestion:

```python
# Create a DELETE /users/{user_id} endpoint — return 204 on success, 404 if not found
```

#### Step 2 — Validate conciseness produced a clean result

- [ ] Is the generated function under 15 lines?
- [ ] Are there any imports you didn't expect?
- [ ] Is there any logging, middleware, or decorator Copilot added on its own?
- [ ] Does it reference `USER_STORE` from the existing context?

#### Step 3 — Trim a verbose prompt

The following prompt was submitted by a developer during a sprint. Rewrite it as a short, scope-safe prompt (target: under 20 words):

**Original verbose prompt:**
```
I want to add some kind of validation to make sure that whenever someone is trying to
create a new user using the POST endpoint, the email address they provide is actually
a valid email address format and also the name should not be empty or blank and if
either of these conditions is not met then we should return an appropriate error response
```

**Your rewritten prompt (write in your worksheet before checking the reference):**

```
# Reference answer — attempt your own first
# Task: Add input validation to the POST /users endpoint only
# Constraint: Email must match basic format (contains @ and .)
#             Name must be a non-empty string
#             Return HTTP 422 with field-level error detail for each violation
#             Do NOT add any external validation library — use Pydantic field validators only
```

#### Step 4 — Reproducibility test for short prompts

Short, precise prompts produce more reproducible output. Test this:

1. Accept the DELETE endpoint from Step 1
2. Undo (`Ctrl+Z`)
3. Trigger Copilot three times on the same short prompt
4. Are all three structurally identical?

Compare this to the reproducibility results from Section 1. Record the difference in your worksheet.

---

# SECTION 4 — SURROUND (Provide Context)

## Goal: Improve output quality by providing relevant surrounding code and types

Copilot generates code relative to the context it can see. The more relevant context is visible, the more accurate and scope-consistent the suggestion.

---

### ❌ Poor Prompt (no context)

```python
# Add validation
```

**What Copilot sees:** A blank comment. It has no information about:

- What is being validated
- Which function this applies to
- What types the inputs are
- What the error response format should be
- Whether a validation library is already in use

**Anti-pattern:** *Context starvation* — prompting Copilot without surrounding code forces it to invent context. Invented context means invented imports, invented variable names, and invented error formats that may conflict with the rest of the codebase.

---

### ✅ Good Prompt (with context)

```python
from pydantic import BaseModel, EmailStr, validator

class UserCreate(BaseModel):
    name: str
    email: str

    # Add a validator to ensure name is not empty and email contains '@'
```

Copilot now has:

- The exact class it is extending
- The field names and types it must work with
- The import context (Pydantic, not marshmallow or cerberus)
- A precise, scoped task (validator methods on this class only)

---

### Hands-on Task

#### Step 1 — Context-free prompt (observe the problem)

In a new scratch file `scratch.py`, type only:

```python
# Add validation and return 400 if invalid
```

Accept the suggestion. Record what Copilot invented:

- Which framework did it assume?
- What variable names did it create?
- What does "invalid" mean to Copilot here?

This is context starvation in action.

#### Step 2 — Context-rich prompt (observe the improvement)

Now open `user_api.py` and add the following block, then trigger Copilot on the comment:

```python
from pydantic import BaseModel
from fastapi import FastAPI, HTTPException

app = FastAPI()

USER_STORE: dict[int, dict] = {
    1: {"id": 1, "name": "Alice", "email": "alice@example.com"},
}

class UserCreate(BaseModel):
    name: str
    email: str

@app.post("/users", status_code=201)
def create_user(user: UserCreate):
    # Validate: name must be non-empty, email must contain '@'
    # Return HTTP 400 with detail message for each violation
    # If valid, add to USER_STORE with auto-incremented id and return the new user
```

**What context Copilot now has:**

| Context element | Why it matters |
|---|---|
| `UserCreate` Pydantic model | Knows the field names and types |
| `USER_STORE` dict definition | Knows the storage structure to write to |
| `HTTPException` import | Will use this for 400 — not `abort()` or `raise ValueError` |
| `status_code=201` on the route | Knows the success response is already defined |
| Existing endpoint pattern above | Will match the same code style |

#### Step 3 — Context checklist before every prompt

Before writing any Copilot prompt, verify the surrounding context includes:

- [ ] All imports the generated code will need (already present in the file)
- [ ] The data model or type definitions for variables the code will use
- [ ] Any shared state (like `USER_STORE`) that the function will read or write
- [ ] At least one example of existing code in the same style
- [ ] The function or class signature if Copilot is completing a body

**Missing any of these?** Add them above your comment before triggering Copilot.

#### Step 4 — Surround context and scope safety

Context also enforces scope. When Copilot can see `USER_STORE` already defined, it is less likely to generate a new database connection. When it can see `HTTPException` imported, it uses that rather than inventing a new error class.

Test this: remove the `USER_STORE` line from context and re-trigger the same prompt. Did Copilot attempt to create a database connection or a new storage variable?

Record in your worksheet: **How did removing context change the generated output?**

---

# SECTION 5 — Reproducible, Scope-Safe Prompts

## Goal: Write prompts that produce consistent, predictable output every time

A prompt is **reproducible** if running it three times produces three structurally equivalent suggestions. A prompt is **scope-safe** if it cannot cause Copilot to modify files, functions, or behaviour outside the defined boundary.

---

## The Scope-Safe Prompt Template

Every prompt you write in this team must follow this structure:

```python
# Task:       [Verb] + [what] + [expected behaviour]
# Scope:      [This file only / this function only / lines N–M only]
# Constraint: [What NOT to do — imports, other functions, patterns to avoid]
# Format:     [Return type, error handling style, naming convention]
```

Not all four fields are needed for every prompt, but **Scope** and **Constraint** are always required for any prompt that touches existing code.

---

## Anti-Pattern Catalogue

The following anti-patterns have caused regressions in this codebase. Recognise them and refuse to use them.

---

### Anti-Pattern 1 — The Whole-File Rewrite

```python
# Refactor this entire file to use best practices
```

**What goes wrong:** Copilot rewrites function signatures, changes variable names, adds new imports, and restructures logic — often in ways that are syntactically correct but behaviourally different. Tests that relied on specific function signatures silently break.

**Regression signal:** Tests fail with `TypeError: function() takes 2 positional arguments but 3 were given` or import errors from renamed functions.

**Safe replacement:**

```python
# Task: Rename local variables inside calculate_discount() to follow snake_case
# Scope: calculate_discount() function only — lines 42–58
# Constraint: Do NOT change function signature, return type, or logic
#             Do NOT modify any other function in this file
```

---

### Anti-Pattern 2 — The Ghost Fix

```python
# Fix the bug
```

**What goes wrong:** Copilot has no idea which bug you mean. It will pattern-match on surrounding code and apply a plausible-looking fix that may change working code. The actual bug may remain unfixed.

**Regression signal:** A different test suite starts failing after the "fix" is applied. The original failing test may now pass, masking the fact that other behaviour changed.

**Safe replacement:**

```python
# Task: Fix the KeyError in get_user_by_email() when email is not in USER_STORE
# Scope: get_user_by_email() function only
# Constraint: Add a .get() call with a None default — do not restructure the function
#             Do not change how the caller handles the return value
```

---

### Anti-Pattern 3 — The Test Eraser

```python
# Make the tests pass
```

**What goes wrong:** The fastest way to make a failing test pass is to delete it or mock it out. Copilot knows this. It will mock real calls, weaken assertions (`assert result is not None` instead of `assert result == 42`), or skip edge cases entirely.

**Regression signal:** All tests show green in CI but production returns wrong values. Coverage report shows uncovered branches that were previously tested.

**Safe replacement:**

```python
# Task: Fix calculate_tax() so the test "returns 0 for tax-exempt items" passes
# Scope: calculate_tax() function in tax_calculator.py only
# Constraint: Do NOT modify test files. Do NOT mock any function.
#             The fix must be in the business logic, not in the test setup.
```

---

### Anti-Pattern 4 — The Vague Validator

```python
# Add validation
```

**What goes wrong:** Copilot applies validation everywhere it sees an opportunity — adding required field checks, type guards, and length constraints across multiple functions. It may add a third-party library (`cerberus`, `voluptuous`) that isn't installed.

**Regression signal:** `ModuleNotFoundError` in production. Existing valid inputs rejected by new constraints. Other functions now raise exceptions where they previously returned defaults.

**Safe replacement:**

```python
# Task: Add input validation to create_product() only
# Scope: create_product() function — do not touch update_product() or delete_product()
# Constraint: Use only built-in Python — no external validation library
#             Validate: name (non-empty str), price (positive float), category (one of: 'books', 'electronics', 'clothing')
#             Raise ValueError with a descriptive message for each violation
```

---

### Anti-Pattern 5 — The Schema Migrator

```python
# Update the database schema
```

**What goes wrong:** Copilot may generate a migration that drops columns, renames tables, or modifies existing migrations — none of which are reversible in production without downtime.

**Regression signal:** `OperationalError: no such column` in production after deployment. Existing data silently dropped.

**Safe replacement:**

```python
# Task: Generate a new Alembic migration to ADD a nullable column 'last_login_at' (DateTime) to the users table
# Scope: New migration file only — do NOT modify existing migration files or the User model
# Constraint: Migration must be reversible — include both upgrade() and downgrade()
#             Do NOT alter, rename, or drop any existing column
```

---

## Reproducibility Test

Run this exercise to validate your prompts are reproducible.

### Step 1

Write a scope-safe prompt for this task:

> Add a `get_user_by_email(email: str)` function to `user_api.py` that looks up a user in `USER_STORE` by email value. Return the user dict or raise `HTTPException(404)` if not found. Do not modify any existing function.

Write your prompt in your worksheet using the four-part template.

### Step 2

Trigger Copilot three times on your prompt (accept → undo → trigger again). Collect the three outputs.

### Step 3

Compare across all three runs:

| Criterion | Run 1 | Run 2 | Run 3 |
|---|---|---|---|
| Function name matches spec? | | | |
| Iterates over `USER_STORE.values()`? | | | |
| Raises `HTTPException(404)`? | | | |
| No new imports added? | | | |
| No other function modified? | | | |

A well-written scope-safe prompt should score 5/5 on all three runs. If any run scores below 4/5, tighten your `Constraint` field and repeat.

---

# Summary

Effective prompt engineering dramatically improves GitHub Copilot output quality, reproducibility, and safety. By following these four principles and the scope-safe template, developers can:

- Reduce ambiguity and prompt-driven regressions
- Get accurate, predictable code suggestions across multiple runs
- Keep AI-generated changes within a defined, reviewable boundary
- Protect existing tests, schemas, and function signatures from unintended modification

---

## Quick Reference — The Four Principles

| Principle | Rule | Anti-pattern to avoid |
|---|---|---|
| **Single** | One task per prompt | Task bundling — combining auth + DB + tests in one prompt |
| **Specific** | Name the framework, fields, error codes, and constraints explicitly | "Create a user API" — Copilot decides everything |
| **Short** | Target under 25 words for inline prompts | "enterprise-grade scalable best practices" — triggers scope creep |
| **Surround** | Ensure imports, types, and shared state are visible above the prompt | Context starvation — prompting on a blank file |

## Quick Reference — Scope-Safe Prompt Template

```python
# Task:       [Verb] + [what to build] + [expected behaviour]
# Scope:      [Exact file, function, or line range — nothing else]
# Constraint: [What NOT to do, what NOT to import, what NOT to modify]
# Format:     [Return type, error style, naming convention]
```

## Quick Reference — Anti-Pattern Red Flags

If your prompt contains any of these phrases, rewrite it before using it:

| Red flag phrase | Why it's dangerous |
|---|---|
| `refactor this entire file` | No scope boundary — everything is at risk |
| `fix the bug` | No bug specified — Copilot guesses |
| `make the tests pass` | Copilot may delete or weaken tests |
| `add validation` | Applied everywhere, may add new libraries |
| `update the schema` | May drop or rename existing columns |
| `best practices` | Undefined standard — triggers scope creep |
| `and also` | Multiple tasks — split into separate prompts |
| `if possible` | Signals optionality — Copilot will include it |

---

*Lab version 2.0 — Python edition with scope-safe prompts and anti-pattern catalogue*
