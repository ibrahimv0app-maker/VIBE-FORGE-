---
name: ci-cd-github-actions-architect
description: Use when setting up CI/CD with GitHub Actions — test, lint, build, deploy. Always uses caching, parallel jobs, matrix builds, and proper secret management.
---

# CI/CD GitHub Actions Architect

CI should be: fast, reliable, secure, and give actionable feedback.

## Standard Workflow
```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

concurrency:
  group: ci-${{ github.ref }}
  cancel-in-progress: true

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm run lint
      - run: npm run typecheck

  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm run test:coverage
      - uses: codecov/codecov-action@v4

  build:
    needs: [lint, test]
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-artifact@v4
        with:
          name: build
          path: dist/

  e2e:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npx playwright install --with-deps chromium
      - run: npm run e2e
      - uses: actions/upload-artifact@v4
        if: failure()
        with:
          name: playwright-report
          path: playwright-report/
```

## Deploy Workflow
```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    needs: [build]
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v4
      - uses: actions/download-artifact@v4
        with:
          name: build
          path: dist/
      - name: Deploy
        env:
          VERCEL_TOKEN: ${{ secrets.VERCEL_TOKEN }}
        run: |
          npm i -g vercel
          vercel --prod --token $VERCEL_TOKEN
```

## Caching
```yaml
# Node modules cache (built-in to setup-node)
- uses: actions/setup-node@v4
  with:
    node-version: 20
    cache: npm   # automatic

# Next.js build cache
- uses: actions/cache@v4
  with:
    path: |
      .next/cache
    key: ${{ runner.os }}-nextjs-${{ hashFiles('**/package-lock.json') }}-${{ hashFiles('**.[jt]s', '**.[jt]sx') }}
    restore-keys: |
      ${{ runner.os }}-nextjs-
```

## Matrix Build
```yaml
strategy:
  matrix:
    node: [18, 20, 22]
    os: [ubuntu-latest, macos-latest, windows-latest]
runs-on: ${{ matrix.os }}
steps:
  - uses: actions/setup-node@v4
    with:
      node-version: ${{ matrix.node }}
```

## Environment Secrets
```yaml
jobs:
  deploy-staging:
    runs-on: ubuntu-latest
    environment: staging  # requires approval if configured
    steps:
      - run: deploy --api-key ${{ secrets.STAGING_API_KEY }}
```

## Concurrency
```yaml
concurrency:
  group: pr-${{ github.event.pull_request.number }}
  cancel-in-progress: true
```
Cancel old runs when a new commit is pushed — saves CI minutes.

## Job Dependencies
```yaml
jobs:
  a:
    ...
  b:
    needs: a   # wait for a
  c:
    needs: [a, b]  # wait for both
  d:
    if: failure()  # only if a, b, or c failed
    needs: [a, b, c]
```

## Conditional Steps
```yaml
- if: github.ref == 'refs/heads/main'
  run: deploy --prod

- if: github.event_name == 'pull_request'
  run: deploy --preview
```

## Performance Tips
- Use `cancel-in-progress` to kill old PR runs
- Cache dependencies
- Run lint, test, build in parallel (not sequentially)
- Use smaller base images for Docker builds
- Don't run e2e on every commit (only on PRs to main)
- Use `actions/cache@v4` aggressively

## Security
- Never echo secrets
- Use `secrets.GITHUB_TOKEN` for API calls (auto-provided)
- Pin actions to a SHA: `uses: actions/checkout@<sha>` (not `@v4`)
- Use `environment` for protected deploys
- Audit third-party actions

## Forbidden Patterns
- No caching (slow CI)
- Sequential jobs when parallel is possible
- Secrets in `env` at workflow level (use job level)
- `@v4` (mutable tag) for security-sensitive actions
- No `cancel-in-progress` (wasted CI minutes)
- Long-running e2e on every commit

## Output Format
1. Workflow YAML
2. Required secrets list
3. Branch protection recommendations
4. CI runtime estimate

