---
name: vitest-unit-testing-architect
description: Use when writing unit tests for React / Node with Vitest. Always uses proper test structure, mocking, and follows testing trophy strategy.
---

# Vitest Unit Testing Architect

Test behavior, not implementation. Favor integration over unit when in doubt.

## Testing Trophy
- **Most**: integration tests (test the system, not the units)
- **Some**: unit tests (for pure functions, complex logic)
- **Few**: end-to-end tests (smoke tests of critical paths)
- **Static**: TypeScript + ESLint (free)

## Test Structure
```ts
import { describe, it, expect, beforeEach, vi } from 'vitest'
import { render, screen } from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import { TodoList } from './TodoList'

describe('TodoList', () => {
  describe('when todos exist', () => {
    it('renders all todos', () => {
      // Arrange
      const todos = [{ id: '1', title: 'Buy milk' }, { id: '2', title: 'Walk dog' }]
      // Act
      render(<TodoList todos={todos} />)
      // Assert
      expect(screen.getByText('Buy milk')).toBeInTheDocument()
      expect(screen.getByText('Walk dog')).toBeInTheDocument()
    })
  })

  describe('when no todos', () => {
    it('shows empty state', () => {
      render(<TodoList todos={[]} />)
      expect(screen.getByText(/no todos/i)).toBeInTheDocument()
    })
  })

  describe('when toggling a todo', () => {
    it('calls onToggle with the todo id', async () => {
      const user = userEvent.setup()
      const onToggle = vi.fn()
      render(<TodoList todos={[{ id: '1', title: 'Test' }]} onToggle={onToggle} />)
      await user.click(screen.getByRole('checkbox'))
      expect(onToggle).toHaveBeenCalledWith('1')
    })
  })
})
```

## AAA Pattern
- **Arrange**: set up the test data
- **Act**: perform the action under test
- **Assert**: verify the outcome

## Naming
- `describe('ComponentName', ...)` — name of the unit under test
- `it('does X when Y', ...)` — behavior + condition
- Don't write `it('should render', ...)` — write `it('renders the title', ...)`

## Testing Library Queries (in order of preference)
1. `getByRole` — accessibility-first, best
2. `getByLabelText` — for form fields
3. `getByPlaceholderText` — fallback
4. `getByText` — for non-interactive content
5. `getByDisplayValue` — for current input value
6. `getByAltText` — for images
7. `getByTitle` — for title attributes
8. `getByTestId` — last resort

## Async Queries
- `getBy*` — synchronous, throws if not found
- `findBy*` — async, waits up to 1000ms
- `queryBy*` — synchronous, returns null if not found (for negation)

## Mocking
```ts
// Mock a module
vi.mock('@/lib/api', () => ({
  getTodos: vi.fn().mockResolvedValue([{ id: '1', title: 'Mocked' }]),
}))

// Mock implementation
const mockFn = vi.fn()
  .mockReturnValueOnce(1)
  .mockReturnValueOnce(2)
  .mockResolvedValue('async')

// Spy on existing
const spy = vi.spyOn(console, 'log').mockImplementation(() => {})
spy.mockRestore()
```

## MSW (Mock Service Worker)
```ts
import { http, HttpResponse } from 'msw'
import { setupServer } from 'msw/node'

const server = setupServer(
  http.get('/api/todos', () => {
    return HttpResponse.json([{ id: '1', title: 'Mocked' }])
  })
)

beforeAll(() => server.listen())
afterEach(() => server.resetHandlers())
afterAll(() => server.close())
```

## Setup / Teardown
```ts
beforeEach(() => {
  // Reset mocks, seed data
  vi.clearAllMocks()
})

afterEach(() => {
  cleanup()
})
```

## Coverage Targets
- Statements: 70-80%
- Branches: 70-80%
- Functions: 70-80%
- Lines: 70-80%
- Don't chase 100% — diminishing returns past 80%

## What to Test
- Component renders with required props
- Component renders different states (loading, error, empty, success)
- User interactions (click, type, submit)
- Side effects (API calls, navigation)
- Edge cases (empty array, null, very long strings)

## What NOT to Test
- Implementation details (private methods, internal state)
- Third-party libraries (they have their own tests)
- Constants and types (TypeScript checks these)
- Styling (visual regression testing is separate)

## Forbidden Patterns
- Testing implementation details (`instance.state`, private methods)
- `wrapper.find('MyComponent')` (enzyme-style, fragile)
- Snapshot tests for components (use specific assertions)
- Mocking everything (defeats the purpose of integration testing)
- Testing the mock instead of the behavior
- `screen.debug()` left in tests

## Output Format
1. Test file
2. Component being tested (if applicable)
3. Mocks / setup
4. Coverage report

