---
name: ui-mockup-screenshot-generator
description: Use when the user needs realistic UI mockups — app screens, dashboards, landing pages — for presentations, marketing, or design review. Always produces high-fidelity, pixel-clean UI shots in the requested device frame.
---

# UI Mockup / Screenshot Generator

UI mockups must look like real product screenshots, not illustrations of UI.

## Device Frames
- Desktop: 1440×900 browser frame (macOS Chrome preferred)
- Tablet: iPad Pro 11" or 12.9" frame
- Phone: iPhone 15 Pro frame (or Pixel 8 for Android)
- Watch: Apple Watch Ultra frame

## Layout Rules
- Realistic density: not too sparse (looks unfinished), not too dense (looks cluttered)
- Real copy: no "Lorem ipsum", no "Button" labels — use plausible real content
- Real data: numbers should be plausible, dates should be recent, names should be diverse
- Proper hierarchy: clear visual order from headers to body to captions
- Proper spacing: 8px grid, consistent padding
- Realistic typography: not all bold, not all the same size

## Color Rules
- Light mode: white/off-white background, dark text, one accent color
- Dark mode: #0A0A0A or #121212 background, off-white text, one accent
- Pick ONE accent color and use it consistently
- No rainbow UIs unless explicitly requested

## Component Library (built into prompts)
- Buttons (primary, secondary, ghost)
- Form inputs (text, select, checkbox, radio, toggle)
- Cards (with shadow, with border, with header)
- Tables / lists
- Charts (bar, line, donut, heatmap)
- Navigation (top bar, sidebar, tabs, breadcrumb)
- Modals / drawers
- Empty states
- Loading states (skeleton)

## Prompt Template
```
High-fidelity UI screenshot of [APP TYPE / SCREEN],
[light/dark mode], [accent color], [typography: Inter / SF Pro / Roboto],
realistic content: [list 3-5 specific data points to show],
proper visual hierarchy, 8px spacing grid, [component list],
shown in [device frame], crisp pixels, 4k, dribbble quality
```

## Forbidden Behaviors
- Placeholder text
- Random colors that don't form a palette
- Components that don't exist in real UI libraries
- Text that overflows its container
- 3D effects / skeuomorphism unless explicitly requested

## Output Format
1. Device + mode + accent color
2. The mockup
3. Component list shown

