# Insights: metric pages, playbooks and settings blocks

Insights-only patterns of the plugin's Pass C pipeline. The shared
`references/patterns.md` covers everything that applies to every help
center. Source: `GK-WP-HC-Plugin/includes/gkhc-passc.php`; if this file and
the PHP disagree, the PHP is right. The metric pipeline runs where the
product has `features.metric_pipeline` (Insights only).

| Page | Pipeline |
|---|---|
| `nav_category: metrics` + `page_type: content` | **Metric pipeline**: `gkhc_passc_restructure`, priority 16 |
| everything else | the general pipeline (shared `references/patterns.md`) |

---

## Metric pages

### Page head (before the first H3)

```markdown
<kbd>Last updated: November 2026</kbd>

## Lead Time for Changes

> _Hours from when work on a change starts to the release that delivered it to production. The other DORA velocity metric._

**Family:** DORA & Quality · **Cadence:** Per PR, aggregated for views · **Where it appears:** /insights/board-metrics, /insights/ai-impact
```

| Pattern | Becomes | Rules |
|---|---|---|
| First H2 equal to the post `title` | removed | The template's H1 replaces it. Metric pages compare against `title` only. |
| **First** blockquote on the page | `.gkhc-definition` lede, the large sentence under the title | Must be under 400 characters of text. Its text is used as-is and markup is stripped. If it contains `0–100` / `0-100`, the spec panel gets **Range: 0 – 100**. If it contains "percentage"/"percent"/"%", it gets **Range: 0 – 100%**. Range is never inferred otherwise. |
| A paragraph starting `**Family:**` | `.gkhc-spec` panel | Split on every `**Label:**`. `·` is the house separator. Any labels work. **Where it appears** is taken out of the panel and becomes the closing section *only if* the page has no `### Where it appears`. Values over 300 characters are dropped. |

### Sections (H3) and their canonical order

The page is split on H3. Each section is recognised by its heading text and
reordered into this order. An unrecognised H3 keeps its place after the
recognised section before it, and nothing is dropped.

| # | Heading (regex, case-insensitive) | Use this text | Treatment |
|---|---|---|---|
| 1 | `^at a glance$` | At a glance | The page's screenshot is moved here (see 11). Run-ins. |
| 2 | `^(formulas?\|the rubric)$` | Formula | Formula panel + instrument, then a legend, then run-ins. |
| 3 | `^how .* (calculates\|applies\|computes) it$` | How GitKraken Insights calculates it | Step rail from `**Step N — …**` paragraphs, then run-ins. |
| 4 | `^why ` | Why it matters | Run-ins. |
| 5 | `^how to read it$` | How to read it | Tier scale from the first qualifying table, then run-ins. |
| 6 | `^settings that affect it$` | Settings that affect it | Run-ins. |
| 7 | `^how to (improve\|use) ` | How to improve it / How to use it | Run-ins. |
| 8 | `^limitations` | Limitations and gotchas | Run-ins. |
| 9 | `^faq$` | FAQ | Q/A pairs. No run-ins. |
| 10 | `^related metrics$` | Related metrics | First table → `.gkhc-related-table`. |
| 11 | `^where it appears$` | Where it appears | Path-token list. Its `<figure>` becomes the hero figure under At a glance. |

Most of the 21 metric pages use exactly the "Use this text" wording. The
variants in use are "How to use …" (6 pages), "How GitKraken Insights
applies it", "Formulas" and "The rubric". Use the standard wording unless the
content calls for a variant.

### Section patterns

**Formula (first fenced code block on the page).** The first fenced block on
the page, wherever it is, is lifted into a "Formula" panel at the top of the
Formula section. Markup is stripped and whitespace kept, so align with spaces.
Put nothing fenced before it.

````markdown
### Formula

```
Lead Time (hours) = release time − work start  (clamped at 0)

  release    = the earliest non-prerelease release …
```
````

A bulleted list directly under the formula (optionally after one intro
paragraph) becomes `.gkhc-legend`, a key to the formula's terms. With no
Formula heading, the panel goes straight after At a glance.

**Instrument.** If the slug tail is in `gkhc_passc_instruments()`, an empty
`.gkhc-instrument` goes under the formula and JS draws it. Content can't turn
one on.

**Step rail (only in "How … calculates it").** Consecutive paragraphs that
start with a bold step label:

```markdown
**Step 1 — Find the delivering release.** For each merged PR, …

**Step 2 — Measure.** Lead Time is the hours between …

**Step 3.** Untitled steps work too.
```

Use an em dash. En dash and hyphen also match. Lists, tables and figures
after a step belong to that step. The rail ends at the first non-step run-in.

**Run-in labels** (every section except FAQ and Related metrics, and on
general pages too). A paragraph that opens with a bold label of 2–80
characters ending in `.` or `:` *inside* the bold:

```markdown
**Release detection required.** If a repo has no release events, …
```

**Tier scale (only in "How to read it").** The first table whose body has
3–6 rows, where every row's first cell is entirely bold:

```markdown
| Band | Pattern |
| --- | --- |
| **Elite** | Less than 1 day |
| **High** | 1 day to 1 week |
| **Medium** | 1 week to 1 month |
| **Low** | More than 1 month |
```

- **Colour.** If every row names a product tier (Power User, Regular,
  Explorer, Emerging), each row gets that tier's colour. If the first row
  starts with a top word (power user, elite, strong, high, deep, lean,
  excellent), rows use the quality ramp teal → indigo → amber → rose → deep
  rose. Otherwise rows use a neutral indigo ramp. Rows mentioning PTO, empty
  state, n/a or not applicable are listed but not drawn.
- **Proportional widths.** Bands are drawn proportional to their range when
  every range parses, the bands don't overlap and they're within 20× of each
  other. Ranges come from the bold cell if it's numeric (`**0–25**`,
  `**≥ 75**`), otherwise from the second cell. Units h/d/w/mo and "less than /
  more than / to" are understood.
- **Not a scale.** For a table that isn't a scale, don't bold the whole first
  cell.

**FAQ.** The question bold with `Q:` inside the bold, and the answer on the
**next line** (no blank line) starting `A:`:

```markdown
**Q: Is Lead Time the same as issue-open to deploy?**
A: Not by default. …
```

A blank line between the Q and A lines breaks the pair.

**Related metrics.** A table with the metric links in the first column:
`| [Cycle Time](/gk-insights/ai-adoption-flow-cycle-time) | The work-start-to-merge portion. |`.

**Where it appears.** Bullets whose bold lead is a product path:

```markdown
* **/insights/board-metrics** — the Change Lead Time tile and chart. …
* **/insights/ai-impact** — implicit in the Cycle Time breakdown …
```

The path becomes a monospace token. Write the em dash with spaces. A
`<figure>` in this section moves up to be the hero under At a glance, with
its path, alt text and caption unchanged. A metric page has one figure.

**Not done on metric pages:** blockquote callouts, labelled code panels,
checklists, link-table detection. Avoid a second blockquote or code block on
a metric page. They render plain.

---

## General-pipeline patterns only Insights pages use

| Pattern (Markdown) | Becomes | Applies to |
|---|---|---|
| `### Step N — Title (3 min)`, `### Month N — Title`, `Week N`, `Phase N` | headed step rail with time badge; non-Step units get a kicker label | **playbooks** `content` only |
| `### Pattern: …`, `### If …`, `### When …` | `.gkhc-branch` (alternatives, not a sequence) | **playbooks** `content` only |
| Setting block (below) | `.gkhc-spec--mini` panel | slug ending `-settings` only |
| `→ Full section: [link](…)` (also `See also:` / `See:`) | `.gkhc-fullsection` link row | slug ending `-settings` only |

### Settings blocks (`ai-adoption-settings.md`)

```markdown
### Maturity Factor

Labeled **"Company AI Readiness (%)"** in the General tab. _In Settings UI: yes._

|  |  |
| --- | --- |
| **Default** | 100% (a factor of 1.00) |
| **Range** | 1 – 100% |
| **Type** | Whole-number percentage |
```

The table **must have an empty header row** (`|  |  |`) and bold first
cells. The `_In Settings UI: yes|no._` sentence in the paragraph before it
becomes a panel field. A table with real headers stays a table.

### Playbook steps

```markdown
## What to do — the 6-month rollout playbook

### Month 1 — Set the baseline

…

### Month 2 — Activate the pilot (2 weeks)
```

Consecutive matching H3s form one rail. Any other H2 or H3 closes it. The
parenthetical at the end becomes the time badge.

---
