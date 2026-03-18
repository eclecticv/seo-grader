---
description: Get a complete content strategy for your startup — 100+ post ideas across 5-8 pillars, with keyword metrics and production-ready briefs you can hand to a writer. Analyzes competitors, filters by positioning, scores by revenue proximity. Prompts for optional DataForSEO key for precise metrics.
argument-hint: <website-url>
allowed-tools: Read, Write, Agent, WebFetch, WebSearch
---

Generate a comprehensive SEO content strategy for the website at $ARGUMENTS using the three-layer framework (positioning-filtered, stage-contextualized, revenue-proximity scored). The strategy produces **100+ post ideas across 5-8 pillars** with full detailed briefs for the top 10-15 priority posts.

## Setup

1. Read settings from `.claude/seo-grader.local.md` in the current project directory (if it exists). Extract:
   - `dataforseo_login` and `dataforseo_password` — if both are non-empty, operate in **enhanced mode** (use DataForSEO API). Otherwise, operate in **free mode** (SERP heuristics only).
   - `country` (default: US), `language` (default: en)
   - `industry`, `audience` — optional context to improve research
   - `stage_override` — if set, skip auto-detection and use this stage (affects cadence, not filtering)

2. **If DataForSEO credentials are NOT configured**, prompt the user before proceeding:

   Tell the user:
   > This strategy will run in **free mode** — keyword difficulty is estimated from SERP heuristics and search volume is shown as relative demand (High/Medium/Low) rather than exact numbers. Results are useful but approximate.
   >
   > For precise search volume, measured keyword difficulty (0-100), competitor traffic estimates, and search intent classification, you can add a [DataForSEO](https://dataforseo.com) API key.

   Then ask:
   - **"Continue in free mode"** — proceed without API credentials
   - **"Set up DataForSEO first"** — guide the user to create `.claude/seo-grader.local.md` with their credentials, then re-read settings and proceed in enhanced mode

   If the user chooses to set up DataForSEO, create `.claude/seo-grader.local.md` with the template from the README and ask them to fill in `dataforseo_login` and `dataforseo_password`. After they confirm, re-read the file and proceed in enhanced mode.

3. Load the SEO strategy methodology from the seo-strategy skill. This provides the three-layer framework, scoring rubrics, and content brief templates.

## Execution

Run two research agents **in parallel**:

### Agent 1: site-analyzer
Launch the `site-analyzer` agent with:
- The website URL: $ARGUMENTS
- Settings context (country, language, industry, audience)
- DataForSEO mode status
- Instructions to extract: positioning, stage, revenue model, audience, content inventory

### Agent 2: competitor-researcher
Launch the `competitor-researcher` agent with:
- The website URL: $ARGUMENTS
- Any industry context from settings
- DataForSEO credentials if available
- Country/language settings
- Instructions to find 3-5 category-aligned competitors and analyze their content strategies

### Wait for both agents to complete.

### Agent 3: strategy-synthesizer
Launch the `strategy-synthesizer` agent with:
- The complete site analysis output from Agent 1
- The complete competitor research output from Agent 2
- All settings (DataForSEO creds, country, language, stage override)
- Instructions to apply the three-layer framework and generate:
  - A full strategy report written to `./seo-strategy-report.md`
  - A brief summary returned to the conversation

## Output

After the strategy-synthesizer completes:

1. Display the brief summary it returned (positioning, stage context, pillar count, total post ideas, priority brief count, top 5 posts to publish first, key insight)
2. Tell the user where the full report was saved: `./seo-strategy-report.md`
3. If in free mode, mention they can get more precise metrics by configuring DataForSEO credentials in `.claude/seo-grader.local.md`
4. Offer to dive deeper into any pillar or post brief

**Note:** The plan command writes the strategy report to file due to its size (5-8 pillars, 100+ post ideas, 10-15 detailed briefs). For a quick on-screen scorecard, use `/seo-grader:audit`. For the combined audit + strategy + competitive report, use `/seo-grader:export`.
