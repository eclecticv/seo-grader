# Stage Detection Guide

How to classify a startup as Seed, Growth, or Scale from website signals. The site-analyzer agent uses these signals to provide context in the strategy report. Stage informs **publishing cadence and priority ordering** but never limits the number of pillars, posts, or score thresholds — the full 100+ idea topic map is always generated regardless of stage.

## Signal Categories

### 1. Content Volume
The single strongest signal. Count total indexable pages.

| Signal | Seed | Growth | Scale |
|--------|------|--------|-------|
| Total pages | < 10 | 10-50 | 50+ |
| Blog posts | < 5 or none | 5-30 | 30+ |
| Case studies | 0-1 | 2-5 | 5+ |
| Resource pages | 0 | 1-5 | 5+ |

**How to count**: Check sitemap.xml first. If no sitemap, crawl navigation + footer links. Blog archives are the most reliable count.

### 2. Product Maturity
Look at how the product is presented.

| Signal | Seed | Growth | Scale |
|--------|------|--------|-------|
| Pricing page | Missing, "contact us", or waitlist | Clear tiers, possibly free trial | Enterprise tier, custom pricing |
| Product screenshots | Few or mockups | Detailed product pages | Product tours, video demos |
| Integrations | None or few listed | Integration page with 5-20 | Marketplace with 20+ |
| API/docs | None | Basic docs | Full developer portal |
| Status/changelog | None | Basic | Detailed with versioning |

### 3. Social Proof
What trust signals are present.

| Signal | Seed | Growth | Scale |
|--------|------|--------|-------|
| Customer logos | 0-3, often unnamed | 5-15 recognizable logos | 15+, enterprise logos |
| Testimonials | 0-2, often from friends/advisors | 3-10 from customers | 10+, with titles and photos |
| Case studies | 0 | 1-5 | 5+, detailed with metrics |
| G2/Capterra badges | None | Some badges | Multiple category badges |
| Press mentions | None | Blog/podcast mentions | Major publication logos |
| Awards | None | Startup awards | Industry analyst mentions |

### 4. Team Signals
Company size indicators.

| Signal | Seed | Growth | Scale |
|--------|------|--------|-------|
| Team page | None or < 10 people | 10-50 people | 50+ or no individuals (too many) |
| Careers page | None | "We're hiring" with 1-5 roles | Full careers portal, 10+ roles |
| LinkedIn (if checked) | < 20 employees | 20-100 | 100+ |
| Office locations | 1 or remote-only | 1-2 offices | Multiple offices/global |

### 5. Funding Signals
Financial maturity indicators.

| Signal | Seed | Growth | Scale |
|--------|------|--------|-------|
| Funding mentions | None, pre-seed, seed | Series A-B mentioned | Series C+ or profitable |
| Investor logos | None or angels | VC logos on homepage | PE/growth equity logos |
| Revenue indicators | None | "Trusted by X customers" | Revenue/ARR milestones |

### 6. Domain Authority Indicators
Technical SEO maturity (observable without tools).

| Signal | Seed | Growth | Scale |
|--------|------|--------|-------|
| Backlink quality | Few, mostly directories | Industry blogs, some press | Major publications, .edu, .gov |
| Content freshness | Sporadic or stale | Monthly updates | Weekly+ publishing cadence |
| Site structure | Simple, flat | Organized sections | Complex hierarchy with hubs |
| Technical SEO | Basic or poor | Reasonable meta tags | Schema markup, optimized |

## Scoring Algorithm

Assign each signal category a stage vote (Seed=1, Growth=2, Scale=3). The final stage is the **weighted average rounded to the nearest stage**:

| Category | Weight |
|----------|--------|
| Content Volume | 3x |
| Product Maturity | 2x |
| Social Proof | 2x |
| Team Signals | 1x |
| Funding Signals | 1x |
| Domain Authority | 1x |

**Example**: A startup with Growth content volume (2), Growth product (2), Seed social proof (1), Growth team (2), Seed funding (1), Seed domain authority (1):
- Weighted sum: (2×3) + (2×2) + (1×2) + (2×1) + (1×1) + (1×1) = 6 + 4 + 2 + 2 + 1 + 1 = 16
- Total weight: 3 + 2 + 2 + 1 + 1 + 1 = 10
- Average: 16/10 = 1.6 → **Growth** (rounds to 2)

## Override Rules

1. **Settings override always wins**: If user sets `stage_override` in settings, use that.
2. **When in doubt, go one stage lower**: Stage affects cadence recommendations, not content scope.
3. **Content velocity matters**: A Growth-stage company with no content team should get Seed-stage cadence. Note this in the report.
4. **Bootstrapped companies**: May show Seed funding signals but Growth/Scale in everything else. Don't let funding alone determine stage.

## How Stage Affects the Strategy

Stage is **context, not a filter**. It determines:
- **Publishing cadence**: Seed = 1-2/month, Growth = 2-4/month, Scale = 4-8/month
- **Priority ordering**: Seed stages front-load Score 5 posts; Scale stages balance across scores
- **Cadence-to-completion estimate**: How long it takes to work through the full 100+ post backlog

Stage does NOT determine:
- Number of pillars (always 5-8)
- Number of post ideas (always 100+)
- Minimum revenue-proximity score (all scores 1-5 included)
- Funnel mix (all stages TOFU/MOFU/BOFU represented)

## Output Format

The site-analyzer should output stage classification as:

```
## Stage Classification: [SEED/GROWTH/SCALE]

**Confidence**: [High/Medium/Low]
**Key signals**:
- Content volume: [X pages, Y blog posts] → [Stage]
- Product maturity: [observations] → [Stage]
- Social proof: [observations] → [Stage]
- Team size: [estimate] → [Stage]
- Funding: [observations] → [Stage]
- Domain authority: [observations] → [Stage]

**Weighted score**: [X.X] → [Final Stage]
**Note**: [Any caveats, e.g., "Company appears Growth-stage but has minimal content team — consider Seed prescriptions"]
```
