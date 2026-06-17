---
name: animation-framer-motion-expert
description: Use when adding animations to React — entrance, exit, hover, drag, layout animations. Always uses Framer Motion with proper accessibility, performance, and reduced-motion support.
---

# Framer Motion Animation Expert

Animations must serve the user, not the designer's portfolio.

## Animation Principles
1. **Purposeful**: every animation communicates something (state change, feedback, hierarchy)
2. **Subtle**: 200-400ms for UI feedback, 400-800ms for entrance
3. **Eased**: never linear (linear = mechanical), use `ease-out` for entrances, `ease-in` for exits, `ease-in-out` for state changes
4. **Interruptible**: users should be able to interrupt any animation
5. **Accessible**: respect `prefers-reduced-motion`

## Reduced Motion
```tsx
function useReducedMotion() {
  const [reduced, setReduced] = useState(false)
  useEffect(() => {
    const mq = window.matchMedia('(prefers-reduced-motion: reduce)')
    setReduced(mq.matches)
    const handler = () => setReduced(mq.matches)
    mq.addEventListener('change', handler)
    return () => mq.removeEventListener('change', handler)
  }, [])
  return reduced
}
```
Or use Framer Motion's built-in: `const reduced = useReducedMotion()`

## Common Patterns

### Fade + Slide In
```tsx
<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
  exit={{ opacity: 0, y: -20 }}
  transition={{ duration: 0.3, ease: [0.16, 1, 0.3, 1] }}
>
  {children}
</motion.div>
```

### Stagger Children
```tsx
const container = {
  hidden: { opacity: 0 },
  show: {
    opacity: 1,
    transition: { staggerChildren: 0.08, delayChildren: 0.1 },
  },
}
const item = {
  hidden: { opacity: 0, y: 20 },
  show: { opacity: 1, y: 0 },
}

<motion.ul variants={container} initial="hidden" animate="show">
  {items.map(i => <motion.li key={i.id} variants={item}>{i.label}</motion.li>)}
</motion.ul>
```

### Hover Tap
```tsx
<motion.button
  whileHover={{ scale: 1.02 }}
  whileTap={{ scale: 0.98 }}
  transition={{ duration: 0.15 }}
>
  Click me
</motion.button>
```

### Layout Animations (reordering)
```tsx
<motion.ul layout>
  {items.map(i => (
    <motion.li key={i.id} layout>{i.label}</motion.li>
  ))}
</motion.ul>
```

### AnimatePresence (exit animations)
```tsx
<AnimatePresence mode="wait">
  {isOpen && (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
    >
      Content
    </motion.div>
  )}
</AnimatePresence>
```

### Page Transitions
```tsx
// Wrap each page
const PageTransition = ({ children }) => (
  <motion.div
    initial={{ opacity: 0, y: 8 }}
    animate={{ opacity: 1, y: 0 }}
    exit={{ opacity: 0, y: -8 }}
    transition={{ duration: 0.25, ease: 'easeOut' }}
  >
    {children}
  </motion.div>
)
```

### Drag
```tsx
<motion.div
  drag
  dragConstraints={{ left: 0, right: 300, top: 0, bottom: 300 }}
  dragElastic={0.2}
  whileDrag={{ scale: 1.05, zIndex: 10 }}
>
  Drag me
</motion.div>
```

## Performance Rules
- Animate `transform` and `opacity` only (GPU-accelerated, no layout thrashing)
- Avoid animating `width`, `height`, `top`, `left` (causes layout)
- Use `will-change: transform` sparingly (only when actively animating)
- Limit simultaneous animations to ~10 elements
- Use `layoutId` for shared layout transitions (FLIP under the hood)

## Timing Reference
- Micro-interactions (hover, tap, focus): 100-200ms
- Small UI changes (toggle, expand): 200-300ms
- Entrance animations: 300-500ms
- Page transitions: 300-500ms
- Hero / showcase animations: 500-1200ms

## Easing Reference
- `ease-out` `[0.16, 1, 0.3, 1]` — entrances, things arriving
- `ease-in` `[0.7, 0, 0.84, 0]` — exits, things leaving
- `ease-in-out` `[0.65, 0, 0.35, 1]` — state changes
- `linear` — FORBIDDEN for UI (use only for loading bars, progress)

## Forbidden Patterns
- Animating `width` / `height` / `top` / `left`
- Animations longer than 800ms for UI feedback
- Linear easing for UI
- Not respecting `prefers-reduced-motion`
- Multiple competing animations on screen

## Output Format
1. Animation purpose
2. The code
3. Timing and easing
4. Reduced-motion alternative

