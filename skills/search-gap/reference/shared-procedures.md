# Shared Procedures

Common procedures used by the /seo:strategy command.

## Crawl & Screenshot Procedure

1. **Crawl the homepage** via WebFetch to extract text content and navigation links (if the page content exceeds 50KB, work with the first 50KB only)
2. **Identify the blog/resources section** — look for links to `/blog`, `/resources`, `/insights`, `/articles`, `/learn`, or similar content hubs in the navigation
3. **Crawl the blog index** via WebFetch (same 50KB limit per page). Follow pagination or archive links to discover ALL blog post URLs
4. **Crawl ALL blog posts** via WebFetch (50KB limit per page) — every single post, not a sample. For sites with 50+ posts, crawl up to 50 of the most recent. **Stop crawling if total accumulated text across all pages exceeds 200KB** — work with what you have
5. **Crawl key product/feature pages** found in the main navigation (e.g., `/features`, `/product`, `/solutions`, `/platform`) — same 50KB per-page limit and 200KB aggregate budget
6. **Screenshot the homepage** using local headless Chrome (NOT the browser MCP):
   - Find Chrome: `which google-chrome-stable 2>/dev/null || which google-chrome 2>/dev/null || which chromium 2>/dev/null || ls "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" 2>/dev/null`
   - Screenshot with 30-second timeout and memory limits (macOS-compatible):
     ```bash
     ( "/path/to/chrome" --headless=new --disable-gpu --no-sandbox --disable-extensions --disable-background-networking --disable-sync --disable-translate --disable-default-apps --js-flags="--max-old-space-size=256" --screenshot="[company]-homepage.png" --window-size=1280,900 "[url]" 2>/dev/null & CHROME_PID=$!; ( sleep 30 && kill $CHROME_PID 2>/dev/null ) & WATCHDOG=$!; wait $CHROME_PID 2>/dev/null; kill $WATCHDOG 2>/dev/null ); if [ ! -f "[company]-homepage.png" ]; then echo "Screenshot failed or timed out — proceeding with text-only analysis"; fi
     ```
   - If the screenshot file exists, read it using the Read tool to visually inspect the above-the-fold area, then delete it
   - **If the screenshot failed or timed out, skip it entirely** — do NOT retry. Proceed with text-only analysis
7. **Read all 3 reference files** to get the full checklist:
   - `skills/search-gap/reference/technical-seo.md` (TS-1 to TS-8)
   - `skills/search-gap/reference/eeat-signals.md` (EA-1 to EA-7)
   - `skills/search-gap/reference/content-depth.md` (CD-1 to CD-6)
8. **Score every single check** as PASS, FAIL, or N/A based on what you observed across ALL crawled pages

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

## Company Name Extraction

Extract the company name from the page title or domain, using the brand name only (e.g., for `https://www.acme.com`, use `acme`; for a page titled "Acme - Project Management", use `acme`).

## Notes

- **IMPORTANT: Do NOT use the browser MCP for screenshots.** Always use local headless Chrome via the Bash tool instead.
- **IMPORTANT: Use `--headless=new` and `--window-size=1280,900`** — never use heights above 900px. Larger screenshots cause excessive memory usage.
- **Memory safety:** The screenshot command has a 30-second timeout and 256MB JS heap limit. If it fails, times out, or produces no file, proceed with text-only analysis. Never retry a failed screenshot. Text analysis via WebFetch is the primary data source — the screenshot is supplementary for visual layout checks only.
- **Content budget:** Each WebFetch call is capped at 50KB. Total crawled text across all pages must not exceed 200KB — stop crawling additional pages if this budget is reached and work with what you have.
- **Crawl ALL blog posts** — the audit requires full content inventory, not just a sample. For very large sites (50+ posts), cap at the 50 most recent.
- If Chrome is not installed, proceed with text-only analysis
- If no blog section is found, note it and evaluate content checks based on available pages. This is itself a significant finding.
