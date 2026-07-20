---
title: Connections & Token Reference
description: A single reference for every GitKraken Insights AI Adoption connection — which token or key each provider needs, the exact scopes, who can create them, and the prerequisites — so you can gather access before you start.
product: GitKraken Insights
content_type: reference
audience: admin
plan_required: GitKraken Insights
integrations: [GitHub, Bitbucket, Claude Code, Codex, Cursor, Jira Cloud]
status: GA
taxonomy:
    category: gk-insights
---
<kbd>Last updated: July 2026</kbd>

This is the at-a-glance reference for **what each AI Adoption connection needs** — token type, scopes, who must create it, and any prerequisites. For the guided, step-by-step walkthrough, use [Connect Your Data](/gk-insights/ai-adoption-connect-your-data); come here when you're gathering access or auditing a token.

> **Plan:** GitKraken Insights
> **Platform:** Browser only via [gitkraken.dev](https://gitkraken.dev)
> **Role:** Owner or Admin (to manage data connections)
> **Where you'll work:** **Insights → Settings → Data Connections**

---

## Summary matrix

| Provider | Credential | Created by | Prerequisite |
|----------|-----------|------------|--------------|
| **GitHub** | Fine-grained or classic PAT | GitHub org admin | Token's resource owner = your org |
| **Bitbucket** | Scoped Atlassian API token + account email | Bitbucket workspace admin | Select workspace(s) to sync |
| **Claude Code** | OTel snippet (no key) | Anthropic org **Owner** | Owner applies org-managed settings |
| **OpenAI Codex** | OTel snippet (no key) | AI-tool org owner | Same OTel connection as Claude Code |
| **Cursor** | Team-level **admin** API key | Cursor team admin | Must be a team key, not personal |
| **Jira** | Plain API token + account email + site URL | Jira admin | Use "Create API token" (not "with scopes") |
| **GitHub Copilot** | GitHub Org PAT + org name | *(coming soon)* | Identity mapping completed first |

Connect **at least one AI provider** (Claude Code, Codex, or Cursor) plus a git provider to populate the dashboards.

---

## GitHub

- **Credential:** a personal access token — **fine-grained** or **classic**.
  - *Fine-grained:* Repository permissions (read-only) **Metadata**, **Contents**, **Pull requests**; recommended Organization permission **Members: Read**. We can't auto-list your orgs — type the org name.
  - *Classic:* scopes **`repo`** (read) and **`read:org`**. We can list your orgs in a dropdown.
- **Set the token's Resource owner to your organization**, not your personal account.
- You can edit a token's scopes after creating it; you cannot change its expiration, so set a long one up front.

## Bitbucket

- **Credential:** a **scoped Atlassian API token** (`ATATT…`) plus the **Atlassian account email** it was created for (HTTP Basic auth). Create it at **id.atlassian.com → Security → API tokens → Create API token with scopes**.
- **Workspaces:** you select one or more **workspaces to sync** (up to 20) after the token validates. Only workspace-owned repositories are supported.
- **Scopes:**

| Scope | Needed for |
|-------|-----------|
| `read:account` | Baseline identity — **required** |
| `read:workspace:bitbucket` | Discovering/listing workspaces — **required** |
| `read:repository:bitbucket` | Repos, commits, tags — **required** |
| `read:pullrequest:bitbucket` | PRs and reviews — **required** |
| `read:pipeline:bitbucket` | *Optional* — ingest Pipelines as deployments (Deployment Frequency, Lead Time) |
| `admin:repository:bitbucket` | *Optional* — branch-restriction reading for repo-readiness scoring |

- **Good to know:** first sync reaches back ~90 days; AI co-author detection reads the PR title/description (not merge-commit bodies), so it's more conservative than on GitHub.

## Claude Code & OpenAI Codex (OpenTelemetry)

- **No API key.** These report via **OpenTelemetry**: you paste a configuration snippet — with your org's telemetry token already embedded — into your AI tool's **organization-managed settings**.
- **Who:** the **Owner** of your Anthropic (Claude Code) organization — admins cannot change org-managed settings.
- **Prerequisites & behavior:**
  - Data starts on each developer's **next session** — there is **no backfill** (Claude Code OTel instrumentation began **2026-03-05**; nothing earlier is available).
  - The default snippet collects usage/session telemetry (tokens, duration, tool calls) — **not prompt content**.
  - Warn developers first: applying org telemetry settings triggers a one-time Claude Code notice on their next session.

## Cursor

- **Credential:** a **team-level API key with admin scope** from the Cursor dashboard (API Keys → Create New Key). A personal or non-admin key can't read team usage.
- Copy it immediately — Cursor shows it once.

## Jira (optional, recommended)

- **Credential:** a **plain API token** (id.atlassian.com → **Create API token** — *not* "Create API token with scopes"), plus the **account email** and your **Jira site URL**.
- **Powers Change Failure Rate**, which additionally needs a **Customer bug field ID** and tracked releases configured — see [Configure CFR](/gk-insights/ai-adoption-connect-your-data#configure-change-failure-rate-cfr).

## GitHub Copilot *(coming soon)*

- Copilot connections are on the way and not available to connect yet.
- When available: a **GitHub Personal Access Token + organization name**, and **developer identity mapping must be complete first** — otherwise Copilot activity can't be attributed and won't backfill.

---

## Notes

- **Multiple connections per provider** are supported; give each a recognizable **Name**.
- **GitLab** activity is included through GitKraken's git integration rather than a self-service token connection here; talk to your account team about GitLab coverage.
- If you open Data Connections and see a **read-only banner**, ask an org Owner or Admin to connect or to grant you access.

## Related pages

- [Connect Your Data — Setting Up AI Adoption](/gk-insights/ai-adoption-connect-your-data) — the step-by-step walkthrough.
- [Getting Started with AI Adoption](/gk-insights/ai-adoption-getting-started)
- [AI Adoption Settings](/gk-insights/ai-adoption-settings)
