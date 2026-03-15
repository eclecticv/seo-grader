---
name: seo-strategy
description: Three-layer SEO methodology for startup content strategies. Use when the user asks to "build an SEO strategy", "create a content plan for my startup", "what content should I write to rank on Google", "analyze competitors' SEO", "generate content briefs", "plan blog content", "keyword research for my website", or mentions "SEO for startups", "content pillars", "pillar topics", "revenue-proximity scoring", "stage-gated SEO", "positioning-led SEO".
version: 0.1.0
---

# SEO Content Strategy Methodology

A three-layer framework for generating startup SEO content strategies that are positioning-aligned, stage-appropriate, and revenue-prioritized.

## The Three-Layer Framework

Every keyword recommendation passes through three sequential filters. Failure at any layer means disqualification — regardless of search volume.

### Layer 1: Positioning Filter
Extract the startup's positioning (category, unique claim, ICP) from their website. Every candidate keyword must reinforce the category position. High-volume keywords that pull the brand into generic/commodity territory are rejected.

See `references/three-layer-framework.md` for the full positioning filter methodology with pass/fail examples.

### Layer 2: Stage Gate
Detect company stage (Seed, Growth, Scale) from website signals: content volume, product maturity, social proof, team size, funding indicators. Each stage gets a prescribed content volume and funnel mix:

- **Seed**: 10-15 posts, 80% bottom-funnel, revenue score ≥ 4
- **Growth**: 20-30 posts, balanced funnel, revenue score ≥ 3
- **Scale**: 30-50+ posts, full funnel, revenue score ≥ 1

See `references/stage-detection.md` for the weighted scoring algorithm and signal tables.

### Layer 3: Revenue-Proximity Score
Every keyword receives a 1-5 score measuring distance from revenue for the specific business model. Score 5 = direct purchase intent, Score 1 = tangential awareness. Stage minimums filter low-value keywords automatically.

See `references/revenue-proximity-rubric.md` for scoring matrices by business model (SaaS, Services, Ecommerce, Marketplace).

## Execution Workflow

Generate a strategy in three sequential steps:

1. **Analyze the site** — scrape the startup's website to extract positioning, detect company stage, identify revenue model, and inventory existing content. Use the `site-analyzer` agent.
2. **Research competitors** — find 3-5 category-aligned competitors, analyze their keyword profiles and content strategies, identify gaps. Use the `competitor-researcher` agent. Run in parallel with step 1.
3. **Synthesize strategy** — apply the three-layer framework to all research, generate pillar architecture, produce validated content briefs, and write the report. Use the `strategy-synthesizer` agent.

## Dual Mode Operation

The skill operates in two modes based on whether DataForSEO credentials are configured:

### Enhanced Mode (DataForSEO)
When `dataforseo_login` and `dataforseo_password` are set in `.claude/seo-strategy.local.md`:
- Real search volume data from Google
- Precise keyword difficulty scores (0-100)
- Competitor keyword profiles with traffic estimates
- Search intent classification (informational/commercial/transactional)

See `references/dataforseo-api.md` for endpoint reference and request/response formats.

### Free Mode (Heuristic)
When no API credentials are configured:
- SERP composition analysis via WebSearch for difficulty estimation
- Google Autocomplete for keyword expansion and traffic validation
- Competitor content scraping via WebFetch
- Explicit disclaimer in output about estimate precision

See `references/difficulty-heuristics.md` for the scoring rubric and validation methods.

## Content Brief Standards

Every post brief includes:
- SEO title + meta description (optimized for CTR)
- Target keyword + secondary keywords
- Revenue-proximity score with rationale
- SERP-matched content format (analyze what formats currently rank)
- H2/H3 outline with key points
- Target word count
- Internal linking map (to/from other posts in strategy)
- CTA recommendation
- E-E-A-T signals specific to this content type and topic
- Schema markup recommendation (JSON-LD type)

See `references/content-brief-template.md` for the complete template structure.

## E-E-A-T Integration

Every brief includes tailored E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness) guidance:
- What firsthand experience to demonstrate
- What expertise signals to include
- How to establish authority for this topic
- Trust elements (methodology, disclosures, dates)

YMYL (Your Money or Your Life) topics require elevated E-E-A-T with credentialed authors and primary source citations.

See `references/eeat-guidelines.md` for format-specific E-E-A-T recommendations.

## Schema Markup

Each brief recommends schema types based on content format:
- How-To → HowTo schema
- Comparison → Article + Review (if rating)
- Listicle → Article + ItemList
- FAQ sections → FAQPage (supplement)
- All posts → BreadcrumbList (always)

See `references/schema-markup-patterns.md` for JSON-LD templates.

## Strategy Output Structure

The final report follows this hierarchy:

1. **Executive Summary** — stage, positioning, key findings, content gaps
2. **Competitive Landscape** — competitors analyzed, keyword gaps, weaknesses
3. **Pillar Briefs** (3-5) — each with pillar page brief + supporting post list
4. **Post Briefs** — organized by pillar, full brief per post
5. **Publishing Order** — prioritized by revenue-proximity (desc), difficulty (asc), volume (desc)
6. **Recommended Cadence** — stage-appropriate publishing frequency

See `examples/sample-report.md` for a complete example of this structure.

## Settings

Users configure the plugin via `.claude/seo-strategy.local.md`:

```yaml
---
dataforseo_login: ""        # Optional: enables enhanced mode
dataforseo_password: ""
country: US                 # Target market (location code)
language: en
industry: ""                # Optional: improves competitor discovery
audience: ""                # Optional: shapes content tone recommendations
difficulty_ceiling: 40      # Max keyword difficulty to include
stage_override: ""          # Override auto-detected stage
---
```

## Additional Resources

### Reference Files
- **`references/three-layer-framework.md`** — Full methodology with positioning filter, stage gate, and revenue-proximity scoring
- **`references/revenue-proximity-rubric.md`** — Detailed scoring matrices by business model type
- **`references/stage-detection.md`** — Signal tables and weighted algorithm for stage classification
- **`references/dataforseo-api.md`** — API endpoints, authentication, request/response formats
- **`references/difficulty-heuristics.md`** — Free-mode SERP-based difficulty scoring
- **`references/eeat-guidelines.md`** — E-E-A-T signals by content format
- **`references/schema-markup-patterns.md`** — JSON-LD templates per content type
- **`references/content-brief-template.md`** — Standard brief structure and report template

### Example Files
- **`examples/sample-report.md`** — Complete example strategy report
