---
name: playwright-e2e-testing-architect
description: Use when writing end-to-end tests with Playwright. Always follows page object model, parallel execution, and tests real user flows.
---

# Playwright E2E Testing Architect

E2E tests are expensive. Reserve them for critical user flows.

## What to E2E Test
- Signup / login / logout
- Core user journey (the thing that makes you money)
- Checkout / payment
- Critical error paths (failed payment, expired session)

## What NOT to E2E Test
- Component-level behavior (unit / integration)
- Styling (visual regression)
- Edge cases (too slow)
- Every CRUD operation (test the critical path, not every combo)

## Setup
```ts
// playwright.config.ts
import { defineConfig, devices } from '@playwright/test'

export default defineConfig({
  testDir: './e2e',
  fullyParallel: true,
  retries: process.env.CI ? 2 : 0,
  workers: process.env.CI ? 1 : undefined,
  reporter: 'html',
  use: {
    baseURL: process.env.BASE_URL || 'http://localhost:3000',
    trace: 'on-first-retry',
    screenshot: 'only-on-failure',
    video: 'retain-on-failure',
  },
  projects: [
    { name: 'chromium', use: { ...devices['Desktop Chrome'] } },
    { name: 'firefox', use: { ...devices['Desktop Firefox'] } },
    { name: 'webkit', use: { ...devices['Desktop Safari'] } },
    { name: 'mobile-chrome', use: { ...devices['Pixel 5'] } },
  ],
})
```

## Test Structure
```ts
import { test, expect } from '@playwright/test'
{ LoginPage } from './pages/LoginPage'

test.describe('Authentication', () => {
  test('user can log in with valid credentials', async ({ page }) => {
    const loginPage = new LoginPage(page)
    await loginPage.goto()
    await loginPage.fillEmail('test@example.com')
    await loginPage.fillPassword('password123')
    await loginPage.submit()
    await expect(page).toHaveURL('/dashboard')
    await expect(page.getByRole('heading', { name: /welcome/i })).toBeVisible()
  })

  test('shows error with invalid credentials', async ({ page }) => {
    const loginPage = new LoginPage(page)
    await loginPage.goto()
    await loginPage.fillEmail('test@example.com')
    await loginPage.fillPassword('wrong')
    await loginPage.submit()
    await expect(page.getByText(/invalid email or password/i)).toBeVisible()
  })
})
```

## Page Object Model
```ts
// e2e/pages/LoginPage.ts
import { Page, Locator } from '@playwright/test'

export class LoginPage {
  readonly page: Page
  readonly emailInput: Locator
  readonly passwordInput: Locator
  readonly submitButton: Locator

  constructor(page: Page) {
    this.page = page
    this.emailInput = page.getByLabel(/email/i)
    this.passwordInput = page.getByLabel(/password/i)
    this.submitButton = page.getByRole('button', { name: /sign in/i })
  }

  async goto() {
    await this.page.goto('/login')
  }

  async fillEmail(email: string) {
    await this.emailInput.fill(email)
  }

  async fillPassword(password: string) {
    await this.passwordInput.fill(password)
  }

  async submit() {
    await this.submitButton.click()
  }
}
```

## Test Fixtures
```ts
// e2e/fixtures/auth.ts
import { test as base, expect } from '@playwright/test'

type AuthFixture = {
  authenticatedPage: Page
}

export const test = base.extend<AuthFixture>({
  authenticatedPage: async ({ page }, use) => {
    // Login via API for speed
    await page.request.post('/api/auth/login', {
      data: { email: 'test@example.com', password: 'password' },
    })
    await page.goto('/')
    await use(page)
  },
})
```

## Authentication State Reuse
```ts
// Save auth state once, reuse for all tests
test('authenticate', async ({ page }) => {
  await page.goto('/login')
  await page.fill('input[name="email"]', 'test@example.com')
  await page.fill('input[name="password"]', 'password')
  await page.click('button[type="submit"]')
  await page.context().storageState({ path: 'e2e/.auth/user.json' })
})

// In other tests:
test.use({ storageState: 'e2e/.auth/user.json' })
```

## Selectors (in order of preference)
1. `getByRole` — accessibility-first
2. `getByLabel` — form fields
3. `getByPlaceholder`
4. `getByText`
5. `getByTestId` — last resort

## Auto-Waiting
Playwright auto-waits for elements to be:
- Visible
- Stable (not animating)
- Receives events
- Enabled

You rarely need explicit waits. If you do, use:
```ts
await expect(page.getByText('Loaded')).toBeVisible({ timeout: 10_000 })
```

## Network Mocking
```ts
await page.route('**/api/todos', async (route) => {
  await route.fulfill({ json: [{ id: '1', title: 'Mocked' }] })
})

// Abort requests to third parties
await page.route('**/*.{png,jpg,jpeg}', (route) => route.abort())
```

## Visual Regression
```ts
await expect(page).toHaveScreenshot('login.png', {
  maxDiffPixelRatio: 0.01,
})
```

## Parallelism
- Tests run in parallel by default
- Use `test.describe.configure({ mode: 'serial' })` for tests that must run in order
- Use separate worker processes for state isolation

## CI Setup
- Run on every PR
- Run on staging before deploy
- Don't run on every commit locally (too slow)

## Forbidden Patterns
- `page.waitForTimeout(1000)` — flaky, use auto-waiting or `expect`
- CSS selectors (`page.$('.my-class')`) — fragile
- Testing the same flow in multiple tests (DRY it up)
- E2E tests for unit-level behavior
- Not isolating state between tests

## Output Format
1. Test file
2. Page objects
3. Fixtures (if any)
4. CI config

