# Module 07 – Lab 02
# Evaluating a RAG System with RAGAS (Module 8 Preview)

> **Module:** M7 – Evaluation-Driven Development (EDD)  
> **Duration:** 60–75 Minutes  
> **Difficulty:** Intermediate

---

# Introduction

Retrieval-Augmented Generation (RAG) improves Large Language Model (LLM) responses by retrieving relevant information from external knowledge sources before generating an answer. However, a RAG system can still produce incorrect or hallucinated responses if retrieval quality is poor or the model ignores the retrieved context.

**RAGAS (RAG Assessment)** provides an evaluation framework that measures the quality of a RAG pipeline using objective metrics such as **Faithfulness**, **Answer Relevancy**, **Context Precision**, and **Context Recall**.

In this lab, you will build a basic RAGAS evaluation harness and measure the **Faithfulness** of a sample RAG system. This serves as a preview for the RAG implementation that will be developed in **Module 8**.

---

# Learning Objectives

After completing this lab, you will be able to:

- Explain why RAG systems require evaluation.
- Understand the purpose of RAGAS.
- Build a simple RAG evaluation harness.
- Measure Faithfulness for generated responses.
- Interpret evaluation results and identify opportunities for improvement.

---

# Background Concepts

## Why Evaluate RAG?

A RAG pipeline has two major components:

1. **Retriever** – Finds relevant documents.
2. **Generator** – Produces an answer using the retrieved context.

Failures may occur because:

- Irrelevant documents are retrieved.
- Relevant documents are ignored.
- The LLM hallucinates.
- Retrieved context is incomplete.

---

## Common RAG Evaluation Metrics

| Metric | Description |
|---------|-------------|
| Faithfulness | Is the answer supported by the retrieved context? |
| Answer Relevancy | Does the answer address the user's question? |
| Context Precision | Were the retrieved documents relevant? |
| Context Recall | Were all important documents retrieved? |

---

# Enterprise Scenario

Contoso Retail is developing an internal AI assistant that answers employee questions using HR policies, product documentation, and operational manuals.

Before releasing the assistant, the AI Engineering team wants to measure whether responses are grounded in the retrieved documentation.

---

# RAG Evaluation Workflow

```text
User Question
      │
      ▼
Retriever
      │
      ▼
Retrieved Context
      │
      ▼
LLM Response
      │
      ▼
RAGAS Evaluation
      │
      ▼
Faithfulness Report
```

---

# Prerequisites

- Python 3.10 or later
- Visual Studio Code
- Git
- Virtual environment
- Basic understanding of RAG

---

# Exercise 1 – Install RAGAS

```bash
pip install ragas
pip install datasets
pip install pandas
```

Verify the installation:

```bash
python -c "import ragas; print(ragas.__version__)"
```

> 📷 **Screenshot:** Successful RAGAS installation.

---

# Exercise 2 – Create an Evaluation Dataset

Create a file named `rag_eval_dataset.json`.

Example record:

```json
{
  "question": "What is the company's annual leave policy?",
  "contexts": [
    "Employees are entitled to 20 days of annual leave each calendar year."
  ],
  "answer": "Employees receive 20 days of annual leave each year.",
  "ground_truth": "Employees are entitled to 20 days of annual leave each calendar year."
}
```

Create at least **5 evaluation records**.

---

# Exercise 3 – Build the Evaluation Harness

Create a Python file named:

```text
evaluate_rag.py
```

Use GitHub Copilot to generate the evaluation harness.

Suggested prompt:

```text
Generate a Python script using RAGAS to evaluate the Faithfulness metric for a RAG dataset loaded from JSON.
```

The script should:

- Load the dataset
- Execute the Faithfulness evaluation
- Print the evaluation score
- Save the report

> 📷 **Screenshot:** Generated evaluation harness.

---

# Exercise 4 – Execute the Evaluation

Run:

```bash
python evaluate_rag.py
```

Sample output:

```text
Faithfulness : 0.92
```

Interpretation:

- 0.90–1.00 → Excellent
- 0.75–0.89 → Acceptable
- Below 0.75 → Requires improvement

---

# Exercise 5 – Analyze the Results

Identify:

- Which questions scored poorly?
- Was the issue caused by retrieval or generation?
- Were the retrieved documents relevant?
- How could the prompt or retriever be improved?

Modify one dataset entry and rerun the evaluation to observe changes.

---

# Validation Checklist

- [ ] RAGAS installed.
- [ ] Evaluation dataset created.
- [ ] Evaluation harness generated.
- [ ] Faithfulness measured.
- [ ] Results interpreted.

---

# Challenge Exercise

Extend the evaluation to measure:

- Answer Relevancy
- Context Precision
- Context Recall

Compare all metrics and identify which aspect of the RAG system requires the most improvement.

---

# Best Practices

- Build representative evaluation datasets.
- Include positive and negative examples.
- Measure multiple metrics, not just Faithfulness.
- Version-control evaluation datasets.
- Re-run evaluations whenever prompts or retrieval logic change.

---

# Knowledge Check

1. Why is Faithfulness important for RAG systems?
2. What problem does RAGAS solve?
3. Why should evaluation datasets include ground truth?
4. How can evaluation results guide prompt or retrieval improvements?

---

# Summary

| Concept | Outcome |
|---------|---------|
| RAGAS | Framework for evaluating RAG applications |
| Faithfulness | Measures grounding in retrieved context |
| Evaluation Harness | Automates RAG quality assessment |
| EDD | Evaluate before deploying AI features |

---

# Looking Ahead

In **Module 8**, you will build a complete RAG application. The evaluation harness created in this lab can be reused to validate future changes and detect regressions as the system evolves.
