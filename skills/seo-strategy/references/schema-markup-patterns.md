# Schema Markup Patterns

Recommended JSON-LD schema types for each content format. Each content brief should suggest the appropriate schema markup based on the post's content format.

## Format → Schema Mapping

| Content Format | Primary Schema | Secondary Schema |
|---------------|---------------|-----------------|
| How-To Guide | HowTo | Article, FAQPage |
| Comparison Post | Article | FAQPage |
| Listicle | Article + ItemList | FAQPage |
| Product Review | Review | Product, FAQPage |
| Case Study | Article | Organization |
| FAQ Page | FAQPage | Article |
| Buying Guide | Article | ItemList, FAQPage |
| Tutorial | HowTo | Article, VideoObject |
| Thought Leadership | Article | Person (author) |
| Landing Page | WebPage | Product, Organization |

## JSON-LD Templates

### Article (Most Common)
Use for blog posts, guides, thought leadership, comparisons.

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[Post Title]",
  "description": "[Meta description]",
  "author": {
    "@type": "Person",
    "name": "[Author Name]",
    "url": "[Author Page URL]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "[Company Name]",
    "logo": {
      "@type": "ImageObject",
      "url": "[Logo URL]"
    }
  },
  "datePublished": "[YYYY-MM-DD]",
  "dateModified": "[YYYY-MM-DD]",
  "image": "[Featured Image URL]"
}
```

### HowTo
Use for step-by-step guides and tutorials.

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "[How-To Title]",
  "description": "[Brief description of what this teaches]",
  "step": [
    {
      "@type": "HowToStep",
      "name": "[Step 1 Title]",
      "text": "[Step 1 description]",
      "image": "[Step 1 image URL (optional)]"
    },
    {
      "@type": "HowToStep",
      "name": "[Step 2 Title]",
      "text": "[Step 2 description]"
    }
  ],
  "totalTime": "PT[X]M",
  "estimatedCost": {
    "@type": "MonetaryAmount",
    "currency": "USD",
    "value": "[cost or 0 if free]"
  }
}
```

### FAQPage
Use for posts with Q&A sections. Can supplement any format.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Question 1]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Answer 1]"
      }
    },
    {
      "@type": "Question",
      "name": "[Question 2]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Answer 2]"
      }
    }
  ]
}
```

### Review
Use for product reviews and comparison posts.

```json
{
  "@context": "https://schema.org",
  "@type": "Review",
  "itemReviewed": {
    "@type": "Product",
    "name": "[Product Name]"
  },
  "author": {
    "@type": "Person",
    "name": "[Author Name]"
  },
  "reviewRating": {
    "@type": "Rating",
    "ratingValue": "[X]",
    "bestRating": "5"
  },
  "reviewBody": "[Brief review summary]"
}
```

### ItemList
Use for listicles and ranked lists.

```json
{
  "@context": "https://schema.org",
  "@type": "ItemList",
  "name": "[List Title]",
  "description": "[What this list covers]",
  "numberOfItems": [X],
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "[Item 1 Name]",
      "url": "[Item 1 URL (optional)]"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "[Item 2 Name]"
    }
  ]
}
```

### BreadcrumbList
Recommend for ALL posts — helps Google understand site structure.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://example.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Blog",
      "item": "https://example.com/blog/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "[Pillar Category]",
      "item": "https://example.com/blog/[pillar-slug]/"
    }
  ]
}
```

## Brief Format

For each content brief, include a schema section:

```
### Schema Markup
- **Primary**: [Schema Type] — [why this type]
- **Secondary**: [Schema Type] — [optional, when applicable]
- **Always include**: BreadcrumbList, Article (base)
```

## Implementation Notes for Briefs

1. **Always recommend BreadcrumbList** — it's low effort, high impact for site structure signals.
2. **FAQPage as supplement**: If a post has a FAQ section (most should), add FAQPage schema for those questions. This can generate rich results.
3. **Don't over-schema**: One primary type + BreadcrumbList is usually sufficient. Adding every possible schema looks spammy.
4. **HowTo is powerful**: If a post has numbered steps, HowTo schema can generate rich step-by-step snippets in SERPs.
5. **Review schema requires compliance**: Google has strict guidelines for Review schema. Only recommend if the post genuinely reviews/rates a product.
