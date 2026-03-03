---
title: Code Quality Metrics in GitKraken Insights
description: Learn about Code Quality metrics in GitKraken Insights, including Bug Work Percent, Documentation and Test Percent, Code Change Rate, and Code Change by Operation.
taxonomy:
    category: gk-dev
---
<kbd>Last updated: March 2026</kbd>

This section presents metrics designed to assess and improve engineering quality. Together, they offer a balanced view of code health by examining how much work is spent on bugs, tests, and documentation, how frequently older code is modified, and how engineering effort is distributed across different parts of the system.

Use these metrics to monitor technical debt, maintain development quality, and align team investments with maintainability and product stability goals.

---

## Bug Work Percent

**Definition:** _The ratio of development work spent on fixing bugs vs everything else._

This metric reveals the proportion of engineering work consumed by fixing defects versus feature development. It helps leaders assess the level of code quality debt and prioritize efforts toward refactoring and process improvements.

<figure>
  <img src="/wp-content/uploads/bug-work-percent.png" srcset="/wp-content/uploads/bug-work-percent@2x.png" class="help-center-img img-bordered" alt="Chart showing percentage of work on bug fixes over time" />
  <figcaption style="text-align: center; color: #888">See how much development effort is spent resolving bugs compared to building new features.</figcaption>
</figure>

---

## Documentation and Test Percent

**Definition:** _The percent of work related to tests and documentation._

This metric shows the proportion of engineering work dedicated to writing tests and documentation. These activities are strong indicators of long-term maintainability and help improve onboarding efficiency, especially in growing or distributed teams.

<figure>
  <img src="/wp-content/uploads/doc-test-percent.png" srcset="/wp-content/uploads/doc-test-percent@2x.png" class="help-center-img img-bordered" alt="Chart showing percentage of test and documentation work" />
  <figcaption style="text-align: center; color: #888">Track how much work goes into tests and documentation over time.</figcaption>
</figure>

---

## Code Change Rate

**Definition:** _How old the code is that is being changed._

This metric tracks the age of code being modified. Frequent changes to older code may reveal technical debt hotspots, signaling the need for deeper refactoring or even system replacement. Teams can use this data to prioritize stability improvements and architectural upgrades.

<figure>
  <img src="/wp-content/uploads/code-change-rate.png" srcset="/wp-content/uploads/code-change-rate@2x.png" class="help-center-img img-bordered" alt="Chart showing age of code being modified" />
  <figcaption style="text-align: center; color: #888">See how much work targets older code, highlighting potential legacy or debt-heavy areas.</figcaption>
</figure>

---

## Code Change by Operation

**Definition:** _The measure of code changes organized by the type of change. (e.g., "test," "documentation," "front-end," "back-end")_

This metric breaks down engineering work by category, such as testing, documentation, front-end, and back-end development. It helps teams visualize where their effort is being spent and supports more strategic allocation of resources across system layers and quality activities.

<figure>
  <img src="/wp-content/uploads/code-change-by-operation.png" srcset="/wp-content/uploads/code-change-by-operation@2x.png" class="help-center-img img-bordered" alt="Chart showing breakdown of code changes by category" />
  <figcaption style="text-align: center; color: #888">Understand the distribution of code changes across different areas of the codebase.</figcaption>
</figure>
