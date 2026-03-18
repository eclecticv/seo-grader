---
description: Run the full SEO audit, competitive landscape analysis, and content strategy, then write a comprehensive markdown report to file
argument-hint: <website-url>
allowed-tools: Read, Write, Bash, Agent, WebFetch, WebSearch
---

# Command: export

Run the 21-check SEO audit, competitive landscape analysis, and three-layer content strategy, then produce a comprehensive markdown report.

## Usage
```
/seo-grader:export <url>
```

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

[...repeat for all 5-8 pillars...]

## Priority Briefs (Top 10-15)
[Full detailed briefs for highest-priority posts]

## Publishing Roadmap
[Phased publishing order for all 100+ ideas, with cadence recommendation]
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
