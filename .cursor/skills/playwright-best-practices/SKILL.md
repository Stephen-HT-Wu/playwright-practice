---
name: playwright-best-practices
description: Playwright testing best practices for this repo (stable locators, isolation, assertions, mocking, and debugging workflows). Use when writing or refactoring tests here.
---

# Playwright best practices (this repo)

Source reference: [Playwright Best Practices](https://playwright.dev/docs/best-practices)

## Core principles

- **Test user-visible behavior**: interact with what a user would see/do, not implementation details.
- **Keep tests isolated**: each test must run independently and be reproducible.
- **Avoid testing third-party dependencies**: prefer mocking network responses for anything you don’t control.

## Locators (priority order)

- **Prefer user-facing locators**:
  - `page.getByRole(...)`
  - `page.getByLabel(...)`
  - `page.getByText(...)` (use carefully; avoid overly broad matches)
- **Avoid brittle selectors**:
  - CSS classes that may change
  - XPath
  - deep DOM structure selectors

## Assertions

- **Use web-first assertions (auto-waiting)**:
  - ✅ `await expect(locator).toBeVisible()`
  - ✅ `await expect(page).toHaveURL(...)`
  - ✅ `await expect(page).toHaveTitle(...)`
- **Avoid manual “instant” checks**:
  - ❌ `expect(await locator.isVisible()).toBe(true)` (no auto-wait)

## Waiting & timing

- **Never use `waitForTimeout` for stability** unless there is truly no better signal.
- **Wait on real conditions** (URL, title, visibility, request completion, etc.) using `expect(...)`.

## Setup & reuse

- Use `test.beforeEach` for shared, per-test setup (e.g., navigate to a baseline page).
- Prefer a little duplication over hidden coupling when it keeps tests clearer and independent.

## Network: don’t depend on the outside world

- If a test must call an external service you don’t control, **mock it** with `page.route(...)`.
- For learning/examples, it’s okay to hit public pages, but treat those tests as **potentially flaky**.

## Debugging workflows (pnpm)

- Run all tests: `pnpm test`
- Single spec: `pnpm exec playwright test tests/<name>.spec.ts`
- Filter by title: `pnpm exec playwright test -g "<title substring>"`
- Headed mode: `pnpm exec playwright test --headed`
- UI mode: `pnpm exec playwright test --ui`
- Inspector debug: `pnpm exec playwright test --debug`
- Trace locally: `pnpm exec playwright test --trace on`
- Open trace: `pnpm exec playwright show-trace test-results/**/trace.zip`
