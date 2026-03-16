# Keyword Difficulty Heuristics (Free Mode)

When DataForSEO credentials are not configured, use these heuristics to estimate keyword difficulty from SERP analysis via WebSearch.

## The SERP Composition Method

Search for the target keyword and analyze the first page of results. Difficulty is estimated by who ranks and how they rank.

## Scoring Rubric (0-100 Estimated Difficulty)

### Domain Type Analysis (40 points max)

Look at the domains ranking on page 1. Score based on the strongest presence:

| SERP Composition | Points | Interpretation |
|-----------------|--------|----------------|
| 7+ results from major brands (Forbes, HubSpot, Wikipedia, Amazon, etc.) | 35-40 | Very hard — dominated by authority domains |
| 4-6 major brands + some niche sites | 25-34 | Hard — brand-heavy but cracks exist |
| 2-3 major brands + several niche/medium sites | 15-24 | Medium — mixed competition |
| Mostly niche sites, blogs, forums | 5-14 | Easy — indie-friendly SERP |
| Reddit, Quora, forums dominating | 0-4 | Very easy — low-quality results indicate opportunity |

**Major brand indicators**: Domains you'd recognize without context. Fortune 500 companies, top publications (NYT, Forbes, Bloomberg), dominant SaaS brands (HubSpot, Salesforce, Shopify), Wikipedia, government sites (.gov), university sites (.edu).

### Content Quality Analysis (30 points max)

Evaluate the quality of content currently ranking:

| Quality Signal | Points | How to Assess |
|---------------|--------|---------------|
| Long-form, comprehensive guides (3000+ words) | 25-30 | Check if results appear thorough from titles/snippets |
| Well-structured content with clear intent match | 15-24 | Titles directly match search intent |
| Thin content, outdated, or poor intent match | 5-14 | Titles seem tangential or generic |
| Very thin, no direct matches, or auto-generated | 0-4 | SERP doesn't serve the intent well |

### SERP Feature Analysis (20 points max)

| Feature Present | Points | Meaning |
|----------------|--------|---------|
| Featured snippet | +5 | Google found a clear answer — hard to displace but snippet opportunity exists |
| People Also Ask (3+ questions) | +3 | Well-understood topic with established content |
| Knowledge panel | +5 | Google considers this well-known entity/topic |
| Video carousel | +2 | Mixed media competition |
| Top stories / news | +3 | Current event topic — high competition, ephemeral |
| Local pack | +2 | Local intent — different competition dynamics |
| No rich features | +0 | Less competitive topic |

### Result Count Indicator (10 points max)

Use the approximate result count reported by the search engine:

| Result Count | Points |
|-------------|--------|
| 1B+ results | 8-10 |
| 100M-1B | 5-7 |
| 10M-100M | 3-4 |
| 1M-10M | 1-2 |
| < 1M results | 0 |

**Note**: Result counts are notoriously imprecise. Use as a tiebreaker only.

## Total Score Interpretation

| Score Range | Difficulty Label | Can a Seed Startup Rank? |
|------------|-----------------|--------------------------|
| 0-20 | Very Easy | Yes, within 1-3 months |
| 21-35 | Easy | Yes, within 3-6 months |
| 36-50 | Medium | Possible with strong content, 6-12 months |
| 51-70 | Hard | Unlikely without significant authority |
| 71-100 | Very Hard | Not recommended for startups |

## Applying the Difficulty Ceiling

Compare estimated difficulty against the `difficulty_ceiling` setting (default: 40).

- Score ≤ ceiling → **Include** keyword in strategy
- Score > ceiling → **Exclude** keyword (note as "aspirational" if score 4-5 on revenue proximity)

## Traffic Existence Validation

In free mode, validate that a keyword has existing organic traffic by checking:

1. **Google Autocomplete**: Does the keyword appear in Google's autocomplete suggestions? If yes, it has meaningful search volume.
2. **SERP results exist**: Does page 1 have 10 organic results? Fewer results may indicate very low volume.
3. **Date freshness**: Are results from the last 12 months? Stale results can indicate declining interest.
4. **Related searches**: Does Google show "Related searches" for this term? If yes, it's an established query pattern.

A keyword must pass at least 2 of these 4 checks to be considered as having "existing organic traffic."

## Limitations of Free Mode

Be transparent in the report:
- Search volume is unknown — cannot differentiate between 100 and 100,000 monthly searches
- Difficulty is estimated, not measured — could be off by 15-20 points
- Competitor keyword profiles are inferred from content, not measured from rank data
- Recommend upgrading to enhanced mode (DataForSEO) for precise metrics

Always include this disclaimer in free-mode reports:
> **Note**: This strategy was generated in free mode using SERP heuristics. Search volume and difficulty estimates are approximate. For precise keyword metrics, configure DataForSEO credentials in `.claude/seo-grader.local.md`.
