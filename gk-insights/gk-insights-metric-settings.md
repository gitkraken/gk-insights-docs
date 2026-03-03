---
title: Metric Settings in GitKraken Insights
description: Learn how to configure release tracking, issue detection, issue tracker projects, critical defect terms, and measurement settings in GitKraken Insights.
taxonomy:
    category: gk-dev
---
<kbd>Last updated: March 2026</kbd>

---

<figure>
  <img src="/wp-content/uploads/measurement-config.png" srcset="/wp-content/uploads/measurement-config@2x.png" class="help-center-img img-bordered" alt="Insights settings page showing the Measurement Configuration section with Release setup highlighted" />
  <figcaption style="text-align: center; color: #888">Navigate to Measurement Configuration in Insights settings to access release tracking, issue detection, and other metric settings.</figcaption>
</figure>

## Release Tracking

Configure how GitKraken Insights detects new releases for your repositories.

### Rules to detect releases

The **Rules to detect releases** list shows all active release rules for your organization. Each rule displays:

- The rule type
- A summary of the matching condition
- The number of releases and repositories matched
- Who created the rule

The following rule types appear in your list:

- **Contains Branch Prefix** — Matches commits pushed to a branch that starts with a specified string.
- **Merged Pull Request To Branch Prefix** — Matches commits that merge a pull request to a branch with a specified prefix.
- **Any Git Tag** — Matches commits with any git tag pushed.
- **Matches Branch** — Matches commits made to a specific branch.
- **Api Call** — Matches releases reported via API call.

To remove a rule, click the **✕** icon on the right side of the rule.

<figure>
  <img src="/wp-content/uploads/release-tracking-rules.png" srcset="/wp-content/uploads/release-tracking-rules@2x.png" class="help-center-img img-bordered" alt="Release tracking settings page showing a list of active release rules" />
  <figcaption style="text-align: center; color: #888">The Rules to detect releases list shows all active release rules for your organization.</figcaption>
</figure>

### Create a new release rule

To add a new rule, click **Create a new release rule**. GitKraken Insights attempts to apply the rule to all connected repositories.

In the rule creation form, select how GitKraken Insights should identify releases. As you configure each option, the **Matching commits** panel on the right previews commits that match your current input.

<figure>
  <img src="/wp-content/uploads/release-tracking-new-rule.png" srcset="/wp-content/uploads/release-tracking-new-rule@2x.png" class="help-center-img img-bordered" alt="Release tracking rules list with the Create a new release rule button highlighted" />
  <figcaption style="text-align: center; color: #888">Click Create a new release rule at the bottom of the rules list to add a new rule.</figcaption>
</figure>

<figure>
  <img src="/wp-content/uploads/release-tracking-new-rule-options.png" srcset="/wp-content/uploads/release-tracking-new-rule-options@2x.png" class="help-center-img img-bordered" alt="Create release rule modal showing all available rule type options and a Matching commits preview panel" />
  <figcaption style="text-align: center; color: #888">Select a rule type to define how GitKraken Insights identifies releases. The Matching commits panel previews commits that match your configured rule in real time.</figcaption>
</figure>

#### When a pull request is merged to a branch that starts with

Identifies a release when a pull request is merged to a branch matching a specified prefix.

- **Input:** Enter a branch name prefix. Leave blank to match the default `main` or `master` branch.

#### When a git tag contains a specific substring

Identifies a release when a git tag contains a matching string or pattern.

- **Input:** Enter a string or regular expression pattern that appears in tags.

#### When a GitHub Action successfully completes

Identifies a release when a specified GitHub Action workflow completes successfully.

> <!-- FLAG FOR HUMAN REVIEW: No screenshot of this option selected was provided. Inputs and additional fields are unknown. -->

#### When a commit message contains a specific string

Identifies a release when a commit message contains a specified partial string.

- **Input:** Enter a partial commit message that indicates a release. Must be at least 3 characters.

#### When a commit message matches a specific string

Identifies a release when a commit message exactly matches a specified string.

- **Input:** Enter the exact commit message that indicates a release.

#### When a commit is pushed to a particular branch

Identifies a release when any commit is pushed to a selected branch.

- **Input:** Select a branch from the dropdown.
- **Note:** GitKraken Insights counts any commit pushed to this branch after today as a release. It does not apply historic commits retroactively.

#### When a commit is pushed to a branch that starts with this string

Identifies a release when a commit is pushed to a branch whose name starts with a specified prefix.

- **Input:** Enter a case-sensitive prefix for a deploy branch.
- **Option:** Check **A number must occur in the branch name to be deemed a release** to further restrict matches.
- **Note:** GitKraken Insights counts any commit pushed to a matching branch after today as a release. It does not detect historic releases.

#### When any git tag is pushed

Identifies a release whenever any git tag is pushed, regardless of tag name or format. No additional input is required.

---

<!-- Sections to be added: Detect issues, Define issue tracker projects, Critical defect terms, Measurement configuration -->
