# GitKraken Insights: product notes for the docs-authoring skill

The Insights Help Center (`help.gitkraken.com/gk-insights/`): the AI Adoption
pages, merged on 2026-11-11 from gk-insights-docs-expo into
gitkraken/gk-insights-docs `expo`, alongside the classic `gk-insights-*` pages.
This is the seed of the Insights repo's `product/` folder; skillsync shipped it
to that repo's `main` and `expo` on 2026-11-11. `product/` is the repo's own
from then on: edit it there.

| | |
| --- | --- |
| Content folder | `gk-insights/` (images in `_images/`), in gitkraken/gk-insights-docs |
| WordPress category | `gk-insights`: pages publish at `/gk-insights/<slug>/` |
| Home page | `ai-adoption-home` (`main-index`; the Insights home module: hero, role paths, metric map) |
| Nav | front matter only (no nav file); sections by `nav_category` |
| Pipelines | metric pipeline, instruments, settings spec panels, playbook steps |
| Auth gate | Insights only, off unless enabled in WP Admin |
| Metadata check | off (FRONTMATTER-SCHEMA.md covers the 8 redesign repos) |

Files in this folder:

- `config.json`: the facts above, for `check_pages.py` and the preview
- `metric-pages.md`: metric pages (the 12-section skeleton, formula panel,
  step rail, tier scale, FAQ, "Where it appears"), playbook steps and
  branches, settings blocks
- `templates.md`: skeletons for a metric page, a family sub-index, a section
  index, a connect/how-to page and a playbook

## How the Insights nav differs

- **Sections are fixed keys**, ordered by the registry's `section_order`
  (`includes/gkhc-registry.php`): `getting-started` → `connect-your-data` →
  `metrics` → `playbooks` → `admin`, plus `home` (Home) and `hidden` (out of
  the nav). A new key renders after Admin & API unless it is added there
  (plugin change), and it needs exactly one un-parented `page_type: index`
  page.
- **Section fallback**: an un-parented `content` page hangs under its
  section's un-parented index page, so most pages omit `nav_parent`.
- **`nav_parent` must be an `index` page in the same `nav_category`.**
- **Every page has `custom_fields`** with `card_icon`, `card_color` (per
  section, below) and `card_description`. `hidden` pages set the three
  `card_*` fields to `""` and use `nav_order: 99`.
- **`nav_category: metrics` + `page_type: content` routes a page through the
  metric pipeline** (`metric-pages.md`). A metric page without `nav_parent`
  is left off the Home metric map.
- **Index cards** come from `nav_parent` children, else the section's
  un-parented `content` pages (the `legacy` index mode).
- Callouts use lead phrases typed by keyword (`> **Before you start:**` is
  info, `> **Heads up:**` is warn); the content adapters don't run on
  Insights.

## Changes that need plugin work (gkhc-plugin-design)

| Change | Why |
|---|---|
| A new metric needs an interactive instrument | Instruments are mapped by slug tail in `gkhc_passc_instruments()` and drawn by `js/gkhc-passc.js` |
| Home hero headline, the four role cards, the "derived" chips on the metric map | Hard-coded in `templates/single-gkhc.php`, `gkhc_passc_role_paths()`, `gkhc_passc_metric_map()` |
| A new top-level section | `section_order` in `includes/gkhc-registry.php` |

## Naming

- File name: `ai-adoption-<section-or-family>-<topic>.md`, lowercase and
  hyphenated (the checker warns on any other prefix). Metric pages carry
  their family prefix (`dora-`, `flow-`, `output-`, `agentic-`,
  `impact-cost-`). The instrument registry and Home's role paths
  (`for-executives` etc.) match on the slug tail, so don't rename those pages
  casually.
- The settings mini-spec-panel transform runs on a slug ending in
  `-settings` (or `layout: settings`).
- Internal links: `/gk-insights/ai-adoption-<name>`.

## Current map (November 2026)

Check this against the files before you rely on it. Running
`check_pages.py` confirms the hierarchy is consistent.

| Section (`nav_category`) | Index page (`nav_order`) | Colour | Children |
|---|---|---|---|
| home | `ai-adoption-home` (0, `main-index`) | purple | — |
| getting-started | `ai-adoption-getting-started` (10) | purple | first-dashboard 10, for-executives 20, for-engineering-leaders 30, for-team-leads 40, for-admins 50, developers 60, repositories 65, ai-sessions 70, ai-tools-comparison 75, surveys 80, insights-for-developers 90. Each has its own `card_icon`. |
| connect-your-data | `ai-adoption-connect-your-data` (20) | blue | connect-github 10, -bitbucket 20, -azure-devops 30, -gitlab 40, -ai-tools 50, -otel 55, -jira-bamboohr 60, -linear-youtrack 65, -clickup 67 |
| metrics | `ai-adoption-metrics` (30) | green | five family sub-indexes, each `nav_parent: ai-adoption-metrics` (below) |
| playbooks | `ai-adoption-playbooks` (40) | amber | playbook-tier-weights 10, -ai-rollout 20, -slow-cycle-time 30, -high-cfr 40 |
| admin | `ai-adoption-admin` (50) | red | settings 10, manual-releases-api 20, security-permissions 30 |
| hidden | — | — | `ai-adoption` (redirect), `ai-adoption-manual-critical-defects-api` (draft) |
| (outside the nav) | — | — | no `custom_fields`: the classic `gk-insights` and `gk-insights-*` pages, `surveys`, and the `exploration-v1/v2/v3` drafts, all from the repo's `main` before the merge |

Metric families (`page_type: index`, `nav_category: metrics`,
`nav_parent: ai-adoption-metrics`). Each child metric page uses the
family's icon and `nav_order` = family order + 1, 2, 3 …

| Family sub-index | `nav_order` | `card_icon` | Metric pages (slug tail → order) |
|---|---|---|---|
| `ai-adoption-agentic-metrics` — Adoption & Agentic | 10 | `user-check` | agentic-adoption-score 11, agentic-autonomy-score 12, agentic-ai-tier 13, agentic-maturity-factor 14, agentic-cursor-boost 15 |
| `ai-adoption-output-metrics` — Output & Throughput | 20 | `package` | output-output-score 21, output-throughput 22, output-direct-commits 23, output-effort-score 24 |
| `ai-adoption-flow-metrics` — Flow & Cycle Time | 30 | `clock` | flow-cycle-time 31, flow-review-cycles 32, flow-first-pass-rate 33, flow-wip 34 |
| `ai-adoption-dora-metrics` — DORA & Quality | 40 | `shield-check` | dora-deployment-frequency 41, dora-lead-time 42, dora-change-failure-rate 43, dora-mttr 44 |
| `ai-adoption-impact-cost-metrics` — AI Impact & Cost | 50 | `currency-dollar` | impact-cost-productivity-uplift 51, impact-cost-ai-assisted-percentage 52, impact-cost-capex-opex 53, impact-cost-spend-by-tier 54 |

