---
name: search-gap
description: >
  Quick SEO health check for your website — crawls your pages, runs 21 checks
  across Technical SEO, E-E-A-T, and Content Depth, then gives you a letter-graded
  scorecard with prioritized fixes and source citations.
  Can be triggered directly via natural language OR called as part of the
  `/seo:strategy` command (which runs the audit as Step 1 before passing results
  to the strategy-synthesizer agent).
  Use when the user asks to audit website SEO,
  run an SEO audit, check SEO health, grade a website for search,
  analyze on-page SEO, find SEO issues, check E-E-A-T signals,
  review technical SEO, or mentions "21-check SEO audit", "SEO scorecard",
  "search gap analysis", "on-page SEO review", "E-E-A-T audit",
  "content depth analysis", "how does my site score for SEO",
  "what SEO problems does my site have".
version: 0.1.0
---

# Search Gap Analysis

A search discoverability and competitive gap analysis tool that audits a website's on-page SEO health, E-E-A-T trust signals, and content depth against 21 checks drawn from Google's official documentation, industry-standard SEO research, and content marketing studies. Then identifies semantic competitors from live SERP data and recommends content pillars scored on relevance, difficulty, and volume.

## Purpose

Analyze a website's full content footprint — homepage, product pages, and all blog posts — to identify search discoverability gaps, competitive blind spots, and strategic content opportunities. The output is a three-section report: on-page audit (21 checks), competitive landscape (SERP-based), and content pillar recommendations (scored on a Goldilocks balance).

## How It Works

0. **Check DataForSEO credentials** — Before anything else, read `.claude/seo-grader.local.md` to check if `dataforseo_login` and `dataforseo_password` are set. If credentials are NOT found or the file doesn't exist:
   - Tell the user that DataForSEO is optional but provides real search volume and keyword difficulty data instead of heuristic estimates
   - Ask if they have credentials they'd like to configure
   - If yes, save them to `.claude/seo-grader.local.md` in this format:
     ```yaml
     ---
     dataforseo_login: ""
     dataforseo_password: ""
     country: US
     language: en
     industry: ""
     audience: ""
     stage_override: ""
     ---
     ```
   - If no, confirm proceeding in free (heuristic) mode
   - Only after this is resolved, proceed to Step 1

   Do NOT proceed to site crawling until the credential check is complete.

1. **Discover & crawl** — WebFetch the homepage, find the blog/resources section, crawl ALL blog posts and key product pages. Note: If Bash tool is not available (e.g., when running as a standalone skill), skip headless Chrome screenshots and proceed with text-only analysis.
2. **Audit 21 checks** — evaluate every check across the crawled pages as PASS/FAIL/N/A
3. **Map the competitive landscape** — extract 5 core topics, WebSearch each, identify top 3 SERP competitors, analyze their content advantages and gaps
4. **Recommend content pillars** — synthesize audit gaps + competitive gaps into 3-5 scored content opportunities

## Dual Mode Operation

The Content Pillar Recommendations (Section 3) produce difficulty and volume metrics in two modes. The credential check in Step 0 handles mode selection.

### Enhanced Mode (DataForSEO)
When `dataforseo_login` and `dataforseo_password` are set in `.claude/seo-grader.local.md`:
- Real search volume data from Google (exact monthly numbers)
- Precise keyword difficulty scores (0-100, measured)
- Search intent classification for pillar topics

### Free Mode (Heuristic)
When no API credentials are configured:
- Keyword difficulty estimated via SERP composition heuristic (0-100 score with qualitative label)
- Search volume indicated as relative demand (High / Medium / Low) with evidence from Google Autocomplete, result count, and content freshness
- Explicit disclaimer in output about estimate precision

## The 21-Check Playbook

### 1. Technical SEO (8 checks: TS-1 to TS-8)
Schema.org structured data, meta title optimization, meta description quality, heading hierarchy, internal linking structure, image optimization, canonical tags & URL structure, Open Graph & Twitter Card metadata.
> See [reference/technical-seo.md](reference/technical-seo.md)

### 2. E-E-A-T Signals (7 checks: EA-1 to EA-7)
Author attribution, About page depth, original research & proprietary data, external citations, trust signals (privacy/terms/contact), case studies & customer proof, content freshness.
> See [reference/eeat-signals.md](reference/eeat-signals.md)

### 3. Content Depth (6 checks: CD-1 to CD-6)
Content depth per page, topic coverage breadth, FAQ & educational content, visual content quality, content architecture (pillar/cluster), funnel content balance (TOFU/MOFU/BOFU).
> See [reference/content-depth.md](reference/content-depth.md)

## Scoring

Each section receives a letter grade (A+ through F) based on the percentage of applicable items that pass. N/A items are excluded from the denominator. See `reference/shared-procedures.md` for the full grading scale, scoring rules, and crawl/screenshot procedure.

## Output Format

### Section 1: On-Page Audit
For each of the 21 checks, the report includes:
- **What it is** — description of the check (from the reference)
- **Why it matters** — the rationale (from the reference)
- **Source** — full citation
- **Compliance** — PASS, FAIL, or N/A
- **Observation** — what was specifically observed across the crawled pages
- **How to fix** — concrete, actionable recommendation (only if FAIL)

### Section 2: Competitive Landscape
For each of the top 3 semantic competitors:
- Domain & SERP presence (appeared in X/5 topic searches)
- Content advantage (what they do better)
- Content gap (what they're missing — the client's opportunity)
- E-E-A-T comparison

### Section 3: Content Pillar Recommendations
For each of 3-5 recommended pillars:
- Pillar title and description
- **Difficulty estimate**: Run the SERP heuristic from `reference/shared-procedures.md` — score 0-100 with qualitative label (Very Easy / Easy / Medium / Hard / Very Hard). Show the breakdown: domain type score + content quality score + SERP feature score + result count score = total.
- **Volume indicator**: High / Medium / Low, with evidence (e.g., "Medium — appears in Google Autocomplete, 10 organic results, results from last 12 months")
- **Relevance score**: High / Medium / Low based on positioning alignment
- Opportunity score (Goldilocks formula: high relevance + low difficulty + meaningful volume)
- 3-5 specific article topics with target intent, format, and estimated difficulty

## Sources

Checks are drawn from:
- Google Search Central documentation and Google Developers guidelines
- Google Search Quality Rater Guidelines (December 2024)
- web.dev performance and accessibility guidelines
- Moz SEO Learning Center and research
- Ahrefs research and case studies
- Backlinko content and ranking factor studies
- SEMrush SERP and content analysis research
- HubSpot content marketing research
- Content Marketing Institute benchmarks
- Open Graph Protocol specification
