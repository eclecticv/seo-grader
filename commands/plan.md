---
description: Generate a positioning-led SEO content strategy for a startup website
argument-hint: <website-url>
allowed-tools: Read, Write, Agent, WebFetch, WebSearch
---

Generate a comprehensive SEO content strategy for the website at $ARGUMENTS using the three-layer framework (positioning-led, stage-gated, revenue-proximity scored).

## Setup

1. Read settings from `.claude/seo-strategy.local.md` in the current project directory (if it exists). Extract:
   - `dataforseo_login` and `dataforseo_password` — if both are non-empty, operate in **enhanced mode** (use DataForSEO API). Otherwise, operate in **free mode** (SERP heuristics only).
   - `country` (default: US), `language` (default: en)
   - `industry`, `audience` — optional context to improve research
   - `difficulty_ceiling` (default: 40) — max keyword difficulty to include
   - `stage_override` — if set, skip auto-detection and use this stage

2. Load the SEO strategy methodology from the seo-strategy skill. This provides the three-layer framework, scoring rubrics, and content brief templates.

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
- All settings (DataForSEO creds, country, language, difficulty ceiling, stage override)
- Instructions to apply the three-layer framework and generate:
  - A full strategy report written to `./seo-strategy-report.md`
  - A brief summary returned to the conversation

## Output

After the strategy-synthesizer completes:

1. Display the brief summary it returned (stage, pillar count, post count, top priorities, key insight)
2. Tell the user where the full report was saved: `./seo-strategy-report.md`
3. If in free mode, mention they can get more precise metrics by configuring DataForSEO credentials in `.claude/seo-strategy.local.md`
4. Offer to dive deeper into any pillar or post brief
