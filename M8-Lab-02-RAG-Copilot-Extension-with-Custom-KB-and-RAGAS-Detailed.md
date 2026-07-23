# Module 08 – Lab 02
# Build a GitHub Copilot Extension with a Custom Knowledge Base and Evaluate with RAGAS

> **Module:** M8 – RAG · Text2SQL · CI/CD Integration
> **Duration:** 90–120 Minutes
> **Difficulty:** Advanced

## Introduction

In this lab, you will build a Retrieval-Augmented Generation (RAG) solution by connecting a GitHub Copilot Extension to a custom Knowledge Base (KB). You will then reuse the RAGAS evaluation harness from Module 7 to measure **Faithfulness** before and after improving the KB.

> **Note:** GitHub Copilot Extensions evolve over time. Focus on the workflow rather than exact UI screens.

## Learning Objectives

- Build or configure a GitHub Copilot Extension.
- Create a custom Knowledge Base.
- Connect the extension to the KB.
- Test enterprise questions.
- Run RAGAS evaluation.
- Improve the KB and compare metrics.

## Enterprise Scenario

Contoso Retail wants an internal AI assistant that answers questions from approved HR, IT, Travel, and Security documents.

## End-to-End Workflow

```text
Enterprise Documents
        │
        ▼
Knowledge Base
        │
        ▼
Index / Embeddings
        │
        ▼
GitHub Copilot Extension
        │
        ▼
GitHub Copilot Chat
        │
        ▼
Enterprise Questions
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
Improve Knowledge Base
```

## Suggested Repository Structure

```text
copilot-rag-demo/
├── docs/
├── extension/
├── evaluations/
├── scripts/
└── README.md
```

## Exercise 1 – Prepare the Knowledge Base

1. Create a **docs/** folder.
2. Add documents such as:
   - Employee Handbook
   - Leave Policy
   - Travel Policy
   - Expense Policy
   - Security Guidelines
3. Review the documents for completeness and freshness.

**Hint:** Better documents generally produce better retrieval quality.

## Exercise 2 – Build the Copilot Extension

Suggested workflow:

1. Create or clone a GitHub Copilot Extension sample.
2. Configure the extension.
3. Connect it to your Knowledge Base or retrieval service.
4. Run the extension locally.
5. Verify it is accessible from GitHub Copilot.

**Deliverable:** A working Copilot Extension connected to enterprise content.

## Exercise 3 – Test the RAG Solution

Ask questions such as:

- What is our annual leave policy?
- How do employees submit travel expenses?
- What is the VPN password reset process?

Observe:

- Was relevant context retrieved?
- Were the answers grounded?
- Were the correct documents referenced?
- Were there hallucinations?

## Exercise 4 – Run the RAGAS Evaluation

Reuse the evaluation harness from Module 7.

Example:

```bash
python evaluate_rag.py
```

Record:

| Metric | Baseline |
|---------|----------|
| Faithfulness | |
| Answer Relevancy | |
| Context Precision | |
| Context Recall | |

## Exercise 5 – Improve the Knowledge Base

Improve one or more of the following:

- Add missing documents
- Improve chunking
- Improve metadata
- Remove outdated content
- Expand topic coverage

Run the evaluation again.

| Metric | Before | After |
|---------|--------|-------|
| Faithfulness | | |
| Answer Relevancy | | |
| Context Precision | | |
| Context Recall | | |

Discuss:

- Which improvement helped the most?
- Which questions still need improvement?

## Validation Checklist

- [ ] Knowledge Base created
- [ ] Copilot Extension configured
- [ ] Enterprise questions answered
- [ ] Baseline RAGAS evaluation completed
- [ ] KB improved
- [ ] Second evaluation completed
- [ ] Faithfulness improved

## Troubleshooting

| Problem | Suggested Action |
|----------|------------------|
| No retrieval | Verify indexing |
| Hallucinations | Improve source documents |
| Low Faithfulness | Improve chunking and metadata |
| Irrelevant answers | Expand KB coverage |

## Best Practices

- Keep the KB current.
- Version-control documents.
- Evaluate after every KB update.
- Track RAGAS metrics over time.

## Summary

This lab demonstrated an enterprise RAG workflow:

1. Build a Knowledge Base.
2. Connect it to a GitHub Copilot Extension.
3. Test enterprise questions.
4. Measure RAG quality with RAGAS.
5. Improve the Knowledge Base.
6. Compare Faithfulness before and after tuning.

## Looking Ahead

The next lab introduces Text2SQL using GitHub Copilot and PostgreSQL.
