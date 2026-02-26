---
title: Pull Request Metrics in GitKraken Insights
description: Learn about Pull Request metrics in GitKraken Insights, including cycle time, lead time, review activity, and code review hours.
taxonomy:
    category: gk-dev
---
<kbd>Last updated: February 2026</kbd>

Pull Request metrics help teams understand how quickly and smoothly code changes move through review and deployment.

PR intelligence turns these insights into clear actions by highlighting slowdowns, spotting patterns in fast or delayed reviews, and uncovering blockers that may affect delivery.

---

## First Response Time ("Pickup Time")

**Definition:** _The time measured from when a PR is opened to when the 1st review or comment is left on a PR._

This metric shows how long each pull request within a selected timeframe took to have a first response (comment or review). Values are expressed in **hours** and averaged over a **7-day period**. Shorter pickup times indicate faster reviewer engagement and healthier collaboration.

<figure>
  <img src="/wp-content/uploads/first-response-time.png" srcset="/wp-content/uploads/first-response-time@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Average time it took for PR to receive comment or review.</figcaption>
</figure>

---

## Cycle Time ("first commit" to "merge")

**Definition:** _The time measured between the 1st commit of a PR to when the PR is merged._

This metric shows how long each pull request within a selected timeframe took to merge from the time the first commit was made. Values are expressed in **days** and averaged over a **7-day period**. Cycle time provides insight into overall delivery speed, highlighting how quickly work moves from coding to production.

<figure>
  <img src="/wp-content/uploads/cycle-time-line.png" srcset="/wp-content/uploads/cycle-time-line@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Average time it took for PR to receive comment or review.</figcaption>
</figure>

The **Details** view offers deeper analysis.

<figure>
  <img src="/wp-content/uploads/pr-cycle-time-details.png" srcset="/wp-content/uploads/pr-cycle-time-details@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Get a detailed breakdown of PR cycle time.</figcaption>
</figure>

- Pull requests are grouped into four categories by duration:
  - **Elite:** Less than 1 day
  - **Fast:** 1–7 days
  - **Average:** 7–29 days
  - **Slower:** Over 30 days
- Each node in the scatter plot is interactive, showing PR details such as time since merge, PR name, author, and a link to open directly in GitHub.
- A sortable table lists all PRs below the chart. You can sort by **Days**, **Pull Request name**, **Author**, **Date Opened**, or **Date Merged**.

---

## Lead Time

**Definition:** _The time from the first commit in a pull request to when that code is deployed to production. This bridges development and deployment activities._

This metric shows how long each pull request within a selected timeframe remained open, measured from when the PR was created until it was merged. Values are expressed in **days** and averaged over a **7-day period**.

<figure>
  <img src="/wp-content/uploads/lead-time.png" srcset="/wp-content/uploads/lead-time@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">See how long PRs remained open until it was merged.</figcaption>
</figure>

---

## Number of Reviews per Day/Week/Month

**Definition:** _The volume of code reviews being conducted, indicating team review capacity and activity._

This metric shows the total number of reviews (all types) completed over a given period of time. Values are expressed in **reviews** and averaged over a **7-day window**. Tracking review activity helps teams understand collaboration patterns and reviewer workload across different timeframes (daily, weekly, or monthly).

<figure>
  <img src="/wp-content/uploads/number-of-reviews.png" srcset="/wp-content/uploads/number-of-reviews@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">See how many reviews have been given over a time period.</figcaption>
</figure>

---

## Open Time ("opened" to "merged")

**Definition:** _The time between when a pull request is opened and when it is merged._

This metric captures the duration from pull request creation to merge. It differs from PR Cycle Time, which starts from the first commit. Open Time isolates the review and approval phase, helping teams identify delays specifically related to code review and collaboration workflows.

<figure>
  <img src="/wp-content/uploads/open-time.png" srcset="/wp-content/uploads/open-time@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Shows the time each pull request remained open before being merged.</figcaption>
</figure>

The **Open Time details view** provides a stacked bar chart that visualizes average PR open durations per repository across time intervals. Each bar segment represents a specific repository, allowing teams to compare performance across services.

<figure>
  <img src="/wp-content/uploads/open-time-details.png" srcset="/wp-content/uploads/open-time-details@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Detailed breakdown of PR open durations across repositories and time intervals.</figcaption>
</figure>

Key highlights include:

- **Hover insights**: Hovering over bars shows per-repository open time for the selected week.
- **Repository comparison**: See how review duration varies across services.
- **Summary metrics**:
  - Pull requests merged
  - Pull request cycle time
  - Pull request average diff delta
  - Pull requests opened

These metrics help teams identify trends, uncover review bottlenecks, and monitor efficiency over time.

---

## Number of PRs Abandoned

**Definition:** _Number of pull requests closed without being merged._

This metric can reveal wasted engineering effort, scope management issues, or breakdowns in work planning and prioritization. A high abandonment rate may indicate unclear requirements, excessive rework, or bottlenecks earlier in the development process.

<figure>
  <img src="/wp-content/uploads/prs-abandoned.png" srcset="/wp-content/uploads/prs-abandoned@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Visualizes how many PRs were closed without merging, segmented by repository and time.</figcaption>
</figure>

---

## Number of PRs Merged Without Review

**Definition:** _The number of pull requests that have been merged without any (bot or human) review._

This metric can indicate potential process gaps in peer review enforcement. It identifies PRs integrated without peer review, exposing quality risks and gaps in your code review governance that could lead to production defects.

<figure>
  <img src="/wp-content/uploads/prs-merged-without-review.png" srcset="/wp-content/uploads/prs-merged-without-review@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Tracks PRs merged without review, highlighting enforcement issues in your review process.</figcaption>
</figure>

---

## Number of PR Comments

**Definition:** _The total number of comments left on your pull requests._

This metric measures the level of engagement during code reviews, revealing how thoroughly code is being evaluated. A high number of comments can indicate active feedback, knowledge sharing, and mentorship opportunities across the team.

<figure>
  <img src="/wp-content/uploads/pr-comments.png" srcset="/wp-content/uploads/pr-comments@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Shows total PR comments, which can reflect review depth and collaboration intensity.</figcaption>
</figure>

---

## PR Size / Effort

**Definition:** The aggregate amount of change (diff delta) across all pull requests that were merged during a given time period.

This metric reflects the total effort involved in the review process. It is calculated by summing the "Before PR submitted" and "While under review" diff delta values, representing the total size of the pull request and the energy required for its review.

<figure>
  <img src="/wp-content/uploads/pr-size.png" srcset="/wp-content/uploads/pr-size@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Displays total PR size (diff delta), helping evaluate review load and PR size trends.</figcaption>
</figure>

By aggregatating the total change volume across merged PRs, this helps teams balance workload distribution and recognize when PRs may be too large for effective review.

---

## Code Review Hours

**Definition:** Average time spent in hours during the "review period" of your team's pull requests.

**How it's calculated:** Total review hours / number of committers.

This metric quantifies the average time investment in reviewing code. It helps leaders evaluate whether code review capacity aligns with delivery goals and whether review processes need optimization to support team velocity and quality.

<figure>
  <img src="/wp-content/uploads/code-review-hours.png" srcset="/wp-content/uploads/code-review-hours@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Average code review time per developer, highlighting team review investment trends.</figcaption>
</figure>
