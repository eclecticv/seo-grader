# Command: audit

Analyze a website's search discoverability against 21 SEO checks and print results on screen.

## Usage
```
/seo-grader:audit <url>
```

## What It Does

### Phase 1: Discover & Crawl Pages

1. **Crawl the homepage** via WebFetch to extract text content and navigation links
2. **Identify the blog/resources section** — look for links to `/blog`, `/resources`, `/insights`, `/articles`, `/learn`, or similar content hubs in the navigation
3. **Crawl the blog index** via WebFetch. Follow pagination or archive links to discover ALL blog post URLs
4. **Crawl ALL blog posts** via WebFetch — every single post, not a sample. For sites with 50+ posts, crawl up to 50 of the most recent
5. **Crawl key product/feature pages** found in the main navigation (e.g., `/features`, `/product`, `/solutions`, `/platform`)
6. **Screenshot the homepage** using local headless Chrome (NOT the browser MCP):
   - Find Chrome: `which google-chrome-stable 2>/dev/null || which google-chrome 2>/dev/null || which chromium 2>/dev/null || ls "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" 2>/dev/null`
   - Screenshot: `"/path/to/chrome" --headless --disable-gpu --no-sandbox --screenshot="[company]-homepage.png" --window-size=1280,4000 "[url]"`
   - Read the screenshot file using the Read tool to visually inspect it
   - Delete the screenshot file after inspection

### Phase 2: On-Page SEO Audit (21 Checks)

1. **Read all 3 reference files** to get the full checklist:
   - `skills/search-gap/reference/technical-seo.md` (TS-1 to TS-8)
   - `skills/search-gap/reference/eeat-signals.md` (EA-1 to EA-7)
   - `skills/search-gap/reference/content-depth.md` (CD-1 to CD-6)
2. **Score every single check** as PASS, FAIL, or N/A based on what you observed across ALL crawled pages

## Scoring Rules

- Score each applicable item as PASS or FAIL based on the criteria in the reference files
- Mark items as N/A ONLY when they genuinely don't apply (e.g., "content freshness" for a brand-new site, "pillar/cluster" for a site with fewer than 5 posts)
- N/A items are excluded from the pass rate — they don't count against the score
- Be honest and specific — cite what you actually observed across the crawled pages
- When uncertain, lean toward FAIL with a note about what you couldn't verify
- For items marked N/A, still include them in the output but note why they don't apply
- Technical checks (TS items) should cite specific pages as evidence, not just general impressions

## Grading Scale

Calculate a letter grade for each section based on pass rate:

| Grade | Pass Rate |
|-------|-----------|
| A+    | 100%      |
| A     | 90-99%    |
| A-    | 85-89%    |
| B+    | 80-84%    |
| B     | 75-79%    |
| B-    | 70-74%    |
| C+    | 65-69%    |
| C     | 60-64%    |
| C-    | 55-59%    |
| D+    | 50-54%    |
| D     | 45-49%    |
| D-    | 40-44%    |
| F     | Below 40% |

## Output

**Print results directly on screen (do NOT write to a file).**

Display the following format in the terminal:

```
AUDIT: [Company Name] — [total pass]/[total applicable] passing ([overall grade])
Pages crawled: [number] (homepage, [X] blog posts, [Y] product pages)

  Technical SEO         [grade]  (X/Y)
  E-E-A-T Signals       [grade]  (X/Y)
  Content Depth          [grade]  (X/Y)

CRITICAL:
  - [Check ID]: [observation] → [fix]
  - [Check ID]: [observation] → [fix]

WARNINGS:
  - [Check ID]: [observation] → [fix]
  - [Check ID]: [observation] → [fix]

Run /seo-grader:plan for full content strategy with competitive analysis
Run /seo-grader:export for complete detailed report
```

### Output Rules

1. **Scorecard first** — the summary table is the first thing the user sees
2. **CRITICAL section** — list the most impactful FAILs (structural SEO issues, missing E-E-A-T basics)
3. **WARNINGS section** — list remaining FAILs, one line each
4. **Keep it scannable** — each finding is one line: Check ID, what's wrong, what to do
5. **No file output** — everything goes to the terminal
6. **Be specific in observations** — cite specific pages, quote actual meta titles, describe what you found in the HTML

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- **Crawl ALL blog posts** — this command requires full content inventory, not just a sample. For very large sites (50+ posts), cap at the 50 most recent.
- If Chrome is not installed, proceed with text-only analysis
- If no blog section is found, note it and evaluate content checks based on available pages. This is itself a significant finding.
