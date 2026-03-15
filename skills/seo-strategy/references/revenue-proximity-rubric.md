# Revenue-Proximity Scoring by Business Model

Detailed scoring matrices for each business model type. Use these to accurately score keywords based on the specific startup's revenue model.

## SaaS (B2B)

| Score | Keyword Patterns | Examples |
|-------|-----------------|----------|
| 5 | `[product] vs [competitor]`, `[category] pricing`, `best [tool] for [ICP]`, `[competitor] alternative`, `[product] review` | "HubSpot vs Salesforce", "project management tool pricing", "best CRM for startups" |
| 4 | `how to [problem product solves]`, `[category] tools`, `[use case] software`, `[pain point] solution`, free tool/calculator content | "how to automate sales outreach", "email marketing tools", "reduce customer churn software" |
| 3 | `what is [concept]`, `[industry] best practices`, `[process] guide`, `[metric] benchmarks` | "what is product-led growth", "SaaS onboarding best practices", "customer retention guide" |
| 2 | `[industry] trends`, `[industry] statistics`, `state of [market]`, `[role] skills` | "SaaS trends 2024", "B2B marketing statistics", "state of customer success" |
| 1 | `[general business]`, `[adjacent topic]`, `[career advice]` | "how to start a business", "remote work tips", "tech salary guide" |

## SaaS (B2C / PLG)

| Score | Keyword Patterns | Examples |
|-------|-----------------|----------|
| 5 | `[product] vs [competitor]`, `best [app] for [use case]`, `[competitor] alternative free`, `[product] pricing` | "Notion vs Obsidian", "best note-taking app", "Evernote alternative free" |
| 4 | `how to [task product enables]`, `[category] app`, `[use case] template`, `free [tool type]` | "how to organize notes", "habit tracker app", "project template free" |
| 3 | `[activity] tips`, `[productivity method] guide`, `how to [broader skill]` | "productivity tips for students", "GTD method guide", "how to build a second brain" |
| 2 | `[lifestyle topic]`, `[broad self-improvement]` | "work-life balance", "morning routine ideas" |
| 1 | `[unrelated lifestyle]`, `[entertainment]` | "best podcasts 2024", "home office decor" |

## Services / Agency

| Score | Keyword Patterns | Examples |
|-------|-----------------|----------|
| 5 | `[service] agency`, `[service] consultant`, `hire [role]`, `[city] [service]`, `[service] pricing`, `outsource [function]` | "SEO agency for startups", "hire fractional CMO", "Toronto web design agency" |
| 4 | `[service] case study`, `[deliverable] examples`, `how to choose [service provider]`, `[service] RFP template` | "website redesign case study", "brand strategy examples", "how to choose a marketing agency" |
| 3 | `[skill area] best practices`, `[deliverable] guide`, `DIY [service]`, `[service] checklist` | "content marketing best practices", "brand positioning guide", "SEO audit checklist" |
| 2 | `[industry] trends`, `[role] career`, `what does a [role] do` | "digital marketing trends", "UX designer career path" |
| 1 | `[general business advice]`, `[adjacent industry]` | "startup funding guide", "how to manage a team" |

## Ecommerce

| Score | Keyword Patterns | Examples |
|-------|-----------------|----------|
| 5 | `buy [product]`, `[product] [year]`, `best [product] for [use case]`, `[product] review`, `[product] vs [product]`, `[brand] discount code` | "buy ergonomic keyboard", "best running shoes 2024", "Herman Miller vs Steelcase" |
| 4 | `[product category] buying guide`, `[product] size guide`, `[product] for [audience]`, `[product] under $[price]` | "mechanical keyboard buying guide", "running shoes for flat feet", "standing desks under $500" |
| 3 | `how to [use/maintain product]`, `[product] setup guide`, `[material/feature] explained` | "how to clean leather boots", "standing desk setup guide", "Cherry MX switches explained" |
| 2 | `[lifestyle topic]`, `[hobby] for beginners`, `[industry] trends` | "home office setup ideas", "running for beginners", "ergonomics trends" |
| 1 | `[general lifestyle]`, `[tangential hobby]` | "work from home tips", "fitness motivation" |

## Marketplace / Platform

| Score | Keyword Patterns | Examples |
|-------|-----------------|----------|
| 5 | `[category] marketplace`, `[category] near me`, `find [provider/product]`, `[provider type] for hire`, `sell [product] online` | "freelance designer marketplace", "find a plumber near me", "sell handmade jewelry online" |
| 4 | `best [provider] in [city]`, `how to hire [provider]`, `[provider] rates`, `how to sell on [platform type]` | "best photographers in Austin", "how to hire a contractor", "freelance rates 2024" |
| 3 | `[industry] guide`, `how to [activity the marketplace serves]`, `[provider role] vs [provider role]` | "home renovation guide", "how to plan a wedding", "interior designer vs decorator" |
| 2 | `[industry] trends`, `[broad topic]` | "gig economy trends", "remote work statistics" |
| 1 | `[tangential]` | "small business taxes", "career change advice" |

## Scoring Rules

1. **Always score from the startup's perspective**, not the searcher's. A keyword scores 5 if the startup can directly convert that searcher, even if the keyword itself seems informational.

2. **Free tool / calculator content** in SaaS gets score 4, not 3. These generate leads directly even though they're "informational."

3. **Case studies and social proof keywords** score 4 for services, 3 for SaaS. Services buyers research more heavily before purchasing.

4. **Location-modified keywords** get +1 score for services and marketplaces (local intent = higher conversion). Cap at 5.

5. **"How to" keywords** score 3-4 depending on whether the how-to directly involves the product/service (4) or is about the broader discipline (3).

6. **Competitor brand keywords** always score 5. Anyone searching for a competitor by name is in buying mode.
