---
title: Dashboard Configuration in GitKraken Insights
description: Learn how to create dashboards, add metrics, arrange widget layouts, apply trendlines, and filter data in GitKraken Insights.
taxonomy:
    category: gk-dev
---
<kbd>Last updated: March 2026</kbd>


## Overview

GitKraken Insights brings your Git data, pull requests, issues, and CI/CD results into one place. Instead of juggling tools or exporting spreadsheets, you get dashboards that show how work is really moving across code, reviews, and releases. The goal is to give both devs and leads a clear view of progress and bottlenecks without extra reporting overhead.

### Key benefits

- **In your workflow:** Metrics come straight from the tools you already use: Git, PRs, CI/CD, issue trackers. No duplicate work, no disruption.
- **Useful context:** See how code changes connect to tickets, review quality, and team goals. Less vanity stats, more signal.
- **Clear next steps:** Spot inefficiencies and get practical ways to improve, whether it's review speed, investment in features vs. fixes, or build times.

---

## Adding Metrics

Before you can add metrics, complete these setup steps:

1. [Request a guided tour to get access](https://www.gitkraken.com/insights#form).
2. Connect GitKraken Insights to your GitHub account.
3. Wait for your repositories to finish importing. For detailed instructions, see the [Getting Started guide](https://help.gitkraken.com/gk-dev/gk-dev-insights).

Once setup is complete, open the **Insights > Dashboard** tab from [gitkraken.dev](https://gitkraken.dev).

<figure>
  <img src="/wp-content/uploads/Insights-Dashboard.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Access your Insights Dashboard from gitkraken.dev.</figcaption>
</figure>

### Creating Dashboards

You can create multiple dashboards in GitKraken Insights to organize metrics by team, project, or focus area. To begin, use the dropdown menu in the top-left corner of the dashboard view. From there, select **+ Create dashboard** to open the creation modal.

<figure>
  <img src="/wp-content/uploads/create-dashboard-dropdown.png" srcset="/wp-content/uploads/create-dashboard-dropdown@2x.png" class="help-center-img img-bordered" alt="Dashboard dropdown showing Create dashboard option" />
  <figcaption style="text-align: center; color: #888">Use the dropdown menu to select an existing dashboard or create a new one.</figcaption>
</figure>

In the modal, enter a **Title** and optional **Description** to help distinguish this dashboard from others. Creating focused dashboards is especially helpful for tracking metrics by repository group, product area, or individual contributor activity.

<figure>
  <img src="/wp-content/uploads/create-dashboard-modal.png" srcset="/wp-content/uploads/create-dashboard-modal@2x.png" class="help-center-img img-bordered" alt="Create dashboard modal with title and description fields" />
  <figcaption style="text-align: center; color: #888">Name your dashboard and optionally add a description to clarify its focus.</figcaption>
</figure>

### Add a metric

1. In the Dashboard view, click the **Add Metric** button in the top-right corner.
2. Browse the list of available widgets, grouped by category (for example, **DORA** and **Pull Requests**).
3. Click **Add** next to the metric you want to display on your dashboard.

<figure>
  <img src="/wp-content/uploads/add-metric.png" srcset="/wp-content/uploads/add-metric@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Add DORA or PR metrics to your dashboard.</figcaption>
</figure>

### Available metrics

**[DORA metrics](/gk-dev/gk-dev-dora-metrics)**

- Deploy Frequency
- Change lead time
- Mean time to repair/recover
- Defect rate (% of deploy with severe defect)

**[Pull Request metrics](/gk-dev/gk-dev-pr-metrics)**

- First response time ("Pickup time")
- Cycle time ("first commit" to "merge")
- Lead time ("first commit" to "deployed")
- Number of reviews per day/week/month
- Open Time ("opened" to "merged")
- Number of PRs Abandoned
- Number of PRs Merged Without Review
- Number of PR Comments
- PR Size/Effort
- Code Review Hours

**[AI Impact metrics](/gk-dev/gk-dev-ai-impact-metrics)**

- Copy/paste vs moved percent
- Duplicated code
- Percent of code rework (churned lines)
- Post PR work occurring
- Active Users
- Suggestions (by total lines)
- Prompt Acceptance Rate
- Tab Acceptance Rate

**[Code Quality metrics](/gk-dev/gk-dev-code-quality-metrics)**

- Bug Work Percent
- Documentation and Test Percent
- Code Change Rate
- Code Change by Operation

**[Velocity/Delivery Consistency](/gk-dev/gk-dev-velocity-metrics)**

- Commit Count
- Estimated Coding Hours

---

## Layout

Widgets on the dashboard can be customized to fit your needs.

- **Resize widgets:** Each widget is available in two sizes—small or large. Drag and drop the lower-right corner of a widget to adjust its size.
- **Rearrange widgets:** Drag and drop from the upper-left corner of a widget to move it into a new position on the dashboard.
- **One per dashboard:** Only one copy of each metric can be placed on a dashboard.
- **Widget menu:** From the menu in the upper-right of each widget, you can switch between **line** and **bar** graph types, resize the widget between large or small, export the graph data, or remove the widget from the dashboard.
- **Switch graph type** Switch between line graphs, area graphs, or bar graphs.

<figure>
  <img src="/wp-content/uploads/layout-options.png" srcset="/wp-content/uploads/layout-options@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Switch between bar, area or line graphs, resize, export graph data, or remove widget from the menu in the upper right.</figcaption>
</figure>

> **Note:** Currently, each user can create only one dashboard per organization. Support for multiple dashboards per user is planned for a future release.

---

## Trendlines

You can add trendlines to any chart in GitKraken Insights to help visualize patterns over time. These overlays make it easier to understand whether your metrics are improving, declining, or fluctuating—and how consistently.

### How to add a trendline

1. On any dashboard widget, click the **⋯ (three dots)** menu in the upper-right corner.
2. Select **Set trendline**.
3. Choose one of the available types:

- **None:** No trendline is shown.
- **Linear:** Adds a straight line through the data to show steady upward or downward trends.
- **Polynomial:** Adds a curved line that reveals acceleration, deceleration, or changing directions in the data.
- **Moving Average:** Smooths out short-term fluctuations to highlight the overall pattern, especially useful for noisy or jumpy data.

<figure>
  <img src="/wp-content/uploads/trendline-menu.png" srcset="/wp-content/uploads/trendline-menu@2x.png" class="help-center-img img-bordered" alt="Chart with trendline settings menu showing Linear and Moving Average options" />
  <figcaption style="text-align: center; color: #888">From the widget menu, select a trendline type to better understand long-term changes in your metrics.</figcaption>
</figure>

> **Tip:** Use trendlines to spot steady improvements, regressions, or shifts in behavior across delivery, review, or quality metrics.

---

## Filters

The dashboard may be filtered by **Workspace**, **Repositories**, **Timeframe**, and **Team**.

- **Workspace:** Workspaces are preset groups of repositories. They also enable other key features across gitkraken.dev, GitKraken Desktop, GitLens, and the GitKraken CLI such as Launchpad and multi-repo actions. On the dashboard, you can filter to only display data for the repositories in your chosen Workspace. To create your first workspace, go to [gitkraken.dev/workspaces](https://gitkraken.dev/workspaces).

- **Repositories:** Refers to the list of repos imported into GitKraken Insights. Check or uncheck repositories to fine-tune the data. Use the search feature to quickly locate repos by name.

- **Timeframe:** Sets the timebox for the dashboard. Options include **This Week, Last Week, Last 7 days, Last 14 days, Last 28 days, Last 30 days, Last 90 days, Last 12 months**, or a custom date range.

- **Team:** Filters the data by a group of users. To configure teams, go to **Insights > Settings > Setup your Team**.


<figure>
  <img src="/wp-content/uploads/timeframe-filter.png" srcset="/wp-content/uploads/timeframe-filter@2x.png" class="help-center-img img-bordered" alt="Overview of GitKraken Insights" />
  <figcaption style="text-align: center; color: #888">Filter your dashboard by Workspace, Repo, Timeframe, or Team.</figcaption>
</figure>
