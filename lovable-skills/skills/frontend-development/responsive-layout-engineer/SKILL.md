---
name: responsive-layout-engineer
description: Use when building responsive layouts — grids, flexbox, breakpoints, mobile-first. Always produces layouts that work flawlessly from 320px to 4K.
---

# Responsive Layout Engineer

Mobile-first is non-negotiable. Every layout starts at 320px and scales up.

## Breakpoint Convention (Tailwind)
- `sm` 640px — large phones in landscape
- `md` 768px — tablets
- `lg` 1024px — small laptops
- `xl` 1280px — desktops
- `2xl` 1536px — large desktops

## Mobile-First Rule
Write the base (mobile) styles first, then add larger breakpoints:
```tsx
// GOOD: mobile-first
<div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">

// BAD: desktop-first (overrides everything for mobile)
<div className="grid grid-cols-4 lg:grid-cols-2 sm:grid-cols-1">
```

## Layout Decision Tree
- 1D layout (row OR column) → Flexbox
- 2D layout (rows AND columns) → CSS Grid
- Free-flow text → Block
- Decorative / overlapping → Absolute / Grid areas

## Common Patterns

### Card Grid
```tsx
<div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
  {items.map(item => <Card key={item.id} {...item} />)}
</div>
```

### Sidebar + Main
```tsx
<div className="flex flex-col lg:flex-row">
  <aside className="lg:w-64 lg:shrink-0 border-b lg:border-b-0 lg:border-r">
    <Sidebar />
  </aside>
  <main className="flex-1 min-w-0">
    <Content />
  </main>
</div>
```

### Sticky Header + Scrollable Content
```tsx
<div className="h-screen flex flex-col">
  <header className="h-16 shrink-0 border-b" />
  <main className="flex-1 overflow-y-auto">
    <Content />
  </main>
</div>
```

### Centered Container
```tsx
<div className="mx-auto w-full max-w-7xl px-4 sm:px-6 lg:px-8">
  {children}
</div>
```

## Critical Rules
- `min-w-0` on flex children (prevents overflow)
- `overflow-x-hidden` on body to prevent horizontal scroll on mobile
- `aspect-ratio` for media containers (prevents layout shift)
- `object-fit: cover` for images in fixed containers
- Test every layout at 320px, 375px, 768px, 1024px, 1440px

## Image Responsiveness
```tsx
<img
  src={src}
  alt={alt}
  className="w-full h-auto"
  loading="lazy"
  decoding="async"
/>
```
For art direction (different images per breakpoint):
```tsx
<picture>
  <source media="(min-width: 1024px)" srcSet={desktop} />
  <source media="(min-width: 640px)" srcSet={tablet} />
  <img src={mobile} alt={alt} className="w-full h-auto" />
</picture>
```

## Typography Scale
```css
.text-responsive {
  font-size: clamp(1rem, 0.875rem + 0.5vw, 1.5rem);
}
```
Or use Tailwind's responsive text utilities:
```tsx
<h1 className="text-2xl sm:text-3xl lg:text-4xl xl:text-5xl">
```

## Touch Targets
- Minimum 44×44px for any interactive element on mobile
- Minimum 8px gap between adjacent interactive elements

## Forbidden Patterns
- Fixed widths on mobile (`w-[375px]`)
- `overflow-x: scroll` to hide horizontal overflow (fix the layout instead)
- Breakpoint-only layouts without a sensible mobile base
- `position: absolute` for primary layout (use Grid/Flex)
- Fixed pixel heights for content (`h-[800px]`)

## Output Format
1. Layout pattern chosen and why
2. The code
3. Breakpoint behavior table (what changes at each breakpoint)
4. Mobile testing checklist

