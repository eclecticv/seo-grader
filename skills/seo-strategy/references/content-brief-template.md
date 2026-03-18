# Content Brief Template

The strategy report uses two output tiers: a **Topic Map** (lightweight entries for 100+ ideas) and **Priority Briefs** (full detailed briefs for the top 10-15 posts).

## Topic Map Entry (Tier 1 — All 100+ Ideas)

Every post idea in the strategy gets this compact format, organized by pillar:

```markdown
| # | Post Title | Target Keyword | Rev. | Funnel | Difficulty | Volume |
|---|-----------|---------------|------|--------|------------|--------|
| 1 | [SEO-optimized title] | [primary keyword] | 5 | BOFU | 18 | 1,200 |
| 2 | [SEO-optimized title] | [primary keyword] | 4 | MOFU | 25 | 800 |
| 3 | [SEO-optimized title] | [primary keyword] | 3 | TOFU | 32 | 2,400 |
```

**Column definitions:**
- **Rev.**: Revenue-proximity score (1-5)
- **Funnel**: BOFU (bottom), MOFU (mid), TOFU (top)
- **Difficulty**: Estimated keyword difficulty (0-100, or range in free mode)
- **Volume**: Monthly search volume (or "est." in free mode)

Sort within each pillar by Rev. score descending, then Difficulty ascending.

## Priority Brief Structure (Tier 2 — Top 10-15 Posts)

```markdown
### [Post Number]. [SEO Title]

**Target Keyword**: [primary keyword]
**Secondary Keywords**: [2-4 related keywords]
**Search Volume**: [monthly volume or "estimated" in free mode]
**Keyword Difficulty**: [0-100 score or estimated range in free mode]
**Revenue-Proximity Score**: [1-5] — [one-line rationale]
**Content Format**: [SERP-matched format: how-to | comparison | listicle | guide | case-study | review]
**Funnel Position**: [bottom | mid | top]

#### Meta Description
[150-160 character meta description optimized for CTR. Include target keyword naturally. End with a value proposition or call to action.]

#### Content Outline

**Target Word Count**: [X,XXX words]

1. **H2: [Section Title]**
   - [Key point to cover]
   - [Key point to cover]

2. **H2: [Section Title]**
   - H3: [Subsection]
     - [Key point]
   - H3: [Subsection]
     - [Key point]

3. **H2: [Section Title]**
   - [Key point to cover]

[Continue for all major sections...]

**H2: FAQ** (if applicable)
- [Question 1]?
- [Question 2]?
- [Question 3]?

#### Internal Links
- Link TO: [Other posts in this strategy that should link to this post]
- Link FROM: [Other posts that this post should link to]
- Pillar link: [Link back to pillar page]

#### CTA Recommendation
[What call-to-action makes sense for this content? E.g., "Free trial signup", "Book a demo", "Download template", "Subscribe to newsletter"]

#### E-E-A-T Signals
- **Experience**: [What firsthand experience to demonstrate in this post]
- **Expertise**: [What expertise to show — author credentials, depth indicators]
- **Authority**: [Citations, external references, credentials to include]
- **Trust**: [Methodology disclosure, update commitments, disclaimers if YMYL]

#### Schema Markup
- **Primary**: [Schema Type]
- **Secondary**: [Schema Type, if applicable]
- **Include**: BreadcrumbList
```

## Pillar Page Brief (Different from Post Brief)

Pillar pages are the hub content that supporting posts link back to. They're broader and longer.

```markdown
## Pillar [Number]: [Pillar Topic Title]

**Pillar Keyword**: [primary keyword for the pillar]
**Search Volume**: [monthly volume]
**Keyword Difficulty**: [score]
**Revenue-Proximity Score**: [1-5]
**Supporting Posts**: [count]

### Pillar Page Brief

**Target Word Count**: [2,500-5,000 words — longer than supporting posts]
**Content Format**: Comprehensive guide / resource hub

#### Meta Description
[150-160 characters covering the full scope of this pillar topic]

#### Content Outline
[Similar to post brief but broader — covers the pillar topic comprehensively with sections that naturally link to each supporting post]

#### Link Architecture
This pillar page should:
- Be linked from site navigation or blog homepage
- Link to ALL supporting posts under this pillar
- Receive links back from ALL supporting posts
- Target the broadest keyword in the cluster

#### Supporting Posts
[List all posts under this pillar with their target keywords]
```

## Report Header Template

The full report starts with an executive summary:

```markdown
# SEO Report: [Company Name]

**Generated**: [Date]
**Website**: [URL]
**Mode**: [Free / Enhanced (DataForSEO)]

## Executive Summary

**Positioning**: [One-line positioning statement extracted from site]
**Revenue Model**: [SaaS / Services / Ecommerce / Marketplace]
**Target Audience**: [ICP description]
**Company Stage**: [Seed / Growth / Scale] (confidence: [High/Medium/Low]) — used for cadence, not filtering

### Strategy Overview
- **Pillars**: [5-8] pillar topics
- **Total Post Ideas**: [100+] across all pillars
- **Priority Briefs**: [10-15] fully detailed
- **Estimated Difficulty Range**: [X-Y]
- **Score Distribution**: [X ideas at Score 5, Y at Score 4, Z at Score 3, etc.]
- **Funnel Distribution**: [X% BOFU, Y% MOFU, Z% TOFU]

### Key Findings
- [Finding 1 — e.g., "Strong opportunity in [topic area] with low competition"]
- [Finding 2 — e.g., "Competitors weak on [specific topic cluster]"]
- [Finding 3 — e.g., "Existing content covers [X] well but misses [Y]"]

### Content Gaps Identified
- [Gap 1]
- [Gap 2]
- [Gap 3]

---

[Pillar architecture → Topic maps per pillar → Priority briefs → Publishing roadmap]
```

## Publishing Roadmap Section

After all briefs, include the full prioritized backlog and cadence:

```markdown
## Publishing Roadmap

All 100+ post ideas ordered by: Revenue-proximity score (desc) > Keyword difficulty (asc) > Search volume (desc)

### Phase 1: Quick Wins (Score 5, Difficulty < 30) — Publish First
| Priority | Post | Pillar | Rev. Score | Difficulty | Volume |
|----------|------|--------|-----------|------------|--------|
| 1 | [Title] | [Pillar] | 5 | 12 | 1,200 |
| 2 | [Title] | [Pillar] | 5 | 18 | 800 |
| ... | ... | ... | ... | ... | ... |

### Phase 2: Authority Builders (Score 4-5, Difficulty 30-50)
| Priority | Post | Pillar | Rev. Score | Difficulty | Volume |
|----------|------|--------|-----------|------------|--------|
| ... | ... | ... | ... | ... | ... |

### Phase 3: Topical Depth (Score 3, All Difficulties)
| Priority | Post | Pillar | Rev. Score | Difficulty | Volume |
|----------|------|--------|-----------|------------|--------|
| ... | ... | ... | ... | ... | ... |

### Phase 4: Full Coverage (Score 1-2, Build Domain Authority)
| Priority | Post | Pillar | Rev. Score | Difficulty | Volume |
|----------|------|--------|-----------|------------|--------|
| ... | ... | ... | ... | ... | ... |

### Recommended Cadence
- **Seed stage**: 1-2 posts/month — Phase 1 first, expect 12+ months for full backlog
- **Growth stage**: 2-4 posts/month — Phases 1-2 in parallel
- **Scale stage**: 4-8 posts/month — All phases in parallel with dedicated content team

At [detected cadence], full strategy completion: ~[X] months
```

## Competitor Analysis Section

Include before the pillar briefs:

```markdown
## Competitive Landscape

### Competitors Analyzed
| Competitor | Domain | Shared Keywords | Estimated Traffic | Content Volume |
|-----------|--------|----------------|-------------------|----------------|
| [Name] | [domain] | [count] | [estimate] | [post count] |

### Content Gap Opportunities
Topics competitors rank for that [Company] does not:
1. [Topic/keyword] — [which competitor(s)], [volume], [difficulty]
2. [Topic/keyword] — [which competitor(s)], [volume], [difficulty]

### Competitor Content Weaknesses
Areas where competitor content is thin or outdated:
1. [Topic] — [observation]
2. [Topic] — [observation]
```
