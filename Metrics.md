# Use Case: Measuring GitHub Copilot Productivity Using Engineering Metrics

## Use Case Overview

### Scenario

Contoso Retail Solutions is modernizing its software development practices by adopting **GitHub Copilot Business** across its engineering teams. Management wants to determine whether GitHub Copilot is actually improving developer productivity rather than relying solely on anecdotal feedback.

As an Engineering Productivity Team, your objective is to establish a baseline, collect engineering metrics over multiple sprints, compare results before and after GitHub Copilot adoption, and present findings in a management dashboard.

Rather than measuring AI usage alone, the organization wants to evaluate four key engineering signals:

- Time Saved
- Pull Request Cycle Time
- Bug Reduction
- Review Effort

Your team will use GitHub, Azure DevOps, SonarQube, GitHub Actions, and GitHub Copilot Analytics to measure these indicators.

---

# Business Objectives

By the end of the pilot, management wants answers to the following questions:

- Are developers delivering features faster?
- Are Pull Requests getting merged sooner?
- Has code quality improved?
- Are reviewers spending less time reviewing code?
- Is GitHub Copilot providing measurable ROI?

---

# Learning Objectives

After completing this lab, you will be able to:

- Identify meaningful productivity metrics
- Collect engineering metrics from multiple tools
- Compare pre-Copilot and post-Copilot performance
- Build an engineering productivity dashboard
- Present findings to stakeholders

---

# Lab Prerequisites

## Required Tools

- GitHub Repository
- GitHub Copilot Business or Enterprise
- GitHub Insights
- GitHub Actions
- Azure DevOps Boards or Jira
- SonarQube (or CodeQL)
- Microsoft Excel or Power BI

---

# Case Study Environment

The engineering team consists of:

| Team | Developers |
|-------|------------|
| Backend | 6 |
| Frontend | 4 |
| QA Automation | 2 |
| DevOps | 2 |

Sprint Duration

- 2 Weeks

Pilot Duration

- 3 Sprints

---

# Step 1 – Establish Baseline Metrics

Before enabling GitHub Copilot, collect metrics from the previous three sprints.

Create a spreadsheet similar to the following.

| Metric | Sprint 1 | Sprint 2 | Sprint 3 | Average |
|---------|----------|----------|----------|---------|
| Story Points Completed | | | | |
| PR Merge Time | | | | |
| Review Time | | | | |
| Review Comments | | | | |
| Bugs Found | | | | |
| Failed Builds | | | | |

These values represent your baseline.

---

# Step 2 – Enable GitHub Copilot

Enable GitHub Copilot Business for all developers.

Developers should use Copilot for:

- Code completion
- Unit test generation
- Documentation
- Refactoring
- API generation
- SQL generation
- Code explanation
- Debugging assistance

Continue development for three additional sprints.

---

# Step 3 – Measure Time Saved

## Objective

Estimate how much developer time GitHub Copilot saves.

Since this metric cannot be directly measured automatically, use multiple approaches.

---

## Method 1 – Developer Survey

At the end of every sprint, ask developers:

1. How many hours did Copilot save this sprint?
2. Which tasks benefited the most?
3. Which tasks saw little or no benefit?
4. Did Copilot reduce context switching?

Example Survey

| Developer | Estimated Hours Saved |
|------------|----------------------|
| Dev 1 | 5 |
| Dev 2 | 4 |
| Dev 3 | 6 |
| Dev 4 | 5 |

Average Time Saved

```
(5+4+6+5)/4 = 5 Hours
```

---

## Method 2 – Compare Sprint Velocity

Collect:

- Story Points Completed
- Features Delivered

Example

Before Copilot

| Sprint | Story Points |
|---------|--------------|
| Sprint 1 | 32 |
| Sprint 2 | 30 |
| Sprint 3 | 31 |

Average = 31

After Copilot

| Sprint | Story Points |
|---------|--------------|
| Sprint 4 | 39 |
| Sprint 5 | 41 |
| Sprint 6 | 42 |

Average = 40.6

Improvement

```
((40.6-31)/31)*100
=31% Productivity Improvement
```

---

# Step 4 – Measure Pull Request Cycle Time

## Tool

GitHub Insights

or

Azure DevOps Analytics

Collect

- Average Merge Time
- Time to First Review
- Time to Approval
- Number of Review Iterations

Example

Before Copilot

| PR | Merge Time |
|----|------------|
| PR101 | 2.8 Days |
| PR102 | 3.1 Days |
| PR103 | 2.9 Days |

Average

2.93 Days

After Copilot

| PR | Merge Time |
|----|------------|
| PR201 | 1.7 Days |
| PR202 | 1.8 Days |
| PR203 | 1.6 Days |

Average

1.7 Days

Improvement

```
((2.93-1.7)/2.93)*100

42% Faster
```

---

# Step 5 – Measure Bug Reduction

## Tool Options

- SonarQube
- GitHub CodeQL
- Azure DevOps
- Jira
- GitHub Actions

Collect

- Production Bugs
- Failed Builds
- Security Issues
- Static Analysis Bugs

Example

Before Copilot

| Metric | Count |
|----------|-------|
| Production Bugs | 28 |
| Failed Builds | 16 |
| Sonar Bugs | 142 |

After Copilot

| Metric | Count |
|----------|-------|
| Production Bugs | 15 |
| Failed Builds | 8 |
| Sonar Bugs | 81 |

Bug Reduction

```
((28-15)/28)*100

46%
```

---

# Step 6 – Measure Review Effort

## Tool

GitHub Pull Requests

or

Azure DevOps Repos

Collect

- Review Time
- Review Comments
- Requested Changes
- Number of Review Iterations

Example

Before Copilot

| Metric | Value |
|----------|-------|
| Review Time | 45 Minutes |
| Comments | 21 |
| Change Requests | 8 |

After Copilot

| Metric | Value |
|----------|-------|
| Review Time | 24 Minutes |
| Comments | 10 |
| Change Requests | 3 |

Review Time Improvement

```
((45-24)/45)*100

46%
```

---

# Step 7 – Collect GitHub Copilot Usage Metrics

Open

GitHub Enterprise → Copilot → Metrics Dashboard

Collect:

- Active Users
- Suggestion Acceptance Rate
- Chat Usage
- Completion Usage
- Languages Used

Example

| Metric | Value |
|----------|-------|
| Active Users | 100% |
| Suggestion Acceptance | 37% |
| Chat Sessions | 215 |
| Accepted Suggestions | 18,500 |

> **Note:** These metrics indicate adoption and usage, not productivity outcomes.

---

# Step 8 – Create an Engineering Productivity Dashboard

Prepare a dashboard using Excel or Power BI.

Example

| Metric | Before Copilot | After Copilot | Improvement |
|----------|----------------|---------------|-------------|
| Story Points | 31 | 41 | +32% |
| PR Merge Time | 2.9 Days | 1.7 Days | -42% |
| Review Time | 45 min | 24 min | -46% |
| Review Comments | 21 | 10 | -52% |
| Production Bugs | 28 | 15 | -46% |
| Failed Builds | 16 | 8 | -50% |

---

# Step 9 – Present Findings

Prepare a 10-minute presentation summarizing:

- Baseline metrics
- Copilot adoption metrics
- Engineering productivity improvements
- Code quality improvements
- Areas where Copilot had limited impact
- Recommendations for organization-wide rollout

---

# Deliverables

At the end of this lab, submit:

- Baseline Metrics Spreadsheet
- Post-Copilot Metrics Spreadsheet
- GitHub Copilot Metrics Screenshot
- PR Analytics Report
- SonarQube or CodeQL Report
- Engineering Productivity Dashboard (Excel or Power BI)
- Final Presentation (5–10 slides)

---

# Success Criteria

The lab is considered successful if participants can:

- Establish a productivity baseline before Copilot adoption.
- Measure changes across multiple sprints using engineering metrics.
- Use GitHub Insights, Azure DevOps, SonarQube, and GitHub Copilot Analytics to collect data.
- Quantify improvements in time saved, PR cycle time, bug reduction, and review effort.
- Build a dashboard that communicates the impact of GitHub Copilot using objective data.
- Recommend whether GitHub Copilot should be adopted more broadly based on measurable outcomes.

---

# Key Takeaways

- GitHub Copilot usage metrics alone do not prove productivity gains.
- Engineering metrics such as PR cycle time, review effort, bug reduction, and sprint velocity provide a more reliable measure of impact.
- Time saved is best estimated through developer surveys and delivery metrics, while PR cycle time, review effort, and bug reduction can be measured automatically using development and quality tools.
- Measuring productivity over multiple sprints provides a more accurate assessment of GitHub Copilot's return on investment than short-term observations.
