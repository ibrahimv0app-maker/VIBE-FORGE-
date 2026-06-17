---
name: wcag-accessibility-auditor
description: Use when auditing a web app for accessibility — WCAG 2.1 AA compliance. Always uses manual + automated checks, verifies with screen readers, and produces actionable fixes.
---

# WCAG Accessibility Auditor

Accessibility is not optional. Audit every page.

## Audit Process
1. Automated scan (axe-core, Lighthouse)
2. Manual keyboard navigation
3. Screen reader test (VoiceOver / NVDA)
4. Color contrast check
5. Mobile accessibility (zoom, dynamic type)
6. Cognitive check (clear language, consistent nav)

## WCAG 2.1 AA Checklist

### Perceivable
- [ ] All images have descriptive `alt` (or empty `alt=""` for decorative)
- [ ] Complex images have long descriptions
- [ ] No information conveyed by color alone
- [ ] Color contrast ≥ 4.5:1 (normal text), ≥ 3:1 (large text, UI)
- [ ] Audio/video has captions / transcripts
- [ ] Content reflows at 200% zoom (no horizontal scroll)
- [ ] Content reflows at 320px width
- [ ] Text spacing can be overridden (no `!important` on text)
- [ ] No images of text (except logos)

### Operable
- [ ] All functionality available via keyboard
- [ ] Logical tab order
- [ ] Visible focus indicator (≥ 3:1 contrast)
- [ ] No keyboard traps (can Tab out of any component)
- [ ] Skip-to-content link
- [ ] Page titles are descriptive
- [ ] No content flashes more than 3 times per second
- [ ] No time limits without pause/stop/extend

### Understandable
- [ ] Language declared: `<html lang="en">`
- [ ] Language changes marked: `<span lang="es">`
- [ ] Navigation consistent across pages
- [ ] Components have consistent identification
- [ ] Errors are identified and described
- [ ] Error suggestions are provided
- [ ] No unexpected context changes (no surprise navigation)
- [ ] Form labels are associated with inputs
- [ ] Required fields indicated

### Robust
- [ ] Valid HTML
- [ ] ARIA used correctly (don't overuse)
- [ ] Custom components have ARIA roles/states
- [ ] Status messages announced (`role="status"` or `aria-live`)
- [ ] Works with assistive technologies (test with screen reader)

## Common Issues & Fixes

### Missing alt text
```html
<!-- Bad -->
<img src="logo.png">

<!-- Good -->
<img src="logo.png" alt="Company Logo">

<!-- Decorative -->
<img src="divider.png" alt="">
```

### Form labels
```html
<!-- Bad -->
<input type="email" placeholder="Email">

<!-- Good -->
<label for="email">Email</label>
<input type="email" id="email" name="email" required>
```

### Button vs link
```html
<!-- Bad: div with onClick -->
<div onclick="submit()">Submit</div>

<!-- Good: button -->
<button type="submit">Submit</button>
```

### Focus indicator
```css
/* Bad: removes focus outline */
*:focus { outline: none; }

/* Good: visible focus */
*:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}
```

### Heading order
```html
<!-- Bad: skipped levels -->
<h1>Title</h1>
<h3>Subtitle</h3>

<!-- Good: sequential -->
<h1>Title</h1>
<h2>Subtitle</h2>
```

### Modal trap
```tsx
// Use focus-trap-react or @radix-ui/react-dialog
<Dialog>
  <DialogContent>  <!-- handles focus trap, escape, restore focus -->
    ...
  </DialogContent>
</Dialog>
```

### ARIA live regions
```html
<!-- For dynamic updates -->
<div role="status" aria-live="polite">
  {message}
</div>

<!-- For urgent updates -->
<div role="alert" aria-live="assertive">
  {error}
</div>
```

### Icon-only buttons
```html
<!-- Bad: no accessible name -->
<button><svg>...</svg></button>

<!-- Good: aria-label -->
<button aria-label="Close"><svg>...</svg></button>
```

### Skip link
```html
<a href="#main" class="skip-link">Skip to main content</a>
<main id="main">...</main>
```

## Component-Specific Patterns

### Tabs
- `role="tablist"` on container
- `role="tab"` on each tab
- `role="tabpanel"` on each panel
- `aria-selected` on active tab
- `aria-controls` linking tab to panel
- Arrow keys to switch tabs

### Modal/Dialog
- `role="dialog"` or `role="alertdialog"`
- `aria-modal="true"`
- `aria-labelledby` for title
- `aria-describedby` for description
- Focus trap inside
- Escape to close
- Restore focus on close

### Dropdown / Menu
- `role="menu"` on container
- `role="menuitem"` on items
- `aria-expanded` on trigger
- `aria-haspopup="menu"` on trigger
- Arrow keys to navigate

### Combobox / Autocomplete
- Use ARIA 1.2 combobox pattern
- `aria-expanded`, `aria-controls`, `aria-activedescendant`
- Type ahead, arrow keys, escape to close

## Automated Testing
```ts
// Jest + axe
import { axe } from 'vitest-axe'
import { render } from '@testing-library/react'

it('should have no a11y violations', async () => {
  const { container } = render(<Button>Click</Button>)
  const results = await axe(container)
  expect(results).toHaveNoViolations()
})
```

```ts
// Playwright + axe
import { injectAxe, checkA11y } from 'axe-playwright'

await injectAxe(page)
await checkA11y(page, null, {
  detailedReport: true,
})
```

## Forbidden Patterns
- `div` with `onClick` (use `button`)
- Removing focus outline without replacement
- `placeholder` as label
- Color alone for state (error / required)
- `tabindex` > 0 (use 0 or -1)
- Auto-playing audio
- New tabs without warning (`target="_blank"`)

## Output Format
1. Audit summary (violations per WCAG category)
2. Findings table (severity, WCAG criterion, page, fix)
3. Quick wins
4. Component-specific fixes
5. Screen reader test results

