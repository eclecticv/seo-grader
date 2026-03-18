# seo-grader

Audit website SEO health against 21 checks and generate comprehensive content strategies for startups. Every check cites its source. Three-layer framework generates **100+ post ideas across 5-8 pillars** — positioning-filtered, stage-contextualized, and revenue-scored.

## Install

```bash
claude /install seo-grader@andorlabs
```

Or load for a single session:
```bash
claude --plugin-dir /path/to/seo-grader
```

## Commands

| Command | Usage | What it does |
|---------|-------|-------------|
| **audit** | `/seo-grader:audit <url>` | Run 21 SEO checks, print scorecard + findings on screen |
| **plan** | `/seo-grader:plan <url>` | Full content strategy: 5-8 pillars, 100+ post ideas, 10-15 priority briefs (writes to file) |
| **export** | `/seo-grader:export <url>` | Complete report: audit + competitive landscape + full strategy to file |

## What It Checks

### SEO Audit (21 checks)

| Category | Checks | Source |
|----------|--------|--------|
| Technical SEO | 8 | Google Search Central, web.dev, Moz |
| E-E-A-T Signals | 7 | Google Quality Rater Guidelines, Ahrefs |
| Content Depth | 6 | HubSpot, Backlinko, Content Marketing Institute |

### Content Strategy (Three-Layer Framework)

1. **Positioning Filter** (hard gate) — Extracts your market position from your website. Rejects keywords that dilute your category story, even if they have high volume.

2. **Stage Context** (informational) — Detects whether you're Seed, Growth, or Scale. Informs publishing cadence and priority order. Never limits pillar count, post count, or score thresholds.

3. **Revenue-Proximity Score** (annotation) — Every keyword scored 1-5 by distance from revenue for your business model. All scores included — used to sort and prioritize, never to filter.

## How the Plan Command Works

```
/seo-grader:plan https://example.com
        |
        |--- site-analyzer (parallel)
        |    Scrapes website -> positioning, stage, audience, content inventory
        |
        |--- competitor-researcher (parallel)
        |    Finds competitors -> keyword profiles, content gaps, weaknesses
        |
        '--- strategy-synthesizer (sequential, receives both outputs)
             Applies three-layer framework -> pillar strategy -> content briefs
             Writes report to ./seo-strategy-report.md
```

## Modes

### Free (no API keys)

Works out of the box. Difficulty and volume estimated via SERP heuristics. Useful but approximate.

### Enhanced (DataForSEO)

Bring your own [DataForSEO](https://dataforseo.com) credentials for real search volume, difficulty scores, and competitor keyword profiles.

Create `.claude/seo-grader.local.md` in your project:

```yaml
---
dataforseo_login: "your-login@email.com"
dataforseo_password: "your-api-password"
country: US
language: en
industry: "B2B SaaS"
audience: "technical founders"
---
```

## Output Format

### Audit checks produce:
- **What it is** — from the reference (word for word)
- **Why it matters** — the rationale
- **Source** — full citation
- **Compliance** — PASS / FAIL / N/A
- **Observation** — what was found on the site
- **How to fix** — actionable recommendation (FAIL only)

### Content strategy produces:
- **Topic map**: 100+ post ideas across 5-8 pillars, each scored 1-5
- **Priority briefs** (top 10-15): SEO title, meta description, target keyword, revenue-proximity score, SERP-matched format, H2/H3 outline, word count, internal linking, CTA, E-E-A-T guidance, schema markup
- **Publishing roadmap**: Phased by score, sorted by difficulty

## Requirements

- Claude Code CLI
- WebFetch + WebSearch (built-in)
- Chrome (optional, for screenshots)
- DataForSEO account (optional, for enhanced mode)

## License

MIT
