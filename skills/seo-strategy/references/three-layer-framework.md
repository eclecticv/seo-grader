# The Three-Layer Framework

A startup SEO methodology that generates comprehensive topic maps by filtering keywords through positioning, enriching with stage context, and scoring by revenue proximity. The framework produces **100+ post ideas across 5-8 pillars** — nothing is filtered out by stage or score. Every idea is scored and ranked so the user can prioritize, but the full landscape is always visible.

## Layer 1: Positioning Filter (Hard Gate)

The only hard filter. Before touching keyword data, extract the startup's positioning:

### What to Extract
- **Category**: What market category are they in (or creating)?
- **Unique claim**: What do they do differently from incumbents?
- **ICP**: Who is the ideal customer? (Role, company size, industry)
- **Anti-positioning**: What they explicitly are NOT (e.g., "not an enterprise tool")
- **Service lines / product areas**: What distinct offerings does the business have? Each is a potential pillar.

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
- **Multi-product / multi-service businesses**: Map each distinct service line or product area as a potential pillar. A GTM consultancy offering positioning, fractional leadership, and AI-powered sprints gets a pillar for each.

## Layer 2: Stage Context (Informational — Not a Filter)

Detect the company's stage to provide context in the report. Stage informs **recommended publishing order and cadence** but does NOT limit the number of pillars, posts, or score thresholds.

### Stage Detection
Use the signals in `references/stage-detection.md` to classify as Seed, Growth, or Scale.

### How Stage Is Used
- **Report metadata**: Stage is reported in the executive summary for context.
- **Publishing cadence**: Seed companies get a longer timeline; Scale companies get an aggressive one.
- **Priority sorting**: The recommended publishing order front-loads high-revenue-proximity posts for Seed/Growth stages, while Scale companies get a balanced rollout.
- **NOT used to limit**: Stage never caps pillar count, post count, or filters out posts by score.

### Stage Override
Users can override auto-detection in settings with `stage_override: "seed"`, `"growth"`, or `"scale"`. Always respect the override.

## Layer 3: Revenue-Proximity Score (Annotation — Not a Filter)

Every keyword receives a 1-5 score measuring distance from revenue for the specific business model. **All scores are included in the output.** The score is used to sort and prioritize, never to exclude.

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

## Pillar Generation

### Target: 5-8 Pillars, 100+ Post Ideas

Generate pillars by mapping the full topic landscape around the business:

1. **Service/product pillars**: One pillar per distinct service line or product area.
2. **ICP problem pillars**: One pillar per major problem category the ICP faces.
3. **Industry/vertical pillars**: If the business serves multiple verticals, each can be a pillar.
4. **Methodology/thought-leadership pillar**: The business's unique approach or framework.
5. **Competitive landscape pillar**: Comparisons, alternatives, reviews.

### Post Ideas Per Pillar
Generate **12-20 post ideas per pillar** to hit 100+ total. For each pillar, systematically cover:
- Score 5: Comparisons, alternatives, pricing, hiring/buying guides
- Score 4: How-to's, solution guides, tool roundups, case studies
- Score 3: Explainers, best practices, frameworks, benchmarks
- Score 2: Industry trends, statistics, state-of-the-market
- Score 1: Thought leadership, adjacent topics, career content

### Post Idea Format (Lightweight)
Each of the 100+ post ideas uses the compact topic map format (see `references/content-brief-template.md`). Full detailed briefs are generated only for the top 10-15 priority posts.

## Output Requirements

1. **No ideas are filtered out by stage or score.** Every positioning-aligned idea is included.
2. **Every idea is scored.** Revenue-proximity 1-5 on every entry.
3. **Ideas are organized by pillar**, then sorted by revenue-proximity score (desc) within each pillar.
4. **Full briefs for top 10-15 posts.** The highest-priority items get the complete treatment.
5. **Publishing roadmap** respects stage for cadence but shows the full 100+ item backlog.
