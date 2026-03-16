---
description: Run a 21-check SEO audit against a website and display a scorecard with grades for Technical SEO, E-E-A-T, and Content Depth
argument-hint: <website-url>
allowed-tools: Read, Bash, WebFetch, WebSearch
---

# Command: audit

Analyze a website's search discoverability against 21 SEO checks and print results on screen.

## Usage
```
/seo-grader:audit <url>
```

## What It Does

1. **Follow the crawl & screenshot procedure** in `skills/search-gap/reference/shared-procedures.md` — this includes crawling all blog posts, product pages, and scoring all 21 checks
2. **Apply the scoring rules and grading scale** from the same shared procedures file
3. **Print results on screen** using the format below

## Output

**Print results directly on screen (do NOT write to a file).**

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
