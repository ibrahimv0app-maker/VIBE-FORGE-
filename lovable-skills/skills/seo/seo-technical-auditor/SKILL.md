---
name: seo-technical-auditor
description: Use when auditing technical SEO — meta tags, structured data, sitemap, robots, canonicals, internal links. Always produces a comprehensive audit with actionable fixes.
---

# SEO Technical Auditor

Technical SEO is the foundation. Without it, content doesn't rank.

## Audit Checklist

### 1. Crawlability
- [ ] `robots.txt` allows important pages
- [ ] `robots.txt` blocks irrelevant pages (admin, search results, params)
- [ ] XML sitemap submitted to Google Search Console
- [ ] Sitemap auto-updates when content changes
- [ ] No orphaned pages (every page has internal links)
- [ ] Crawl budget optimized (no infinite URL params)

### 2. Indexability
- [ ] `noindex` on thin / duplicate pages
- [ ] Canonical tags on duplicate content
- [ ] `hreflang` on multi-language pages
- [ ] No accidental `noindex` on important pages
- [ ] 404 page is helpful (links to popular pages)

### 3. URL Structure
- [ ] URLs are lowercase, hyphen-separated
- [ ] URLs are short and descriptive
- [ ] No URL parameters when possible
- [ ] Trailing slashes consistent
- [ ] No `.html` / `.php` extensions

### 4. Meta Tags
```html
<title>Descriptive Title | Brand</title>  <!-- 50-60 chars -->
<meta name="description" content="...">     <!-- 150-160 chars -->
<link rel="canonical" href="https://...">
<meta name="robots" content="index, follow">
```

### 5. Open Graph & Twitter Cards
```html
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:image" content="https://...">  <!-- 1200x630 -->
<meta property="og:url" content="https://...">
<meta property="og:type" content="website">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@brand">
```

### 6. Structured Data (Schema.org)
```json-ld
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "...",
  "image": "https://...",
  "datePublished": "2024-...",
  "author": { "@type": "Person", "name": "..." }
}
```
- Validate with Google's Rich Results Test
- Don't fake schema (Google penalizes)
- Common types: Article, Product, FAQ, HowTo, BreadcrumbList, Organization

### 7. Heading Structure
- One `<h1>` per page
- `<h2>` for major sections
- `<h3>` for subsections
- Don't skip levels (h1 → h3 is bad)
- Headings describe the content (not just for styling)

### 8. Internal Linking
- Every page has at least 3 internal links
- Use descriptive anchor text (not "click here")
- Link to important pages from high-authority pages
- Breadcrumbs on every page
- Related posts / products

### 9. Images
- `alt` attribute on every image (descriptive, not keyword-stuffed)
- Descriptive filename (`red-running-shoes.jpg` not `IMG_1234.jpg`)
- Compressed (WebP / AVIF preferred)
- Lazy-loaded (except LCP image)
- Width/height set (prevents CLS)

### 10. Page Speed (see web-performance-auditor)
- LCP < 2.5s
- INP < 200ms
- CLS < 0.1

### 11. Mobile-Friendly
- Responsive design
- Touch targets ≥ 44×44px
- No intrusive interstitials
- Font size ≥ 16px on mobile

### 12. HTTPS
- SSL certificate valid
- HTTP redirects to HTTPS
- HSTS header set
- Mixed content fixed

### 13. International
- `hreflang` for multilingual
- Localized URLs (`/en/`, `/es/`)
- Language switcher
- Currency / region detection

## Tools
- Google Search Console
- Screaming Frog (crawl)
- Ahrefs / Semrush (backlinks, keywords)
- PageSpeed Insights
- Schema.org validator
- Rich Results Test

## Common Issues
- Duplicate content (canonical fixes)
- Thin content (noindex or expand)
- Orphaned pages (add internal links)
- Broken links (301 redirect or remove)
- Redirect chains (collapse to one hop)
- Slow server (CDN, caching)

## Audit Report Format
For each issue:
- Page URL
- Issue description
- Severity (Critical / High / Medium / Low)
- Recommended fix
- Expected impact

## Forbidden Patterns
- Keyword stuffing
- Hidden text / links
- Cloaking
- Buying links
- Duplicate content across domains
- Auto-generated content
- Sneaky redirects

## Output Format
1. Site summary
2. Audit findings (sorted by severity)
3. Quick wins (< 1 day each)
4. Long-term fixes
5. Expected traffic impact

