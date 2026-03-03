---
title: GitKraken Insights FAQ
description: Answers to common questions about GitKraken Insights for developer leaders, including access, integrations, available metrics, and customization.
taxonomy:
    category: gk-dev
---
<kbd>Last updated: March 2026</kbd>

---

### What is GitKraken Insights?

GitKraken Insights turns raw Git data into clear, actionable engineering metrics. It pulls code activity, pull requests, issues, and CI/CD results into a single dashboard, giving both developers and leaders a shared view of how work is progressing — without extra reporting overhead.

---

### How do I get access?

GitKraken Insights is available by request only. To get started, [request a guided tour](https://www.gitkraken.com/insights#form) and a member of the GitKraken team will walk you through Insights and explain how to enable access for your organization.

Insights is available as an add-on to seats in your existing GitKraken subscription, or as a discounted standalone solution for developers on your team who don't use GitKraken.

---

### What tools does GitKraken Insights connect to?

GitKraken Insights currently supports connections with **GitHub**, **GitLab**, **Bitbucket**, and **Jira Cloud**. Support for Azure DevOps is coming soon.

To enable AI Impact metrics, you can also connect **Cursor** or **GitHub Copilot** as an AI provider.

---

### What metrics does GitKraken Insights track?

GitKraken Insights covers five metric categories:

- **DORA Metrics** — Deploy Frequency, Change Lead Time, Mean Time to Repair/Recover, and Defect Rate
- **Pull Request Metrics** — Cycle Time, Lead Time, First Response Time, Open Time, Number of Reviews, PR Size, Code Review Hours, and more
- **AI Impact Metrics** — Prompt Acceptance Rate, Tab Acceptance Rate, Duplicated Code, Code Rework, and Active AI Users
- **Code Quality Metrics** — Bug Work Percent, Documentation and Test Percent, Code Change Rate, and Code Change by Operation
- **Velocity and Delivery Consistency Metrics** — Commit Count and Estimated Coding Hours

---

### Does GitKraken Insights work with AI coding tools?

Yes. GitKraken Insights connects to Cursor and GitHub Copilot to surface AI Impact metrics. These metrics help teams measure how AI tools affect code quality and developer efficiency — including how often suggestions are accepted, how much code is duplicated or reworked, and how many developers are actively using AI tools.

---

### How long does it take to see data after connecting?

After setup is complete, GitKraken Insights begins importing your repository data automatically:

- **Past month's activity** is typically available within a few hours.
- **Full year's activity** is usually ready within one to two days.

You can track import progress at any time from the **Dashboard** tab.

---

### Do developers need to change their workflow?

No. GitKraken Insights reads from existing Git activity, pull requests, issues, and CI/CD data. Developers continue working in their normal tools — GitKraken Insights observes and measures without requiring any changes to how work gets done.

---

### Can I customize dashboards and the metrics they display?

Yes. You can create dashboards, add specific metrics as widgets, arrange the widget layout, and apply filters by Workspace, Repository, Timeframe, and Team. You can also add trendlines to individual metrics to visualize direction over time.

Note: each user can currently create one dashboard per organization. Support for multiple dashboards per user is planned for a future release.

---

### How does GitKraken Insights identify releases for DORA metrics?

You configure release detection rules in **Metric Settings > Release Tracking**. Rules can match on branch prefix, merged pull request target, git tags, commit messages, or API calls. GitKraken Insights attempts to apply each rule to all connected repositories automatically.

---

### How does GitKraken Insights identify critical defects?

Critical defects are identified two ways. In **Metric Settings > Critical Defect Terms**, you define strings that GitKraken Insights matches case-insensitively against branch names, linked issue titles, and pull request titles. In **Metric Settings > Define Issue Tracker Projects**, you configure the specific issue field values that mark a defect as critical within your issue tracker.
