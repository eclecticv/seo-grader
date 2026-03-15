# seo-strategy

Generate positioning-led, stage-gated SEO content strategies for startups. Every keyword recommendation is validated against your positioning, company stage, and distance from revenue.

## Install

```bash
claude /install eclecticv/seo-strategy
```

Or load for a single session:
```bash
claude --plugin-dir /path/to/seo-strategy
```

## Commands

| Command | Usage | What it does |
|---------|-------|-------------|
| **plan** | `/seo-strategy:plan <url>` | Full content strategy with pillar topics, post briefs, and publishing order |

## The Three-Layer Framework

1. **Positioning Filter** — Extracts your market position from your website. Rejects keywords that dilute your category story, even if they have high volume.

2. **Stage Gate** — Detects whether you're Seed, Growth, or Scale. Prescribes stage-appropriate content volume and funnel mix. Seed gets 10-15 bottom-funnel posts, not 50 awareness articles.

3. **Revenue-Proximity Score** — Every keyword scored 1-5 by distance from revenue for your business model. Bottom-funnel comparison posts rank above thought leadership. Stage minimums auto-filter low-value keywords.

## How It Works

```
/seo-strategy:plan https://example.com
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

## What You Get

- **Executive Summary** — detected stage, positioning, key findings
- **Competitive Landscape** — 3-5 competitors analyzed with content gaps
- **Pillar Topics** (3-5) with pillar page briefs
- **Post Briefs** (10-50 depending on stage), each with:
  - SEO title + meta description
  - Target keyword + secondary keywords
  - Revenue-proximity score with rationale
  - SERP-matched content format
  - H2/H3 outline with key points
  - Word count target, internal linking map, CTA
  - E-E-A-T guidance + schema markup
- **Publishing Order** — prioritized by revenue-proximity, then difficulty
- **Recommended Cadence** — stage-appropriate frequency

## Modes

### Free (no API keys)

Works out of the box. Difficulty and volume estimated via SERP heuristics. Useful but approximate.

### Enhanced (DataForSEO)

Bring your own [DataForSEO](https://dataforseo.com) credentials for real search volume, difficulty scores, and competitor keyword profiles.

Create `.claude/seo-strategy.local.md` in your project:

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

## Settings

| Setting | Default | Description |
|---------|---------|-------------|
| `dataforseo_login` | — | Enables enhanced mode |
| `dataforseo_password` | — | DataForSEO API password |
| `country` | US | Target market |
| `language` | en | Target language |
| `industry` | — | Improves competitor discovery |
| `audience` | — | Shapes content tone |
| `difficulty_ceiling` | 40 | Max keyword difficulty to include |
| `stage_override` | — | Override auto-detected stage |

## Cost Note

The strategy-synthesizer uses Claude Opus for reasoning. Research agents use Sonnet. A typical run processes 10-20 web pages. Enhanced mode adds DataForSEO API costs (~$0.50-2.00 per run).

## Requirements

- Claude Code CLI
- WebFetch + WebSearch (built-in)
- DataForSEO account (optional, for enhanced mode)

## License

MIT
