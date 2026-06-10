---
title: AI Adoption Settings in GitKraken Insights
description: Reference for the admin settings that affect AI Adoption scores in GitKraken Insights, including Maturity Factor, Tier Weights, Developer Hourly Rate, and Baseline Period.
product: GitKraken Insights
content_type: reference
audience: admin
plan_required: GitKraken Insights
integrations: [Claude Code, Codex, Cursor]
status: GA
taxonomy:
    category: gk-insights
---
<kbd>Last updated: June 2026</kbd>

<!-- FLAG FOR HUMAN REVIEW: The source Confluence "Settings & Admin" page also documents Developers (Roster), Teams, Jira (CFR), Time Off (BambooHR), and Demo Mode sections. Those were not migrated here because they cover product-wide administration rather than AI Adoption. Decide whether they belong on a separate admin page. -->

Every admin-configurable setting that affects AI Adoption scores in GitKraken Insights, organized by where it lives in the product, plus a one-line "what it changes."

If you came from a metric page to look up a specific setting, jump to the anchor of the same name.

**What's in the Settings UI today vs. backend-only.** As of 2026-05-28, the Settings → General form writes these four keys: `maturity_factor`, `developer_hourly_rate`, `baseline_period_start`, `default_department`. The other per-org settings on this page — **Tier Weights**, **Direct Commit Weight**, **Exclude Chore from Output Score** — are stored in the same `app_settings` table but are not yet exposed in the UI form. To change those today, file a request with support and we'll set them directly. A self-serve form is on the roadmap.

---

<!-- FLAG FOR HUMAN REVIEW: Screenshot in source Confluence page. Caption: "Settings → General — Maturity Factor, Developer Hourly Rate, Baseline Period, and Default Department. (Tier Weights, Direct Commit Weight, and Exclude Chore are stored in app_settings but not yet exposed in the form.)" Export to _images/ and add the figure here. -->

## General settings

The single most impactful set of knobs. These shift how scores are calculated for every developer in your org.

### Maturity Factor

Also labeled **"Company AI Readiness %"** in the General tab. _In Settings UI: yes._

|  |  |
| --- | --- |
| **Default** | 0.75 (75%) |
| **Range** | 0.01 – 1.00 |
| **Type** | Float |

**What it does.** Scales every P90-based score (Adoption, Agentic, Output Norm) downward. At 1.00, a developer at the org's 90th percentile scores 100. At 0.75, the same developer scores 75 — leaving headroom for the org to grow into the Power User band.

**Why you'd raise or lower it.** - **Lower (0.50 – 0.70):** Early in your AI rollout. You want every developer to feel like there's runway. Few or no Power Users yet. - **Default (0.75):** Most orgs in active rollout. The tier ceiling pushes the top 10% to keep stretching. - **Higher (0.85 – 1.00):** Mature orgs with widespread, deep adoption where you want the scoring to reflect that maturity in absolute terms.

**Affects:** [Agent Adoption Score](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#agent-adoption-score), [Agent Autonomy Score](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#agent-autonomy-score), [Output Norm](/gk-insights/ai-adoption/ai-adoption-output-metrics#output-score), [AI Tier](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#ai-tier).

→ Full section: [Maturity Factor](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#maturity-factor)

---

### Tier Weights

Three positive numbers that say how much Adoption, Agentic, and Output each count toward the [AI Tier](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#ai-tier) composite. _In Settings UI: not yet — change via support (see panel above)._

| Weight | Default | App-settings key | What it emphasizes |
| --- | --- | --- | --- |
| **Adoption** | 0.5 | `tier_weight_adoption` | Daily, consistent AI use |
| **Agentic** | 0.2 | `tier_weight_agentic` | Autonomous multi-step AI work |
| **Output** | 0.3 | `tier_weight_output` | Effort-weighted shipping rate |

**Range:** Each weight is any positive number (we store raw values, then renormalize to sum to 1.0 on read).

**What it does.** The three weights compete for the 100% budget. The tier-badge tooltip in the app shows the live percentages for every developer.

**How to think about tuning.** - Adoption-heavy (e.g. 0.7 / 0.1 / 0.2): "We care that everyone is _trying_ AI. Output will follow." - Output-heavy (e.g. 0.3 / 0.1 / 0.6): "We've moved past the rollout phase — now we care about delivery." - Balanced (the default): A signal that AI use without output is incomplete, and output without AI is the old way.

**Guardrails.** If you set all three to zero we fall back to the defaults (0.5 / 0.2 / 0.3) — never a "100% output, 0% everything else" boost. Negative or NaN values are rejected and the default for that key is used.

**Affects:** [AI Tier](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#ai-tier) — and through it, the developer table sorting, the Top 10 widget, the executive ranking, and every breakdown chart that buckets by AI Tier.

→ See also: [Playbook — Set tier weights for your org's maturity](/gk-insights/ai-adoption/ai-adoption-playbooks#set-tier-weights-for-your-orgs-maturity)

---

### Direct Commit Weight

_In Settings UI: not yet — change via support._ App-settings key: `direct_commit_weight`.

|  |  |
| --- | --- |
| **Default** | 0.5 |
| **Range** | 0.0 – 1.0 |
| **Type** | Float |

**What it does.** Scales direct commits (pushes straight to a default branch with no PR) relative to merged PRs in the [Output Score](/gk-insights/ai-adoption/ai-adoption-output-metrics#output-score) formula:

```
Output Score = SUM(PR effort) + DirectCommitWeight × SUM(DC effort)
```

* **0.0** — direct commits are ignored entirely
* **0.5** (default) — a direct commit counts half as much as a PR of equivalent effort
* **1.0** — direct commits count as much as PRs

**When to change it.** - Lower toward 0 if your team uses direct commits primarily for trivial maintenance and you don't want them inflating Output Score. - Raise toward 1 if your team uses direct commits for substantive work (e.g. a Trunk-Based Development workflow).

**Affects:** [Output Score](/gk-insights/ai-adoption/ai-adoption-output-metrics#output-score), [Output Norm](/gk-insights/ai-adoption/ai-adoption-output-metrics#output-score), [AI Tier](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#ai-tier).

---

### Exclude Chore from Output Score

_In Settings UI: not yet — change via support._ App-settings key: `output_score_exclude_chore`.

|  |  |
| --- | --- |
| **Default** | On (chores excluded) |
| **Type** | Boolean toggle |

**What it does.** When **on**, Chore-category PRs and commits are subtracted from the _effort_ side of the Output Score. The displayed PR / DC _counts_ still include chores — only the effort sums change.

**Why the asymmetric treatment.** If a developer's window happens to be all chores (e.g. they spent a sprint on dependency bumps), we don't want them to disappear from the developer table. The Output Score will dip, but the count cell still says "5 PRs, 12 direct commits" so they remain visible. The Output Score tooltip shows you the chore subset that was subtracted.

**When to turn off.** Rarely. The default reflects most orgs' definition of "real output". Turn off if you've explicitly decided chores are part of how you measure delivery — e.g. for an SRE team where dependency upgrades _are_ the job.

**Affects:** [Output Score](/gk-insights/ai-adoption/ai-adoption-output-metrics#output-score), and downstream [AI Tier](/gk-insights/ai-adoption/ai-adoption-agentic-metrics#ai-tier).

---

### Developer Hourly Rate

_In Settings UI: yes._

|  |  |
| --- | --- |
| **Default** | $75 / hour |
| **Range** | $1 – unbounded |
| **Type** | Currency |

**What it does.** Multiplies into productivity-value calculations on the AI Impact and CapEx pages. We use this to translate "additional hours per developer per week" into a dollar figure.

**How to set it.** Use your fully-loaded internal developer cost rate (salary × benefits × overhead, divided by working hours). Most orgs land between $50 and $200/hour. If you don't have a precise number, the default $75 is a reasonable industry midpoint for a senior IC.

**Affects:** [Productivity Uplift](/gk-insights/ai-adoption/ai-adoption-impact-cost-metrics#productivity-uplift), [CapEx / OpEx Split](/gk-insights/ai-adoption/ai-adoption-impact-cost-metrics#capex--opex-split), the AI Impact ROI cards.

---

### Baseline Period

_In Settings UI: yes._

|  |  |
| --- | --- |
| **Default** | November 1 of previous year through the first day of the current month |
| **Type** | Date |

**What it does.** Sets the historical reference window for trend comparisons. AI Impact uplift math, productivity delta, and the "vs. baseline" cards on the executive view all compare your current window to this baseline.

**Why November 1?** Calendar-year reset point. By default the baseline window runs roughly the previous calendar year, which is a stable comparison most leaders understand instinctively.

**When to change it.** Pick a different anchor if: - Your AI rollout started mid-year and you want to compare against pre-rollout months. - Your fiscal year doesn't start in January. - You want a fixed snapshot (e.g. "Q1 2026") to compare every subsequent quarter against.

**Affects:** AI Impact uplift cards, ROI calculations, baseline-comparison trend overlays.

---

### Default Department

_In Settings UI: yes._

|  |  |
| --- | --- |
| **Default** | None (admin picks) |
| **Type** | Dropdown |

**What it does.** Pre-selects which teams are visible to a user the first time they hit the dashboard. Once a user has saved a different selection it sticks per-user in browser storage.

**When to set it.** Use this to anchor the dashboard to the largest, most-watched department in your org. Engineering leadership usually picks "Engineering" or the equivalent rolled-up group.

**Affects:** Initial view on /teams, /developers, /executive, and every page with a team filter.

---

## What's not configurable (yet)

These behaviors are deliberately fixed in code. If you need them tunable, ask your account manager — they're candidates for a future setting.

* **Tier thresholds** (Emerging < 25, Explorer 25–54, Regular 55–79, Power User ≥ 80). The Maturity Factor is the intended knob for shifting tier population, not the thresholds themselves.
* **Small-cohort fallback** (5 developers; synthetic P90 of 5.0 effort/week).
* **Agentic threshold** (10 tools in a session to count as "agentic").
* **Cursor secondary boost** (25% — set via `SCORE_SECONDARY_BOOST` env var if needed).
* **Provider weight structures** (the four-factor blend per provider). Tunable via `SCORE_WEIGHT_*` env vars.
* **Sync safety lag** (12h default per provider; `SNOWFLAKE_SYNC_SAFETY_LAG_HOURS`, `CODEX_SYNC_SAFETY_LAG_HOURS`, `CURSOR_SYNC_SAFETY_LAG_HOURS`).

---

## Related reading

* [Playbook — Set tier weights for your org's maturity](/gk-insights/ai-adoption/ai-adoption-playbooks#set-tier-weights-for-your-orgs-maturity)
* [Playbook — Roll out AI tooling with the Adoption Score](/gk-insights/ai-adoption/ai-adoption-playbooks#roll-out-ai-tooling-with-the-adoption-score)
