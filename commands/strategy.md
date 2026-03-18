---
description: Create a complete SEO strategy — crawls your site, grades 21 checks, analyzes competitors, and builds a content plan with 100+ post ideas and production-ready briefs. Prompts for optional DataForSEO key for precise keyword metrics.
argument-hint: <website-url>
allowed-tools: Read, Write, Bash, Agent, WebFetch, WebSearch
---

# Command: strategy

Create a complete SEO strategy for the website at $ARGUMENTS — site audit, competitive research, and content plan — then print a summary on screen and write the full report to a markdown file.

## Setup

1. Read settings from `.claude/seo.local.md` in the current project directory (if it exists). Extract:
   - `dataforseo_login` and `dataforseo_password` — if both are non-empty, operate in **enhanced mode** (use DataForSEO API). Otherwise, operate in **free mode** (SERP heuristics only).
   - `country` (default: US), `language` (default: en)
   - `industry`, `audience` — optional context to improve research
   - `stage_override` — if set, skip auto-detection and use this stage (affects cadence, not filtering)

2. **If DataForSEO credentials are NOT configured**, prompt the user before proceeding:

   Tell the user:
   > This will run in **free mode** — keyword difficulty is estimated from SERP heuristics and search volume is shown as relative demand (High/Medium/Low) rather than exact numbers. The audit section is unaffected, but the content strategy will have approximate keyword metrics.
   >
   > For precise search volume, measured keyword difficulty (0-100), and competitor traffic data, you can add a [DataForSEO](https://dataforseo.com) API key.

   Then ask:
   - **"Continue in free mode"** — proceed without API credentials
   - **"Set up DataForSEO first"** — guide the user to create `.claude/seo.local.md` with their credentials, then re-read settings and proceed in enhanced mode

   If the user chooses to set up DataForSEO, create `.claude/seo.local.md` with the template from the README and ask them to fill in `dataforseo_login` and `dataforseo_password`. After they confirm, re-read the file and proceed in enhanced mode.

3. Load the SEO strategy methodology from the seo-strategy skill. This provides the three-layer framework, scoring rubrics, and content brief templates.

## Execution

### Step 1: Run the 21-check audit

Follow the crawl & screenshot procedure in `skills/search-gap/reference/shared-procedures.md` — this includes crawling all blog posts, product pages, and scoring all 21 checks. Apply the scoring rules and grading scale from the same shared procedures file.

Save the audit results (section grades, per-check pass/fail, observations, and fixes) — you will pass these to the strategy-synthesizer agent.

### Step 2: Launch research agents in parallel

**Agent 1: site-analyzer** — launch with:
- The website URL: $ARGUMENTS
- Settings context (country, language, industry, audience)
- DataForSEO mode status
- Instructions to extract: positioning, stage, revenue model, audience, content inventory

**Agent 2: competitor-researcher** — launch with:
- The website URL: $ARGUMENTS
- Any industry context from settings
- DataForSEO credentials if available
- Country/language settings
- Instructions to find 3-5 category-aligned competitors and analyze their content strategies

### Step 3: Wait for both agents to complete.

### Step 4: Launch strategy-synthesizer

Launch the `strategy-synthesizer` agent with:
- The **audit results** from Step 1 (section grades, all 21 check results with observations)
- The complete **site analysis** output from Agent 1
- The complete **competitor research** output from Agent 2
- All settings (DataForSEO creds, country, language, stage override)
- Instructions to apply the three-layer framework and generate:
  - A comprehensive combined report (audit + competitive landscape + strategy) written to `./[company]-seo-report.md`
  - A brief summary returned to the conversation

## Output

After the strategy-synthesizer completes, display this summary on screen:

```
SEO REPORT: [Company Name]
File: [company]-seo-report.md

  Audit (21 checks):
    Technical SEO         [grade]  (X/Y)
    E-E-A-T Signals       [grade]  (X/Y)
    Content Depth         [grade]  (X/Y)
    OVERALL               [grade]  (X/Y passing)

  CRITICAL:
    - [Check ID]: [observation] → [fix]
    - [Check ID]: [observation] → [fix]

  Strategy:
    Positioning: [one-line positioning statement]
    Stage: [Seed/Growth/Scale] (context only)
    Competitors: [domain1], [domain2], [domain3]
    Pillars: [N] (5-8)
    Post Ideas: [N] (100+)
    Priority Briefs: [N] (10-15 detailed)
    Top 3 posts to write first:
      1. [title] — Rev. [score], Diff. [score]
      2. [title] — Rev. [score], Diff. [score]
      3. [title] — Rev. [score], Diff. [score]

Open [company]-seo-report.md for the full report.
```

If in free mode, add: "Add DataForSEO credentials to `.claude/seo.local.md` for precise keyword metrics."

Offer to dive deeper into any pillar, post brief, or audit finding.
