# seo-grader

Audit website SEO health against 21 checks and generate positioning-led content strategies for startups. Every check cites its source. Three-layer framework ensures every keyword recommendation is validated against your positioning, company stage, and distance from revenue.

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
| **plan** | `/seo-grader:plan <url>` | Full three-layer content strategy with pillar topics + post briefs (writes to file) |
| **export** | `/seo-grader:export <url>` | Write complete report (audit + competitive landscape + strategy) to file |

## What It Checks

### SEO Audit (21 checks)

| Category | Checks | Source |
|----------|--------|--------|
| Technical SEO | 8 | Google Search Central, web.dev, Moz |
| E-E-A-T Signals | 7 | Google Quality Rater Guidelines, Ahrefs |
| Content Depth | 6 | HubSpot, Backlinko, Content Marketing Institute |

### Content Strategy (Three-Layer Framework)

1. **Positioning Filter** — Extracts your market position from your website. Rejects keywords that dilute your category story, even if they have high volume.

2. **Stage Gate** — Detects whether you're Seed, Growth, or Scale. Prescribes stage-appropriate content volume and funnel mix. Seed gets 10-15 bottom-funnel posts, not 50 awareness articles.

3. **Revenue-Proximity Score** — Every keyword scored 1-5 by distance from revenue for your business model. Bottom-funnel comparison posts rank above thought leadership.

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
difficulty_ceiling: 40
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

### Content briefs produce:
- SEO title + meta description
- Target keyword + secondary keywords
- Revenue-proximity score with rationale
- SERP-matched content format
- H2/H3 outline with key points
- Word count target, internal linking map, CTA
- E-E-A-T guidance + schema markup

## Requirements

- Claude Code CLI
- WebFetch + WebSearch (built-in)
- Chrome (optional, for screenshots)
- DataForSEO account (optional, for enhanced mode)

## License

MIT
