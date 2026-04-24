---
name: playwright-add-test
description: Add or update Playwright tests in this repository using @playwright/test conventions and pnpm scripts. Use when the user asks to create a new spec, extend coverage, or refactor Playwright tests here.
---

# Add / update Playwright tests (repo conventions)

## Where to put tests

- Create specs under `tests/`, named `*.spec.ts`.

## Default imports

Use the test runner from `@playwright/test`:

```ts
import { test, expect } from '@playwright/test';
```

## Fast iteration commands

- Run only the spec you’re editing: `pnpm exec playwright test tests/<name>.spec.ts`
- Run a single test by title: `pnpm exec playwright test -g "<title substring>"`
- Debug interactively: `pnpm exec playwright test --ui`

## Reliability guidelines

- Prefer role/label-based locators: `getByRole`, `getByLabel`, `getByText`
- Add assertions that wait for the right state: `toBeVisible`, `toHaveURL`, `toHaveTitle`
- Avoid `waitForTimeout` unless there is no better signal
