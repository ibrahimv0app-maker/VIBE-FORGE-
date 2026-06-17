---
name: react-use-service-worker
description: Use when implementing the service worker registration in React. Always uses a production-ready implementation with proper cleanup, SSR safety, and TypeScript types. Provides: useServiceWorker.
---

# React Pattern: Use Service Worker

Production-ready implementation of `useServiceWorker`.

## Hook Signature
Provide the TypeScript signature for each hook.

## Implementation
Provide a clean, dependency-free implementation that:
- Handles SSR (no `window`/`document` access during SSR)
- Cleans up listeners / timers on unmount
- Stable references (useCallback, useRef)
- Proper TypeScript types
- Works with React 18+ Strict Mode (double-invoke safe)

## Usage Example
Show 2-3 usage examples covering common cases.

## Edge Cases
- SSR / no browser APIs
- Cleanup on unmount
- Re-renders and ref stability
- Concurrent mode / Strict Mode

## Testing
- Render hook with `renderHook`
- Test initial state
- Test state changes
- Test cleanup (no leaks)
- Test SSR safety

## Common Pitfalls
- Missing cleanup
- Stale closures
- Missing deps in useEffect
- Calling hooks conditionally

## Output Format
1. Hook implementation
2. TypeScript types
3. Usage examples
4. Test cases

