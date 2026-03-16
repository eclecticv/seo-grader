# Command: export

Run the 21-check SEO audit, competitive landscape analysis, and three-layer content strategy, then produce a comprehensive markdown report.

## Usage
```
/seo-grader:export <url>
```

## What It Does

1. **Run the full audit internally** — follow all steps from the `audit` command (crawl all pages, read all 3 search-gap reference files, score all 21 checks)
2. **Run competitive landscape analysis** — extract 5 core topics, WebSearch each, identify top 3 SERP competitors, analyze their content
3. **Run the full content strategy** — follow all steps from the `plan` command (three-layer framework, pillar architecture, content briefs)
4. **Write the comprehensive combined analysis** to a single markdown file in the current directory

## Output

Write a markdown file to the current working directory named `[company-name-lowercase]-seo-export.md`.

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

**Observation:** [What you observed across the crawled pages — be specific. Name specific pages, cite evidence.]

**How to fix:** [Only if FAIL. Specific, actionable recommendation.]

---

[...repeat for every TS check...]

## 2. E-E-A-T Signals ([X/Y] — [Grade])

[...every EA check...]

## 3. Content Depth ([X/Y] — [Grade])

[...every CD check...]

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

**Content Advantage:** [What they do better — reference actual pages.]

**Content Gap:** [What they're missing — the target site's opportunity.]

**E-E-A-T Comparison:** [How their trust signals compare.]

---

[...repeat for each competitor...]

---

# Part 3: Content Strategy

[Full three-layer content strategy output: executive summary, pillar briefs, post briefs, publishing order, recommended cadence]
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
9. **Content strategy follows three-layer framework** — positioning-led, stage-gated, revenue-scored

## After Writing the File

After writing the `.md` file, output a brief terminal summary:

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
    Stage: [Seed/Growth/Scale]
    Pillars: [N]
    Post Briefs: [N]

Open [filename]-seo-export.md for the full report.
```

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- This is the most comprehensive seo-grader output — combines all three capabilities
- For a quick scorecard, use `/seo-grader:audit`
- For content strategy only, use `/seo-grader:plan`
- If Chrome is not installed, proceed with text-only analysis
