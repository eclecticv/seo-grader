# DataForSEO API Reference

Complete reference for making DataForSEO API calls in enhanced mode. The plugin reads credentials from `.claude/seo-grader.local.md` settings.

## Authentication

**Method**: HTTP Basic Auth
**Header**: `Authorization: Basic {base64(login:password)}`

Credentials come from the settings file:
```yaml
dataforseo_login: "user@example.com"
dataforseo_password: "api-password-here"
```

The API password is auto-generated in the DataForSEO dashboard (API Access tab) and differs from the account password.

## Base URL

`https://api.dataforseo.com`

All endpoints use: `POST https://api.dataforseo.com/v3/{category}/{endpoint}`

## Location Codes

| Country | Code |
|---------|------|
| United States | 2840 |
| Canada | 2124 |
| United Kingdom | 2826 |
| Australia | 2036 |
| Germany | 2276 |
| France | 2250 |
| India | 2356 |
| Brazil | 2076 |

Full list: `GET /v3/dataforseo_labs/locations_and_languages`

## Key Endpoints

### 1. Keyword Suggestions
Find related keywords from a seed keyword.

**Path**: `POST /v3/dataforseo_labs/google/keyword_suggestions/live`

**Request**:
```json
[{
  "keyword": "sales automation",
  "location_code": 2840,
  "language_code": "en",
  "limit": 100,
  "include_seed_keyword": true,
  "filters": [
    ["keyword_info.search_volume", ">", 100]
  ]
}]
```

**Key response fields**:
- `keyword` — the suggested keyword
- `keyword_info.search_volume` — monthly search volume
- `keyword_info.competition_level` — LOW / MEDIUM / HIGH
- `keyword_info.cpc` — cost per click (indicates commercial intent)
- `keyword_properties.keyword_difficulty` — difficulty score 0-100
- `search_intent_info.main_intent` — informational / navigational / commercial / transactional
- `keyword_info.monthly_searches[]` — 12-month trend data

### 2. Bulk Keyword Difficulty
Score difficulty for up to 1,000 keywords at once.

**Path**: `POST /v3/dataforseo_labs/google/bulk_keyword_difficulty/live`

**Request**:
```json
[{
  "keywords": [
    "sales automation tools",
    "best crm for startups",
    "hubspot alternative"
  ],
  "location_code": 2840,
  "language_code": "en"
}]
```

**Key response fields**:
- `keyword` — the keyword
- `keyword_difficulty` — difficulty score 0-100

### 3. Search Volume
Precise monthly search volume for keywords.

**Path**: `POST /v3/keywords_data/google_ads/search_volume/live`

**Request**:
```json
[{
  "keywords": [
    "sales automation",
    "crm software"
  ],
  "location_code": 2840,
  "language_code": "en"
}]
```

**Key response fields**:
- `keyword` — the keyword
- `search_volume` — average monthly searches
- `competition` — competition level
- `cpc` — cost per click
- `monthly_searches[]` — 12-month trend with year/month/search_volume

### 4. SERP Analysis (Organic)
See who ranks for a keyword and what SERP features appear.

**Path**: `POST /v3/serp/google/organic/live/advanced`

**Request**:
```json
[{
  "keyword": "best crm for startups",
  "location_code": 2840,
  "language_code": "en",
  "device": "desktop",
  "depth": 20
}]
```

**Key response fields**:
- `items[].type` — "organic", "featured_snippet", "people_also_ask", "knowledge_graph"
- `items[].rank_group` — position in SERP
- `items[].domain` — ranking domain
- `items[].title` — page title
- `items[].url` — ranking URL
- `items[].description` — snippet text
- `items[].breadcrumb` — URL breadcrumb

### 5. Ranked Keywords (Domain Analysis)
Find all keywords a domain ranks for.

**Path**: `POST /v3/dataforseo_labs/google/ranked_keywords/live`

**Request**:
```json
[{
  "target": "competitor.com",
  "location_code": 2840,
  "language_code": "en",
  "limit": 100,
  "order_by": ["keyword_data.keyword_info.search_volume,desc"],
  "filters": [
    ["ranked_serp_element.serp_item.rank_group", "<=", 20]
  ]
}]
```

**Key response fields**:
- `keyword_data.keyword` — the keyword
- `keyword_data.keyword_info.search_volume` — monthly volume
- `keyword_data.keyword_info.competition_level` — competition
- `ranked_serp_element.serp_item.rank_group` — ranking position
- `ranked_serp_element.serp_item.url` — ranking URL

### 6. Competitors Domain
Find competing domains for a target domain.

**Path**: `POST /v3/dataforseo_labs/google/competitors_domain/live`

**Request**:
```json
[{
  "target": "usersite.com",
  "location_code": 2840,
  "language_code": "en",
  "limit": 10,
  "filters": [
    ["avg_position", "<=", 20]
  ]
}]
```

**Key response fields**:
- `domain` — competitor domain
- `avg_position` — average ranking position
- `sum_position` — sum of positions
- `intersections` — number of shared keywords
- `full_domain_metrics[].organic.count` — total organic keywords
- `full_domain_metrics[].organic.etv` — estimated traffic volume

## Rate Limits

- General: 2,000 requests/minute
- Max concurrent (Labs/Backlinks APIs): 30 requests
- Max tasks per request: 100

## Cost Optimization Tips

1. **Batch keywords**: Use bulk endpoints (search volume, keyword difficulty) to process up to 1,000 keywords per request instead of one-by-one.
2. **Filter server-side**: Use the `filters` parameter to reduce response size and focus on relevant results.
3. **Limit results**: Use the `limit` parameter to cap results (e.g., top 100 keywords instead of all).
4. **Keyword suggestions over SERP**: Keyword suggestions include volume and difficulty — avoid separate SERP calls when you just need metrics.
5. **SERP only for format analysis**: Use SERP endpoint specifically when you need to know what content formats are ranking (for SERP-matched format recommendations).

## Error Handling

| Status Code | Meaning |
|-------------|---------|
| 20000 | Success |
| 20100 | Task created (batch mode) |
| 40000 | Bad request — check parameters |
| 40100 | Unauthorized — check credentials |
| 40200 | Payment required — insufficient balance |
| 40400 | Not found |
| 50000 | Internal server error — retry |

Always check both the top-level `status_code` and each `tasks[].status_code` — they can differ.

## Mode Detection

To determine if enhanced mode is available, check for DataForSEO credentials in settings:

```
If dataforseo_login AND dataforseo_password are non-empty in settings:
  → Enhanced mode: use DataForSEO API for keyword metrics
Else:
  → Free mode: use WebSearch SERP heuristics
```

In free mode, skip all DataForSEO calls and use the difficulty heuristics from `difficulty-heuristics.md` instead.
