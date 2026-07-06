# Capstone Project: AI-Powered Testing with GitHub Copilot
## End-to-End QA Project for Manual Testers & Automation Test Engineers

**Course:** GitHub Copilot for Software Testing

**Capstone:** CP-01

**Difficulty:** Advanced

**Target Audience**

- Manual Test Engineers
- Automation Test Engineers
- QA Engineers
- SDETs
- QA Leads
- Test Architects

---

# Capstone Overview

This capstone project brings together everything learned throughout the GitHub Copilot for Testers course.

Rather than using a predefined application, **participants should use an application they currently work on (or a sample application provided by the instructor).** This makes the exercises directly applicable to real-world projects while allowing each participant to tailor the outputs to their own business domain.

Throughout the project, participants will use GitHub Copilot as an AI-powered testing assistant to perform requirement analysis, planning, manual testing, automation testing, API testing, code review, and project management activities.

The capstone follows the complete Software Testing Life Cycle (STLC) and demonstrates how GitHub Copilot can accelerate testing activities from requirement analysis through release readiness.

---

# Learning Objectives

After completing this capstone, participants will be able to:

- Analyze business requirements using GitHub Copilot
- Use Ask Mode effectively
- Use Plan Mode effectively
- Use Agent Mode effectively
- Create Use Case Diagrams
- Create Sequence Diagrams
- Design comprehensive test strategies
- Generate manual test cases
- Create exploratory testing checklists
- Design automation strategies
- Generate automation frameworks
- Generate API test scenarios
- Perform AI-assisted code reviews
- Create GitHub Copilot Custom Agents
- Integrate GitHub Copilot with GitHub using MCP
- Integrate GitHub Copilot with Jira using MCP
- Produce release readiness documentation

---

# Prerequisites

Participants should have access to:

- Visual Studio Code
- GitHub Copilot Enterprise or GitHub Copilot Pro+
- GitHub Repository
- GitHub MCP Server (configured)
- Jira MCP Server (configured)
- Git
- An existing application (preferred) or an instructor-provided sample application
- Basic knowledge of Manual Testing and Automation Testing

---

# Selecting Your Application

Each participant should choose **one application** to use throughout the capstone.

Recommended options include:

- Your organization's existing application (preferred)
- A training project provided by the instructor
- An open-source application
- A demo e-commerce, banking, healthcare, insurance, HR, travel, or retail application

Choose an application that contains multiple business features such as:

- User Authentication
- Search
- CRUD Operations
- Business Workflows
- APIs
- Database interactions
- Reports
- Notifications
- External integrations

**Important:** Use the **same application** throughout every phase of this capstone.

---

# Sample Business Features

Your application should ideally contain several functional modules. Examples include:

- User Registration
- Login
- Forgot Password
- Search
- Dashboard
- Product/Service Management
- Shopping Cart
- Checkout
- Payment
- Order Management
- User Profile
- Reports
- Notifications
- Administration

If your application contains different modules, substitute them throughout the exercises.

---

# Capstone Phases

---

# Phase 1 – Requirement Analysis

## Objective

Understand the application before writing test cases.

---

## Activities

Using **GitHub Copilot Ask Mode**:

- Analyze business requirements.
- Identify functional modules.
- Identify business rules.
- Identify assumptions.
- Identify missing requirements.
- Identify dependencies.
- Identify risks.
- Generate clarification questions.

---

## Deliverables

- Requirement Analysis Document
- Functional Module Summary
- Business Rules
- Risk List
- Assumptions
- Clarification Questions

---
# Phase 2 – Configure GitHub Copilot Instructions

## Objective

Create a project-wide `copilot-instructions.md` file that defines testing standards, coding conventions, documentation requirements, and quality expectations for GitHub Copilot.

The goal is to ensure that every AI-generated response follows the same organizational standards throughout the project.

---

## Activities

Create the following file:

```text
.github/copilot-instructions.md
```

Configure GitHub Copilot with instructions specific to your project.

The instructions should include:

### Project Context

- Describe the application.
- Describe the business domain.
- Identify the primary users.
- Describe the overall system architecture.

---

### Manual Testing Standards

Instruct Copilot to:

- Generate ISTQB-aligned test cases.
- Include positive, negative, and boundary scenarios.
- Use clear preconditions.
- Generate structured test steps.
- Include expected results.
- Assign priorities.
- Suggest test data.
- Recommend exploratory testing ideas.

---

### Automation Standards

Configure Copilot to follow your organization's framework.

Examples:

- Selenium + Java + TestNG
- Playwright + TypeScript
- Cypress
- Robot Framework

Specify standards such as:

- Page Object Model
- Explicit waits only
- Reusable utilities
- Meaningful assertions
- Logging
- Avoid duplicate code
- Follow project naming conventions

---

### API Testing Standards

Configure Copilot to:

- Generate positive and negative API tests.
- Validate response schema.
- Validate HTTP status codes.
- Validate response time.
- Verify authentication and authorization.
- Recommend contract testing.

---

### Coding Standards

Examples:

- Follow SOLID principles.
- Keep methods small and reusable.
- Add meaningful comments where required.
- Avoid hard-coded values.
- Use configuration files.
- Prefer reusable utilities.
- Follow project naming conventions.

---

### Documentation Standards

Ask Copilot to:

- Explain assumptions.
- Document generated code.
- Produce Markdown documentation.
- Generate Mermaid diagrams where applicable.

---

### Security Guidelines

Instruct Copilot to:

- Never expose secrets.
- Never generate hard-coded passwords.
- Avoid insecure coding patterns.
- Recommend secure authentication practices.

---

### Testing Best Practices

Ask Copilot to:

- Recommend edge cases.
- Identify missing validations.
- Suggest regression candidates.
- Highlight potential risks.
- Recommend automation opportunities.

---

## Example Copilot Instructions

```markdown
# Project Overview

This repository contains the QA assets for our enterprise application.

Always generate production-quality outputs.

---

# Manual Testing

Generate ISTQB-compliant test cases.

Always include:

- Positive scenarios
- Negative scenarios
- Boundary Value Analysis
- Equivalence Partitioning
- Decision Table scenarios
- Exploratory testing ideas

---

# Automation

Use Playwright with TypeScript.

Follow:

- Page Object Model
- Fixtures
- Explicit waits
- Reusable methods
- Meaningful assertions

Avoid duplicated code.

---

# API Testing

Generate REST API tests with:

- Positive tests
- Negative tests
- Authentication
- Authorization
- Response validation

---

# Documentation

Generate Markdown documentation.

Use Mermaid diagrams whenever appropriate.

---

# Code Review

Always identify:

- Duplicate code
- Maintainability issues
- Missing assertions
- Performance improvements

Suggest refactoring where appropriate.
```

---

## Deliverables

Participants should submit:

- `.github/copilot-instructions.md`
- Summary of the standards defined
- Explanation of how the instructions improved GitHub Copilot responses

---

# Phase 2.1 – Test Planning

## Objective

Create a comprehensive testing strategy before implementation.

---

Using **GitHub Copilot Plan Mode**, create:

- Test Strategy
- Test Scope
- Test Objectives
- Entry Criteria
- Exit Criteria
- Smoke Testing Strategy
- Regression Strategy
- Automation Strategy
- API Testing Strategy
- Test Data Strategy
- Test Environment Strategy
- Risk Matrix
- Resource Plan
- Test Schedule

---

## Deliverables

- Master Test Plan

---

# Phase 3 – Use Case Diagram

## Objective

Understand system functionality from the user's perspective.

---

Create a Use Case Diagram that includes:

- Actors
- Business Functions
- External Systems
- Relationships
- Include/Extend relationships where applicable

Examples of use cases include:

- Login
- Search
- Create Record
- Update Record
- Delete Record
- Approve Request
- Submit Order
- Generate Report

Use the use cases relevant to your own application.

---

## Activities

Using GitHub Copilot:

- Validate the diagram.
- Identify missing actors.
- Identify missing use cases.
- Suggest improvements.
- Identify testing opportunities.

---

## Deliverables

- Use Case Diagram
- Use Case Analysis

---

# Phase 4 – Sequence Diagrams

## Objective

Understand system interactions.

---

Create Sequence Diagrams for **three to five important business workflows**.

Examples:

- User Login
- Search
- Create Transaction
- Checkout
- Payment
- Approval Process
- Report Generation

For each sequence diagram:

- Identify actors.
- Identify services.
- Identify alternate flows.
- Identify exception flows.
- Identify integration points.

---

## Activities

Using GitHub Copilot:

Generate:

- Functional scenarios
- Negative scenarios
- Integration scenarios
- Failure scenarios
- API scenarios
- Risk areas

---

## Deliverables

- Sequence Diagrams
- Workflow Analysis

---

# Phase 5 – Manual Testing

## Objective

Generate comprehensive manual testing artifacts.

---

Generate:

- Functional Test Cases
- Negative Test Cases
- Boundary Value Tests
- Equivalence Partition Tests
- Decision Table Tests
- State Transition Tests (if applicable)
- Exploratory Testing Charter
- Accessibility Test Scenarios
- Localization Test Scenarios
- Security Test Ideas

---

## Deliverables

Minimum:

- 75 Manual Test Cases
- Exploratory Testing Checklist
- Decision Tables
- Test Data Matrix
- Requirement Traceability Matrix (RTM)

---

# Phase 6 – GitHub Copilot Custom Agents

Create three Custom Agents.

---

## Agent 1 – Manual Testing Expert

Capabilities

- Requirement Analysis
- Test Case Generation
- Exploratory Testing
- Boundary Value Analysis
- Equivalence Partitioning
- Decision Table Testing
- State Transition Testing
- Bug Report Generation
- Risk Analysis

---

## Agent 2 – Automation Testing Expert

Capabilities

- Selenium
- Playwright
- Cypress
- Robot Framework
- Page Object Model
- TestNG
- JUnit
- NUnit
- Fixtures
- Assertions
- CI/CD
- Automation Framework Design

---

## Agent 3 – API Testing Expert

Capabilities

- REST Assured
- Postman
- Playwright API
- Contract Testing
- Authentication
- OAuth
- JWT
- Performance Test Planning
- Security Validation

---

## Deliverables

- Manual Testing Agent
- Automation Testing Agent
- API Testing Agent

---

# Phase 7 – Automation Testing

Choose the automation technology used by your organization.

Examples:

- Selenium
- Playwright
- Cypress
- Robot Framework

Generate:

- Automation Framework
- Folder Structure
- Page Objects
- Test Classes
- Utility Classes
- Configuration
- Reporting

Automate **at least three end-to-end business workflows**.

---

## Deliverables

- Automation Framework
- Automated Test Scripts
- Execution Reports

---

# Phase 8 – API Testing

Identify the APIs used by your application.

Generate:

- Functional API Tests
- Negative API Tests
- Boundary Tests
- Authentication Tests
- Authorization Tests
- Error Handling Tests
- Contract Validation
- Response Assertions

---

## Deliverables

- API Test Suite
- API Test Strategy

---

# Phase 9 – AI-Assisted Code Review

Use GitHub Copilot to review:

- Automation Framework
- Test Scripts
- API Tests

Review for:

- Code duplication
- Maintainability
- Readability
- Assertions
- Synchronization
- Naming standards
- Error handling
- Best practices

Refactor where necessary.

---

## Deliverables

- Code Review Report
- Refactored Code Summary

---

# Phase 10 – GitHub MCP Integration

Use the GitHub MCP Server to interact with your repository using natural language.

Activities:

- Create GitHub Issues.
- Search existing Issues.
- Create Feature Branches.
- Create Pull Requests.
- Review Pull Requests.
- Summarize commits.
- Generate Release Notes.
- Link Pull Requests to Issues.
- Generate repository summaries.

---

## Deliverables

- GitHub Issues
- Pull Requests
- Release Notes
- Repository Activity Summary

---

# Phase 11 – Jira MCP Integration

Use the Jira MCP Server.

Activities:

- Create Epics.
- Create User Stories.
- Create Tasks.
- Create Test Tasks.
- Create Bugs.
- Link Bugs to Stories.
- Update Issue Status.
- Retrieve Sprint Backlog.
- Generate Sprint Summary.
- Generate QA Status Report.
- Create Release Readiness Report.

---

## Deliverables

- Jira Epic
- Jira Stories
- Jira Tasks
- Jira Bugs
- Sprint Summary
- QA Status Report

---

# Phase 12 – Release Readiness

Using GitHub Copilot Plan Mode, prepare:

- Regression Summary
- Automation Coverage
- Open Risks
- Known Issues
- Test Metrics
- Release Checklist
- Go / No-Go Recommendation

---

## Deliverables

- Release Readiness Report

---

# Final Deliverables

## Documentation

- Requirement Analysis
- Test Strategy
- Risk Matrix
- Use Case Diagram
- Sequence Diagrams
- Manual Test Cases
- Exploratory Testing Checklist
- Decision Tables
- Test Data Matrix
- Requirement Traceability Matrix
- Automation Strategy
- API Testing Strategy
- Code Review Report
- Release Readiness Report

---

## Automation

- Automation Framework
- Automated Test Scripts
- API Test Suite
- Execution Reports

---

## GitHub Copilot Artifacts

- Manual Testing Custom Agent
- Automation Testing Custom Agent
- API Testing Custom Agent

---

## GitHub MCP Deliverables

- Issues
- Pull Requests
- Release Notes
- Repository Summary

---

## Jira MCP Deliverables

- Epic
- User Stories
- Tasks
- Bugs
- Sprint Summary
- QA Status Report

---

# Assessment Rubric

| Area | Weight |
|-------|--------|
| Requirement Analysis | 10% |
| Test Planning | 10% |
| UML Diagrams | 10% |
| Manual Testing | 15% |
| Automation Testing | 15% |
| API Testing | 10% |
| Custom Agents | 10% |
| GitHub MCP Integration | 10% |
| Jira MCP Integration | 5% |
| Release Readiness | 5% |

---

# Success Criteria

Participants successfully complete the capstone if they can:

- Analyze an existing application using GitHub Copilot.
- Create a complete testing strategy.
- Model the application using Use Case and Sequence Diagrams.
- Produce comprehensive manual testing artifacts.
- Build and execute an automation framework.
- Generate API testing assets.
- Perform AI-assisted code reviews.
- Create specialized GitHub Copilot Custom Agents.
- Use GitHub MCP to manage repository activities.
- Use Jira MCP to manage Agile work items.
- Produce release-ready QA documentation.

---

# Capstone Summary

This capstone reflects a real enterprise QA engagement. Rather than learning GitHub Copilot features in isolation, participants apply them to an application they already know, making the exercises immediately relevant to their daily work. By progressing through requirement analysis, planning, UML modeling, manual testing, automation, API validation, AI-assisted code reviews, and GitHub/Jira MCP integration, participants experience an end-to-end AI-assisted testing workflow that mirrors modern Agile and DevOps practices.
