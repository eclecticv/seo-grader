---
description: Get the full picture in one file — site audit, competitive landscape, and prioritized content strategy with keyword metrics and production-ready briefs, all written to a markdown report. Prompts for optional DataForSEO key for precise metrics.
argument-hint: <website-url>
allowed-tools: Read, Write, Bash, Agent, WebFetch, WebSearch
---

# Command: export

Run the 21-check SEO audit, competitive landscape analysis, and three-layer content strategy, then produce a comprehensive markdown report.

## Usage
```
/seo-grader:export <url>
```

## Setup

1. Read settings from `.claude/seo-grader.local.md` in the current project directory (if it exists). Extract:
   - `dataforseo_login` and `dataforseo_password` — if both are non-empty, operate in **enhanced mode**. Otherwise, operate in **free mode**.
   - `country` (default: US), `language` (default: en)
   - `industry`, `audience`, `stage_override`

2. **If DataForSEO credentials are NOT configured**, prompt the user before proceeding:

   Tell the user:
   > This export will run in **free mode** — keyword difficulty is estimated from SERP heuristics and search volume is shown as relative demand (High/Medium/Low) rather than exact numbers. The audit section is unaffected, but the content strategy section will have approximate keyword metrics.
   >
   > For precise search volume, measured keyword difficulty (0-100), and competitor traffic data, you can add a [DataForSEO](https://dataforseo.com) API key.

   Then ask:
   - **"Continue in free mode"** — proceed without API credentials
   - **"Set up DataForSEO first"** — guide the user to create `.claude/seo-grader.local.md` with their credentials, then re-read settings and proceed in enhanced mode

## What It Does

1. **Follow the crawl & screenshot procedure** in `skills/search-gap/reference/shared-procedures.md` — this includes crawling all pages and scoring all 21 checks
2. **Run competitive landscape analysis** — extract 5 core topics, WebSearch each, identify top 3 SERP competitors, analyze their content
3. **Run the full content strategy** — follow all steps from the `plan` command (three-layer framework, 5-8 pillars, 100+ post ideas, 10-15 priority briefs)
4. **Write the comprehensive combined analysis** to a single markdown file in the current directory

## Output

Write a markdown file to the current working directory named `[company]-seo-export.md` (see shared-procedures.md for company name extraction).

The file must follow this EXACT structure:

```markdown
# SEO Report: [Company Name]

**URL:** [url]
**Date:** [date]
**Pages Crawled:** [number] (homepage, [X] blog posts, [Y] product pages)
**Audit Score:** [total pass]/[total applicable] ([overall grade])

---

## Summary

| Section | Score | Grade |
|---------|-------|-------|
| Technical SEO | X/Y | [grade] |
| E-E-A-T Signals | X/Y | [grade] |
| Content Depth | X/Y | [grade] |

---

# Part 1: SEO Audit (21 Checks)

## 1. Technical SEO ([X/Y] — [Grade])

### TS-1: Schema.org Structured Data (JSON-LD)

**What it is:** [Copy from reference file — word for word]

**Why it matters:** [Copy from reference file — word for word]

**Source:** [Copy from reference file — word for word]

**Compliance:** PASS | FAIL | N/A

**Observation:** [What you observed across the crawled pages — be specific.]

**How to fix:** [Only if FAIL. Specific, actionable recommendation.]

---

[...repeat for every check in all 3 sections...]

---

# Part 2: Competitive Landscape

## Core Topics Searched
1. [Topic 1]
2. [Topic 2]
3. [Topic 3]
4. [Topic 4]
5. [Topic 5]

## Competitor 1: [Domain]

**SERP Presence:** Appeared in [X]/5 topic searches
**Content Advantage:** [What they do better.]
**Content Gap:** [What they're missing.]
**E-E-A-T Comparison:** [How their trust signals compare.]

---

[...repeat for each competitor...]

---

# Part 3: Content Strategy

## Executive Summary
[Positioning, stage context, key findings]

## Pillar Architecture (5-8 Pillars)

### Pillar 1: [Topic]
[Pillar page brief]

#### Topic Map (12-20 ideas)
| # | Post Title | Target Keyword | Rev. | Funnel | Diff. | Volume |
|---|-----------|---------------|------|--------|-------|--------|
| 1 | ... | ... | 5 | BOFU | ... | ... |

[...repeat for all 5-8 pillars — every entry must include difficulty and volume data...]

## Priority Briefs (Top 10-15)
[Full detailed briefs for highest-priority posts, each with search volume and difficulty]

## Publishing Roadmap
[Phased publishing order for all 100+ ideas, with keyword metrics and cadence recommendation]
```

## Critical Rules for the Output

1. **Every single check gets its own section** — all 21 items, no exceptions
2. **"What it is" and "Why it matters" are copied word-for-word** from the reference files
3. **"Source" is the full citation** from the reference files
4. **"Observation" is specific** — cite specific pages, quote actual meta titles
5. **"How to fix" is actionable** — give concrete alternatives
6. **N/A checks are still listed** with explanations
7. **Section grades count only applicable items** — N/A excluded from denominator
8. **Competitor analysis is based on actual SERP data** — run WebSearches
9. **Content strategy follows three-layer framework** — positioning-filtered, stage-contextualized, revenue-scored
10. **100+ post ideas across 5-8 pillars** — no ideas filtered by stage or score threshold
11. **Top 10-15 posts get full detailed briefs** — the rest are in the topic map with scores
12. **Publishing roadmap covers all ideas** — phased by score, sorted by difficulty
13. **Every topic map entry and content brief includes search volume and difficulty** — enhanced mode: exact numbers from DataForSEO; free mode: heuristic difficulty (0-100 with label) and relative volume (High/Medium/Low with evidence). Never omit these fields.

## After Writing the File

```
EXPORT COMPLETE: [Company Name]
File: [filename]-seo-export.md

  Audit:
    Technical SEO         [grade]  (X/Y)
    E-E-A-T Signals       [grade]  (X/Y)
    Content Depth         [grade]  (X/Y)
    OVERALL               [grade]  (X/Y passing)

  Competitive Landscape:
    Top Competitors: [domain1], [domain2], [domain3]

  Content Strategy:
    Stage: [Seed/Growth/Scale] (context only)
    Pillars: [N] (5-8)
    Post Ideas: [N] (100+)
    Priority Briefs: [N] (10-15 detailed)

Open [filename]-seo-export.md for the full report.
```
