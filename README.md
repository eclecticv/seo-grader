# seo-grader

**A complete SEO strategy in a box for busy founders.** Point it at your website, get back a prioritized content plan — 100+ post ideas across 5-8 pillars, with production-ready briefs you can hand directly to a writer. No SEO expertise required.

The plugin crawls your site, analyzes your competitors, and generates a full content strategy — audit, keyword research, pillar architecture, topic map, and detailed briefs with search volume and difficulty data. It runs in Claude Code with three commands and works out of the box. Add a [DataForSEO](https://dataforseo.com) key and it upgrades to precise keyword metrics.

## Install

```bash
claude /install seo-grader@andorlabs
```

Or load for a single session:
```bash
claude --plugin-dir /path/to/seo-grader
```

## Why This Exists

Most SEO tools dump a spreadsheet of keywords sorted by volume and leave you to figure out the rest. That's useless for a founder who needs to know: *what should I write first, and why?*

This plugin answers that question using a **three-layer framework**:

1. **Positioning Filter** (hard gate) — Extracts your market position from your website. Rejects keywords that pull your brand into generic/commodity territory, even if they have high volume. A CRM for solo founders shouldn't write about enterprise pipeline management.

2. **Stage Context** (informational) — Auto-detects whether you're Seed, Growth, or Scale from website signals. Informs publishing cadence and priority order — but never limits how many ideas you get. You always get the full 100+ topic map.

3. **Revenue-Proximity Score** (annotation) — Every keyword scored 1-5 by distance from revenue for your specific business model (SaaS, Services, Ecommerce, Marketplace). All scores included — used to sort and prioritize, never to filter. The first posts you publish are the ones closest to money.

## Commands

| Command | What it does |
|---------|-------------|
| `/seo-grader:audit <url>` | Find out what's hurting your search rankings — 21 checks with letter grades and prioritized fixes |
| `/seo-grader:plan <url>` | Get a complete content strategy — 5-8 pillars, 100+ post ideas, 10-15 priority briefs with keyword metrics |
| `/seo-grader:export <url>` | Get the full picture in one file — audit + competitive landscape + full strategy report |

## How It Works

### Audit: 21 Checks Across 3 Categories

| Category | Checks | Sources |
|----------|--------|---------|
| Technical SEO | 8 | Google Search Central, web.dev, Moz |
| E-E-A-T Signals | 7 | Google Quality Rater Guidelines, Ahrefs |
| Content Depth | 6 | HubSpot, Backlinko, Content Marketing Institute |

Every check includes the exact source citation, what was observed on your site, and a specific fix if it fails.

### Plan: Parallel Agent Architecture

The strategy command runs three specialized agents:

```
/seo-grader:plan https://yoursite.com
        |
        |--- site-analyzer (parallel)
        |    Crawls your site → extracts positioning, detects stage,
        |    identifies revenue model, inventories existing content
        |
        |--- competitor-researcher (parallel)
        |    Finds 3-5 category competitors → analyzes their keyword profiles,
        |    content strategies, and weaknesses you can exploit
        |
        '--- strategy-synthesizer (sequential, receives both outputs)
             Applies three-layer framework → generates 5-8 pillars with 100+
             post ideas → writes priority briefs and publishing roadmap
```

### Two-Tier Output: Topic Map + Priority Briefs

**Tier 1 — Topic Map (100+ ideas):** Every post idea scored and organized by pillar — title, keyword, revenue score, funnel position, difficulty, volume. This is your full content backlog.

**Tier 2 — Priority Briefs (top 10-15):** The highest-impact posts get the full treatment — everything a writer needs to start immediately:

- **SEO title + meta description** — optimized for CTR, within character limits
- **Target keyword + secondaries** — with search volume and difficulty data
- **Revenue-proximity score** — 1-5 with a rationale specific to your business
- **SERP-matched format** — analyzes what currently ranks and recommends the winning format
- **Full outline** — H2/H3 structure with key points per section
- **Word count target** — based on competing content length
- **Internal linking map** — which posts to link to/from, pillar connections
- **CTA recommendation** — appropriate for funnel position
- **E-E-A-T guidance** — what experience, expertise, and trust signals to include
- **Schema markup** — recommended JSON-LD types for the content format

## Keyword Metrics: Free and Enhanced Modes

### Free Mode (no API keys needed)

Works out of the box. The plugin estimates keyword difficulty using a SERP composition heuristic (who ranks, content quality, SERP features, result count) and validates search demand via Google Autocomplete and result analysis. Difficulty is scored 0-100 with a qualitative label (Very Easy → Very Hard). Volume is indicated as relative demand (High/Medium/Low) since precise numbers require API access.

Free-mode reports include a disclaimer about estimate precision.

### Enhanced Mode (DataForSEO)

Add your [DataForSEO](https://dataforseo.com) credentials for precise metrics:

- **Real search volume** — exact monthly search numbers from Google
- **Keyword difficulty scores** — measured 0-100, not estimated
- **Competitor keyword profiles** — see what your competitors rank for, with traffic estimates
- **Search intent classification** — informational / commercial / transactional
- **12-month trend data** — spot rising and declining keywords

The plugin will prompt you to set up DataForSEO when running in free mode. To configure in advance, create `.claude/seo-grader.local.md` in your project:

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

## Example Output

### Audit scorecard
```
AUDIT: AcmeCRM — 14/19 passing (B+)
Pages crawled: 8 (homepage, 5 blog posts, 2 product pages)

  Technical SEO         A   (7/8)
  E-E-A-T Signals       B   (5/6)
  Content Depth          C+  (2/5)

CRITICAL:
  - CD-5: No pillar/cluster architecture → Group posts into 2-3 pillars with hub pages
  - EA-4: Zero external citations in blog posts → Add 2-3 authoritative sources per post

WARNINGS:
  - TS-1: Missing JSON-LD on blog posts → Add Article schema to all posts
  - CD-6: 100% top-funnel content → Add comparison and how-to posts (bottom/mid-funnel)
```

### Strategy topic map (excerpt)
```
Pillar 1: Simple CRM for Small Teams — 18 post ideas

| # | Post Title                            | Rev. | Funnel | Diff. | Volume |
|---|---------------------------------------|------|--------|-------|--------|
| 1 | AcmeCRM vs Folk CRM                   |   5  | BOFU   |     8 | 320/mo |
| 2 | CRM for Freelancers                   |   5  | BOFU   |    12 | 720/mo |
| 3 | Spreadsheet vs CRM: When to Switch    |   4  | MOFU   |    18 | 1,100  |
| 4 | What Does a CRM Actually Do?          |   3  | TOFU   |    42 | 3,200  |
| …                                                                          |
```

### Priority brief (excerpt)
```
### AcmeCRM vs Folk CRM: Which Is Better for Solo Founders?

Target Keyword: acmecrm vs folk crm
Search Volume: 320/mo | Difficulty: 8 (Very Easy) | Revenue Score: 5/5
Format: Comparison | Funnel: Bottom | Word Count: 2,000

Why this scores 5/5: Direct competitor comparison — searcher is actively
evaluating CRM options and is in buying mode.

Outline:
  H2: Quick Comparison Table
  H2: Who Each CRM Is Built For
  H2: Feature Comparison (Contact, Pipeline, Integrations, Mobile)
  H2: Pricing Breakdown
  H2: The Verdict — Choose Folk if... / Choose Acme if...
  H2: FAQ
```

## Requirements

- Claude Code CLI
- WebFetch + WebSearch (built-in)
- DataForSEO account (optional — the plugin prompts you to set this up for better accuracy)

## License

MIT
