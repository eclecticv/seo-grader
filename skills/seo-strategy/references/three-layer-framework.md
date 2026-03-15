# The Three-Layer Framework

A startup SEO methodology that filters keywords through positioning, stage, and revenue proximity — in that order. Each layer is a hard gate: keywords that fail any layer are discarded regardless of volume.

## Layer 1: Positioning Filter

Before touching keyword data, extract the startup's positioning:

### What to Extract
- **Category**: What market category are they in (or creating)?
- **Unique claim**: What do they do differently from incumbents?
- **ICP**: Who is the ideal customer? (Role, company size, industry)
- **Anti-positioning**: What they explicitly are NOT (e.g., "not an enterprise tool")

### The Filter Test
For every candidate keyword, ask: **"Would ranking #1 for this term reinforce our category position?"**

**Pass examples** (for a B2B sales intelligence startup):
- "sales prospecting tools for startups" — directly in category
- "how to build a prospect list without a budget" — problem they solve, for their ICP
- "ZoomInfo alternatives for small teams" — competitive positioning they claim

**Fail examples** (same startup):
- "CRM software" — adjacent category, dilutes their sales intelligence positioning
- "enterprise sales strategy" — wrong ICP (they target startups, not enterprise)
- "marketing automation tools" — different category entirely, even if their ICP searches it

### Edge Cases
- **Category-creating startups**: If the startup is defining a new category, allow keywords in adjacent categories ONLY if the content explicitly bridges to the new category. E.g., a "revenue intelligence" startup can target "sales analytics" if the content frames sales analytics as a subset of revenue intelligence.
- **Multi-product startups**: Use the primary positioning from the homepage. Don't try to serve multiple positions in one strategy.

## Layer 2: Stage Gate

### Stage Detection Signals

**Seed Stage**:
- Website has < 10 content pages
- No visible blog or < 5 blog posts
- Team page shows < 15 people (or no team page)
- No case studies or social proof
- Product appears early (beta language, waitlists, "launching soon")
- Domain likely < 2 years old
- No visible funding announcements above Series A

**Growth Stage**:
- 10-50 content pages
- Active blog with 5-30 posts
- Team page shows 15-100 people
- Some case studies, testimonials, logos
- Product is live with clear pricing
- Some domain authority signals (backlinks from industry sites)
- Series A-B funding range

**Scale Stage**:
- 50+ content pages
- Mature blog with 30+ posts and regular publishing cadence
- Team page shows 100+ people (or "careers" page with many openings)
- Extensive social proof (enterprise logos, analyst mentions)
- Multiple products or tiers
- Strong domain authority
- Series C+ or profitable

### Stage → Content Prescription

| Stage | Total Posts | Funnel Mix | Min Revenue Score | Pillar Count |
|-------|-----------|------------|-------------------|--------------|
| Seed | 10-15 | 80% bottom, 20% mid | ≥ 4 | 1-2 |
| Growth | 20-30 | 50% bottom, 30% mid, 20% top | ≥ 3 | 3-4 |
| Scale | 30-50+ | Balanced | ≥ 1 | 3-5 |

### Stage Override
Users can override auto-detection in settings with `stage_override: "seed"`, `"growth"`, or `"scale"`. Always respect the override — the user knows their situation better than the signals suggest.

## Layer 3: Revenue-Proximity Score

### Scoring Rubric (1-5)

**Score 5 — Direct Revenue Intent**
The searcher is actively comparing or buying.
- "[Your product] vs [competitor]"
- "[Product category] pricing"
- "Best [solution] for [specific ICP]"
- "[Competitor] alternative"
- "[Product] review [current year]"
- "Buy [product category]"

**Score 4 — High Intent / Problem-Aware**
The searcher has a problem your product solves and is looking for solutions.
- "How to [solve problem your product addresses]"
- "[Product category] comparison"
- "Tools for [job your product does]"
- "[Pain point] solution"
- "[Use case] software"

**Score 3 — Mid-Funnel / Solution-Aware**
The searcher is learning about the solution space.
- "What is [concept your product addresses]"
- "[Industry] best practices for [relevant area]"
- "[Process your product improves] guide"
- "How [industry leaders] do [thing]"

**Score 2 — Awareness / Problem-Unaware**
The searcher is exploring the broader topic.
- "[Broad industry trend]"
- "[Industry] statistics [year]"
- "State of [relevant market]"
- "[Role] career guide"

**Score 1 — Tangential**
Related to the industry but not in any buying journey for your product.
- "[General business advice]"
- "[Adjacent industry topic]"
- "[Thought leadership that doesn't connect to product]"

### Business Model Adjustments

**SaaS**: Score 5 heavily weights comparison and alternative keywords. Free tool / calculator content can score 4 (lead gen).

**Services/Agency**: Score 5 includes "[service] agency", "[city] [service]". Case study and portfolio keywords score 4.

**Ecommerce**: Score 5 includes product-specific and buying guide keywords. Category pages can score 4-5.

**Marketplace**: Score 5 includes both supply and demand side keywords. "[Category] near me" or "[category] marketplace" score 5.

### Applying the Minimum Score Filter
After scoring every keyword, filter by the stage minimum:
- Seed: Discard anything below score 4
- Growth: Discard anything below score 3
- Scale: Keep everything (score ≥ 1)

This ensures seed-stage startups focus exclusively on content that can drive revenue quickly, while scale-stage companies can afford awareness plays.
