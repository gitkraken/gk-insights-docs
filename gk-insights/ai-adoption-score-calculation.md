---
title: How AI Adoption Scores Are Calculated
description: The end-to-end reference for how GitKraken Insights turns AI-tool telemetry and git activity into the Adoption, Autonomy, Output, and AI Tier scores — the full formula pipeline in one place, with links to each detailed metric page.
product: GitKraken Insights
content_type: reference
audience: all
plan_required: GitKraken Insights
integrations: [Claude Code, Codex, Cursor]
status: GA
taxonomy:
    category: gk-insights
---
<kbd>Last updated: July 2026</kbd>

This page is the single reference for **how the AI Adoption scores are calculated**, end to end. Each score has its own detailed page; this one shows how they connect — the pipeline from raw signals to the AI Tier a developer lands in — so you can explain and defend the numbers.

> **Plan:** GitKraken Insights
> **Platform:** Browser only via [gitkraken.dev](https://gitkraken.dev)
> **Role:** Lead, Admin, or Owner
> **Prerequisite:** Connected GitHub or Bitbucket and at least one AI provider. See [Connect Your Data](/gk-insights/ai-adoption-connect-your-data).

---

## The pipeline at a glance

```
AI-tool telemetry ──► per-provider score (four-factor blend)
git activity      ──► Output Score ──► Output Norm (rate vs org P90)
                             │
   Adoption Score ◄──────────┤
   Autonomy Score ◄──────────┘
                             │
                             ▼
         AI Tier = weighted blend of Adoption, Autonomy, Output Norm
                             │
                             ▼
     Emerging · Exploring · Regular · Power User   (or On PTO)
```

Three scores feed one composite. Everything below the per-provider step is a normalized 0–100 number.

---

## 1. Per-provider score (the four-factor blend)

Each connected AI provider (Claude Code, Codex, Cursor) is scored independently from four signals:

- **Daily Use** — how many days the developer used the tool
- **Hourly Spread** — how spread across the workday that use was
- **Prompts** — prompt/request volume
- **Output** — token/lines produced

These four combine with fixed weights (`SCORE_WEIGHT_*`, set at the deployment level — see [what's not configurable](/gk-insights/ai-adoption-settings#whats-not-configurable-yet)). The blend within a provider is not org-tunable; **how much each provider counts relative to the others is** — see [Provider Weights](/gk-insights/ai-adoption-settings#provider-weights).

---

## 2. Adoption Score

**Measures:** how much your team is actually using AI, day to day.

```
Adoption = min(Primary + 0.25 × Cursor, 100) × Maturity Factor
           where Primary = four-factor blend of Claude ∪ Codex
                 Cursor  = four-factor blend of Cursor (secondary/confirmatory signal)
```

- **Cursor is a 25% secondary boost** (`SCORE_SECONDARY_BOOST`), not a primary signal — its event stream is sparser, so it confirms rather than drives.
- **Maturity Factor** (default **0.75**) scales the whole score to set the tier ceiling for your org. Lower it while a rollout is young; raise it as the org matures.

→ Full detail: [Agent Adoption Score](/gk-insights/ai-adoption-agentic-metrics#agent-adoption-score) · settings: [Maturity Factor](/gk-insights/ai-adoption-settings#maturity-factor)

---

## 3. Autonomy Score (Agentic)

**Measures:** how *autonomously* the team uses AI — multi-step agentic work, not single completions.

- Built from **Claude Code and Codex only** (Cursor is excluded — it isn't an agentic signal).
- Counts sessions that cross the **agentic threshold of 10 tool calls** in a session.

→ Full detail: [Agent Autonomy Score](/gk-insights/ai-adoption-agentic-metrics#agent-autonomy-score)

---

## 4. Output Score → Output Norm

**Measures:** how much real work shipped — effort-weighted, not a raw count.

```
Output Score = SUM(authored-PR effort)
             + DirectCommitWeight × SUM(direct-commit effort)
             + ReviewWeight       × SUM(reviewed-PR effort)
```

- **Effort Score** per PR / commit is an LLM-judged complexity rating in five tiers (**0.1–0.9**), LOC-blind.
- **Default weights:** Direct Commit **0.5**, Review **0.5** (both org-tunable).
- **Output Norm** is Output Score expressed as a per-week rate and normalized against your organization's **P90** so it can sit on the same 0–100 scale as Adoption and Autonomy. Small orgs (< 5 developers) use a synthetic P90 fallback.

→ Full detail: [Output & Throughput Metrics](/gk-insights/ai-adoption-output-metrics) · settings: [Direct Commit Weight](/gk-insights/ai-adoption-settings#direct-commit-weight), [Review Weight](/gk-insights/ai-adoption-settings#review-weight)

---

## 5. AI Tier (the composite)

The headline tier blends the three normalized scores:

```
AI Tier score = w_adoption × Adoption
              + w_agentic  × Autonomy
              + w_output   × Output Norm
```

- **Default weights:** Adoption **0.5** / Autonomy **0.2** / Output **0.3**. Org-tunable in [Settings → General](/gk-insights/ai-adoption-settings#tier-weights); stored raw and **renormalized to sum to 1.0** on read. If all three are set to zero, the defaults are restored.
- **Tier bands** (fixed):

| Tier | Score |
|------|-------|
| **Power User** | ≥ 80 |
| **Regular** | 55–79 |
| **Exploring** | 25–54 |
| **Emerging** | < 25 |
| **On PTO** | developer was on approved leave for the window |

→ Full detail: [AI Tier](/gk-insights/ai-adoption-agentic-metrics#ai-tier)

---

## Reading the scores responsibly

- These scores describe **behavior and throughput, not developer worth.** Use them to spot rollout friction and coaching opportunities, not to rank people. See [Getting Started → How to think about developer scores](/gk-insights/ai-adoption-getting-started#how-to-think-about-developer-scores).
- **Percentile-based numbers move week to week** as the org cohort shifts — read trends, not single-week snapshots.
- Set **no numeric targets** on individuals; targets invert the signal.

## Related pages

- [Adoption & Agentic Metrics](/gk-insights/ai-adoption-agentic-metrics)
- [Output & Throughput Metrics](/gk-insights/ai-adoption-output-metrics)
- [AI Impact & Cost Metrics](/gk-insights/ai-adoption-impact-cost-metrics)
- [AI Adoption Settings](/gk-insights/ai-adoption-settings)
- [AI Adoption Playbooks](/gk-insights/ai-adoption-playbooks)
