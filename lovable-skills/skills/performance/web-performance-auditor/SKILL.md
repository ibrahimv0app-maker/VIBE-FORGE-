---
name: web-performance-auditor
description: Use when auditing web performance — Core Web Vitals, bundle size, render performance, network. Always produces a prioritized action plan with measurable improvements.
---

# Web Performance Auditor

Performance is a feature. Measure, prioritize, optimize.

## Core Web Vitals (the 3 that matter)
- **LCP** (Largest Contentful Paint): < 2.5s
- **INP** (Interaction to Next Paint): < 200ms
- **CLS** (Cumulative Layout Shift): < 0.1

## Other Vital Metrics
- **FCP** (First Contentful Paint): < 1.8s
- **TTFB** (Time to First Byte): < 800ms
- **TBT** (Total Blocking Time): < 200ms

## Audit Process
1. Run Lighthouse on mobile + desktop
2. Run PageSpeed Insights
3. Check Chrome DevTools Performance tab
4. Check Network tab (waterfall)
5. Check Coverage tab (unused JS/CSS)
6. Check Bundle Analyzer
7. Check Web Vitals in production (CrUX)

## Common Issues & Fixes

### Slow LCP
- **Cause**: large hero image, render-blocking JS, slow TTFB
- **Fix**:
  - Use `next/image` or `loading="eager"` + `fetchpriority="high"` for LCP image
  - Preload LCP image: `<link rel="preload" as="image" href="...">`
  - Defer non-critical JS
  - Optimize TTFB (CDN, edge, faster origin)

### High INP
- **Cause**: long JS tasks blocking the main thread
- **Fix**:
  - Break long tasks with `setTimeout` or `scheduler.yield()`
  - Debounce/throttle event handlers
  - Use `requestAnimationFrame` for visual updates
  - Move heavy work to Web Workers
  - Reduce JS bundle size

### High CLS
- **Cause**: images without dimensions, late-loading fonts, dynamic content
- **Fix**:
  - Always set `width` and `height` on images (or `aspect-ratio` in CSS)
  - Use `font-display: swap` or `font-display: optional`
  - Reserve space for ads / embeds
  - Don't insert content above existing content

### Slow TTFB
- **Cause**: slow origin, no CDN, slow DB queries
- **Fix**:
  - Use a CDN (Cloudflare, Vercel Edge, CloudFront)
  - Cache at the edge
  - Optimize DB queries (see sql-query-optimizer skill)
  - Use SSR with streaming

### Large JS Bundle
- **Cause**: too many dependencies, no code splitting, large components
- **Fix**:
  - Code split with `next/dynamic` or `React.lazy`
  - Tree-shake unused exports
  - Replace large libs (moment → date-fns, lodash → native)
  - Audit with `@next/bundle-analyzer`
  - Lazy-load below-the-fold components

## Image Optimization
```tsx
// Next.js (auto-optimizes)
import Image from 'next/image'
<Image
  src="/hero.jpg"
  alt="Hero"
  width={1600}
  height={900}
  priority  // for LCP image
/>

// Plain HTML
<img
  src="/hero.jpg"
  alt="Hero"
  width="1600"
  height="900"
  loading="eager"
  fetchpriority="high"
/>
<img
  src="/other.jpg"
  alt="Other"
  loading="lazy"
  decoding="async"
/>
```

## Font Optimization
```tsx
// Next.js (auto-optimizes)
import { Inter } from 'next/font/google'
const inter = Inter({ subsets: ['latin'], display: 'swap' })

// Plain HTML
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
```

## Code Splitting
```tsx
// Route-level (Next.js does this automatically)
// Component-level
const HeavyChart = dynamic(() => import('./HeavyChart'), {
  loading: () => <Skeleton />,
  ssr: false,  // if it uses browser APIs
})
```

## Render Performance
- Use `React.memo` for expensive components with stable props
- Use `useMemo` for expensive calculations
- Use `useCallback` for stable function references
- Don't overdo it (memoization has overhead)
- Use `key` prop correctly in lists (stable IDs, not array index)
- Virtualize long lists (react-window, react-virtuoso)

## Network Optimization
- HTTP/2 or HTTP/3 (multiplexing)
- Brotli compression (better than gzip)
- Cache headers: `Cache-Control: public, max-age=31536000, immutable` for hashed assets
- Preconnect to third-party origins
- Prefetch likely-next resources

## Service Worker (PWA)
- Cache static assets
- Offline fallback
- Background sync
- Be careful: bad caching can break updates

## Measurement in Production
```ts
// Track Web Vitals
import { useReportWebVitals } from 'next/web-vitals'

export function reportWebVitals(metric) {
  // Send to analytics
  fetch('/api/web-vitals', { method: 'POST', body: JSON.stringify(metric) })
}
```

## Performance Budget
- JS: < 200KB initial
- CSS: < 50KB initial
- Images: < 500KB initial
- Fonts: < 100KB initial
- LCP: < 2.5s on 4G

## Forbidden Patterns
- `useEffect` for everything (causes re-renders)
- Inline objects/arrays as props (breaks memo)
- Massive context providers that re-render on every change
- Not setting image dimensions
- Loading all fonts (only load what you use)
- Ignoring mobile performance

## Output Format
1. Audit findings table (metric, current, target, fix)
2. Prioritized action plan (Quick wins / Medium / Long-term)
3. Expected impact per fix
4. Measurement plan (how to verify improvements)

