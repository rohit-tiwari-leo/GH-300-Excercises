# GitHub Copilot Capstone — End-to-End AI-Assisted Development

> **Scope:** Code generation · Debugging · Refactoring · Test generation · Documentation · Commit/PR summary · Manual vs. agentic comparison · PROPTFOO eval scorecard

---

## Problem context

### The scenario

You are a mid-level developer on a fintech startup's backend team. You've inherited a poorly documented, partially-broken **expense-tracking microservice** written in Python (FastAPI). It has no tests, inconsistent error handling, undocumented endpoints, and a known bug where duplicate transactions are silently inserted.

Your task: use GitHub Copilot at every stage to bring this service to production-readiness — then evaluate your output rigorously using the PROPTFOO eval suite.

**Starter repo includes:**
- `main.py` — FastAPI application with incomplete and inconsistent endpoints
- `models.py` — SQLAlchemy models with missing constraints
- `db.py` — database session management with N+1 query issues

> **Important:** Do not fix anything before your assigned phase begins. The broken state is intentional and is part of the evaluation.

---

## Capstone phases

### Phase 1 — Code generation `[blue]`

Use Copilot to generate **three missing CRUD endpoints** and a **transaction deduplication helper** from docstring prompts only.

**Deliverables:**
- `POST /transactions`, `GET /transactions/{id}`, `DELETE /transactions/{id}` endpoints
- `deduplicate_transaction()` helper with inline docstring
- Prompt log: record every Copilot prompt used and whether the suggestion was accepted, modified, or rejected

---

### Phase 2 — Debugging `[amber]`

Use Copilot Chat to identify and fix the **silent duplicate-insert bug** and a **broken pagination query**. Log your reasoning steps.

**Deliverables:**
- Fixed `main.py` with both bugs resolved
- A debugging journal (plain text or markdown): what you asked Copilot, what it said, where it was right or wrong
- Before/after diff committed to a `fix/duplicate-insert` branch

---

### Phase 3 — Refactoring `[purple]`

Refactor `db.py` to remove N+1 queries, extract a service layer, and apply dependency injection — using Copilot suggestions.

**Deliverables:**
- New `services/transaction_service.py` module
- Updated `db.py` with eager loading via SQLAlchemy `joinedload`
- Dependency-injected session passed via FastAPI `Depends()`
- Before/after EXPLAIN query output demonstrating improvement (or neutral impact)

---

### Phase 4 — Test generation `[green]`

Generate a pytest suite covering happy paths, edge cases, and the deduplication logic. Target **≥ 85% branch coverage**.

**Deliverables:**
- `tests/test_transactions.py` with pytest fixtures and parametrized cases
- `pytest-cov` HTML report showing branch coverage %
- At least one test explicitly covering the deduplication edge case
- At least one test for the previously broken pagination query

---

### Phase 5 — Documentation `[red]`

Generate OpenAPI docstrings, a README, and an architecture decision record (ADR) for the service layer — all via Copilot.

**Deliverables:**
- Inline OpenAPI docstrings on all endpoints (rendered in `/docs`)
- `README.md` with: setup instructions, environment variables, API overview, known limitations
- `docs/adr-001-service-layer.md` following the MADR template

---

### Phase 6 — Commit & PR summary `[blue]`

Use Copilot to write **atomic commit messages** and a structured **PR description** including summary, test plan, and risk notes.

**Deliverables:**
- Commit history following [Conventional Commits](https://www.conventionalcommits.org/) spec (`feat:`, `fix:`, `refactor:`, `test:`, `docs:`)
- PR description with sections: Summary, Changes, Test plan, Risk / rollback notes
- All commits squashed or grouped logically before PR creation

---

## Capstone extension — manual vs. agentic comparison

This extension uses **Phase 2 (debugging)** as the comparison unit — it's the most cognitively demanding phase and the clearest place to measure where agentic tooling adds or subtracts value.

### Manual baseline

1. Complete Phase 2 (debugging) without any AI tools — no Copilot, no ChatGPT, no search-engine-assisted code paste
2. Record time to resolution (start → passing tests)
3. Document your reasoning process in a plain-text journal
4. Measure: lines of code changed, number of attempts, tests introduced

### Agentic with Copilot

1. Repeat Phase 2 in a **fresh branch** using Copilot Chat and Copilot Workspace
2. Record: time to resolution, all prompts used, suggestion acceptance rate
3. Note explicitly where Copilot was wrong or required correction
4. Capture all prompt text verbatim for eval input

### Comparison deliverable

A written reflection (**400–600 words**) comparing:

- Time-to-completion
- Defect density in the output (bugs introduced or missed)
- Cognitive load (subjective, 1–5 scale with justification)
- Where the agentic approach added value and where it subtracted it

Include a **2 × 4 quantitative table** with columns: Metric · Manual · Agentic · Delta.

| Metric | Manual | Agentic | Delta |
|--------|--------|---------|-------|
| Time to resolution (min) | | | |
| Lines changed | | | |
| Bugs missed post-fix | | | |
| Cognitive load (1–5) | | | |

---

## Final EDD PROPTFOO eval suite

### What PROPTFOO measures

PROPTFOO is a structured rubric for evaluating AI-assisted developer outputs across **eight dimensions**:

| Letter | Dimension | Focus |
|--------|-----------|-------|
| **P** | Prompt quality | How well-crafted were the Copilot prompts? |
| **R** | Reasoning transparency | Was Copilot's reasoning captured and critiqued? |
| **O** | Output correctness | Does the code actually work? |
| **P** | Performance impact | Did refactoring improve or degrade efficiency? |
| **T** | Test coverage | What branch coverage was achieved? |
| **F** | Format and style | Do commits, PRs, and docs meet conventions? |
| **O** | Ownership & hallucination | Were fabricated references caught and logged? |
| **O** | Overall delta | What was the measurable productivity gain? |

---

### Eval scorecard

Run the full eval suite against the completed capstone deliverable and self-score each dimension.

| Dimension | What to assess | Scoring guide (1–5) | Weight |
|-----------|---------------|---------------------|--------|
| **P** Prompt quality | Are prompts specific, context-rich, and iterative? Do they include constraints and examples? | 1 = vague one-liners · 3 = structured with context · 5 = expert few-shot with constraints | 15% |
| **R** Reasoning transparency | Is Copilot's reasoning captured? Are wrong suggestions identified and documented? | 1 = black-box acceptance · 3 = some critique · 5 = full reasoning journal with corrections | 10% |
| **O** Output correctness | Do generated code, tests, and docs actually work? Validated by running the test suite and a human review pass. | 1 = broken · 2 = partial · 3 = works with hacks · 4 = clean · 5 = clean + edge cases handled | 25% |
| **P** Performance impact | Did the refactoring improve or degrade query efficiency? Measured by before/after EXPLAIN output. | 1 = regression · 3 = neutral · 5 = measurable improvement with evidence | 10% |
| **T** Test coverage | Branch coverage % from pytest-cov. Are deduplication and edge cases explicitly tested? | 1 = <50% · 2 = 50–70% · 3 = 70–80% · 4 = 80–90% · 5 = ≥90% with edge cases | 20% |
| **F** Format and style | Do commits follow Conventional Commits? Is the PR description complete? Does the README render cleanly? | 1 = messy · 3 = mostly follows conventions · 5 = all artifacts publication-ready | 10% |
| **O** Ownership & hallucination | Did the developer catch any fabricated API references, wrong library versions, or invented method signatures? | 1 = no review · 3 = some checks · 5 = explicit hallucination log with resolution for each instance | 5% |
| **O** Overall delta | Productivity gain from extension: time saved, defect density reduction, reflection quality. | 1 = no measurable gain · 3 = modest time savings · 5 = significant gain with nuanced reflection | 5% |

---

### Score thresholds

| Score | Outcome |
|-------|---------|
| ≥ 88 | Distinction — requires hallucination log + high-quality reflection |
| 70–87 | Pass |
| < 70 | Does not pass |

> **Gate criterion:** Output correctness (O) must score ≥ 3. A broken service cannot pass the capstone regardless of score in other dimensions.

---

### Scorecard submission format

Submit a **single markdown file** containing:

1. A self-scored table: Dimension · Raw score (1–5) · Weighted score · Evidence snippet or link
2. One paragraph justification per dimension
3. The extension comparison table (if extension was completed)
4. A link to the GitHub repo with all branches and PR history intact

> The facilitator reserves the right to adjust scores based on running the test suite against the submitted repo. Adjusted scores are final.

---

## Customisation notes

| Parameter | Default | Suggested alternatives |
|-----------|---------|----------------------|
| Language / framework | Python / FastAPI | TypeScript / Express · Java / Spring Boot |
| Passing threshold | 70 | 75 for certification context · 65 for introductory workshop |
| Extension | Optional | Make required for advanced cohorts |
| Hallucination log | Required for distinction | Make required for all passing submissions |
