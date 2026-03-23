---
title: Dashboard Configuration in GitKraken Insights
description: Learn how to create dashboards, add metrics, arrange widget layouts, apply trendlines, and filter data in GitKraken Insights.
product: GitKraken Insights
content_type: how-to
audience: all
plan_required: GitKraken Insights
status: GA
taxonomy:
    category: gk-insights
---
<kbd>Last updated: March 2026</kbd>


## What GitKraken Insights dashboards display

GitKraken Insights dashboards display Git activity, pull requests, issues, and CI/CD results in a single view. Each dashboard contains configurable metric widgets that can be filtered by workspace, repository, timeframe, and team. This page covers how to create dashboards, add metrics, customize layouts, apply trendlines, and filter data.

> **Plan:** GitKraken Insights
> **Platform:** Browser only — [gitkraken.dev](https://gitkraken.dev)
> **Role:** Lead, Admin, or Owner
> **Prerequisite:** Connected repositories (see [Getting Started](/gk-dev/gk-dev-insights))
> **Limitation:** Each user can currently create one dashboard per organization.

---

## Adding Metrics

Before you can add metrics, complete these setup steps:

1. [Request a guided tour to get access](https://www.gitkraken.com/insights#form).
2. Connect GitKraken Insights to your GitHub account.
3. Wait for your repositories to finish importing. For detailed instructions, see the [Getting Started guide](https://help.gitkraken.com/gk-dev/gk-dev-insights).

Once setup is complete, open the **Insights > Dashboard** tab from [gitkraken.dev](https://gitkraken.dev).

<!-- FLAG FOR HUMAN REVIEW: Insights-Dashboard.png uses non-standard capitalization and may not exist. Likely should be insights-dashboard-oct-2025.png. -->
<figure>
  <img src="/wp-content/uploads/Insights-Dashboard.png" class="help-center-img img-bordered" alt="Screenshot of Insights Dashboard in gitkraken.dev for viewing metrics and widgets" />
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



### Duplicate a dashboard

You can duplicate an existing dashboard to quickly create a new version with the same configuration, filters, and widgets. This is useful when you want to reuse a dashboard as a starting point without modifying the original.

#### Steps

1. Navigate to **Dashboards** in GitKraken Insights.
2. Locate the dashboard you want to duplicate.
3. Click the **Actions** dropdown on the right side of the dashboard row.
4. Select **Duplicate**.

<figure>
  <img src="/wp-content/uploads/gki-duplicate-dashboard.png" class="help-center-img img-bordered" alt="Duplicate dashboard option in the Actions dropdown menu" />
  <figcaption style="text-align: center; color: #888">Select Duplicate from the Actions menu</figcaption>
</figure>

5. In the **Copy dashboard** dialog, review or update the following fields:
   - **Title**: Enter a name for the new dashboard.
   - **Description**: (Optional) Update the description.
6. Click **Make copy**.

<figure>
  <img src="/wp-content/uploads/gki-copy-dashboard-dialog.png" class="help-center-img img-bordered" alt="Copy dashboard dialog showing title and description fields" />
  <figcaption style="text-align: center; color: #888">Update the dashboard details, then click Make copy</figcaption>
</figure>

The duplicated dashboard will appear in your dashboard list with the same configuration as the original.

#### Notes

- Duplicating a dashboard does not affect the original dashboard.
- The new dashboard is created with the same widgets and filters as the original.

### Add a metric

1. In the Dashboard view, click the **Add Metric** button in the top-right corner.
2. Browse the list of available widgets, grouped by category (for example, **DORA** and **Pull Requests**).
3. Click **Add** next to the metric you want to display on your dashboard.

<figure>
  <img src="/wp-content/uploads/add-metric.png" srcset="/wp-content/uploads/add-metric@2x.png" class="help-center-img img-bordered" alt="Screenshot of Add Metric dialog listing DORA and Pull Request metrics to add" />
  <figcaption style="text-align: center; color: #888">Add DORA or PR metrics to your dashboard.</figcaption>
</figure>

### Browse available metrics

| Metric | Category | Description |
|---|---|---|
| Deploy Frequency | [DORA](/gk-dev/gk-dev-dora-metrics) | Total deployments per period |
| Change Lead Time | [DORA](/gk-dev/gk-dev-dora-metrics) | First commit to deployment |
| Mean Time to Repair/Recover | [DORA](/gk-dev/gk-dev-dora-metrics) | Defect detected to fix deployed |
| Defect Rate | [DORA](/gk-dev/gk-dev-dora-metrics) | % of deployments with critical defect |
| First Response Time | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | PR opened to first review/comment |
| Cycle Time | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | First commit to PR merge |
| Lead Time | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | First commit to deployed |
| Number of Reviews | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | Review volume per period |
| Open Time | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | PR opened to merged |
| PRs Abandoned | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | PRs closed without merge |
| PRs Merged Without Review | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | PRs merged with no review |
| PR Comments | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | Total comments on PRs |
| PR Size/Effort | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | Aggregate diff delta of merged PRs |
| Code Review Hours | [Pull Requests](/gk-dev/gk-dev-pr-metrics) | Avg review time per committer |
| Copy/Paste vs Moved % | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | Duplicated vs refactored code |
| Duplicated Code | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | Lines in duplicate blocks |
| Percent of Code Rework | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | Recently written code modified again |
| Post PR Work Occurring | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | Follow-up work after merge |
| Active Users | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | Unique users in AI providers |
| Suggestions | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | AI-generated suggestions (by total lines) |
| Prompt Acceptance Rate | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | % of prompt suggestions accepted |
| Tab Acceptance Rate | [AI Impact](/gk-dev/gk-dev-ai-impact-metrics) | % of tab suggestions accepted |
| Bug Work Percent | [Code Quality](/gk-dev/gk-dev-code-quality-metrics) | Bug fix work vs all other work |
| Documentation and Test % | [Code Quality](/gk-dev/gk-dev-code-quality-metrics) | Work related to tests and documentation |
| Code Change Rate | [Code Quality](/gk-dev/gk-dev-code-quality-metrics) | Age of code being changed |
| Code Change by Operation | [Code Quality](/gk-dev/gk-dev-code-quality-metrics) | Changes by type (test, doc, FE, BE) |
| Commit Count | [Velocity](/gk-dev/gk-dev-velocity-metrics) | Commits to connected repositories |
| Estimated Coding Hours | [Velocity](/gk-dev/gk-dev-velocity-metrics) | Estimated time spent coding |

---

## Customize widget layout

Widgets on the dashboard can be customized to fit your needs.

- **Resize widgets:** Each widget is available in two sizes—small or large. Drag and drop the lower-right corner of a widget to adjust its size.
- **Rearrange widgets:** Drag and drop from the upper-left corner of a widget to move it into a new position on the dashboard.
- **One per dashboard:** Only one copy of each metric can be placed on a dashboard.
- **Widget menu:** From the menu in the upper-right of each widget, you can switch between **line** and **bar** graph types, resize the widget between large or small, export the graph data, or remove the widget from the dashboard.
- **Switch graph type** Switch between line graphs, area graphs, or bar graphs.

<figure>
  <img src="/wp-content/uploads/layout-options.png" srcset="/wp-content/uploads/layout-options@2x.png" class="help-center-img img-bordered" alt="Screenshot of widget menu to switch chart types, resize, export data, or remove widgets" />
  <figcaption style="text-align: center; color: #888">Switch between bar, area or line graphs, resize, export graph data, or remove widget from the menu in the upper right.</figcaption>
</figure>

> **Note:** Currently, each user can create only one dashboard per organization. Support for multiple dashboards per user is planned for a future release.

---

## Add trendlines to charts

You can add trendlines to any chart in GitKraken Insights to help visualize patterns over time. These overlays make it easier to understand whether your metrics are improving, declining, or fluctuating—and how consistently.

### How to add a trendline

1. On any dashboard widget, click the **⋯ (three dots)** menu in the upper-right corner.
2. Select **Set trendline**.
3. Choose one of the available types:

- **None:** No trendline is shown.
- **Linear:** Adds a straight line through the data to show steady upward or downward trends.
- **Polynomial:** Adds a curved line that reveals acceleration, deceleration, or changing directions in the data.
- **Moving Average:** Smooths out short-term fluctuations to highlight the overall pattern, especially useful for noisy or jumpy data.

> **Use Linear** to see if a metric is steadily improving or declining over a long period. **Use Polynomial** when you suspect acceleration, deceleration, or directional changes. **Use Moving Average** when data is noisy and you need to smooth out short-term fluctuations.

<figure>
  <img src="/wp-content/uploads/trendline-menu.png" srcset="/wp-content/uploads/trendline-menu@2x.png" class="help-center-img img-bordered" alt="Chart with trendline settings menu showing Linear and Moving Average options" />
  <figcaption style="text-align: center; color: #888">From the widget menu, select a trendline type to better understand long-term changes in your metrics.</figcaption>
</figure>

> **Tip:** Use trendlines to spot steady improvements, regressions, or shifts in behavior across delivery, review, or quality metrics.

---

## Filter dashboard data

The dashboard may be filtered by **Workspace**, **Repositories**, **Timeframe**, and **Team**.

- **Workspace:** Workspaces are preset groups of repositories. They also enable other key features across gitkraken.dev, GitKraken Desktop, GitLens, and the GitKraken CLI such as Launchpad and multi-repo actions. On the dashboard, you can filter to only display data for the repositories in your chosen Workspace. To create your first workspace, go to [gitkraken.dev/workspaces](https://gitkraken.dev/workspaces).

- **Repositories:** Refers to the list of repos imported into GitKraken Insights. Check or uncheck repositories to fine-tune the data. Use the search feature to quickly locate repos by name.

- **Timeframe:** Sets the timebox for the dashboard. Options include **This Week, Last Week, Last 7 days, Last 14 days, Last 28 days, Last 30 days, Last 90 days, Last 12 months**, or a custom date range.

- **Team:** Filters the data by a group of users. To configure teams, go to **Insights > Settings > Setup your Team**.


<figure>
  <img src="/wp-content/uploads/timeframe-filter.png" srcset="/wp-content/uploads/timeframe-filter@2x.png" class="help-center-img img-bordered" alt="Dashboard view of filters for workspace, repository, timeframe, and team" />
  <figcaption style="text-align: center; color: #888">Filter your dashboard by Workspace, Repo, Timeframe, or Team.</figcaption>
</figure>
