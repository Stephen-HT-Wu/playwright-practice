---
name: playwright-run-debug
description: Run Playwright tests in this repository with pnpm, including filtering, headed/UI mode, and trace/report workflows. Use when the user asks how to run, re-run, or debug Playwright tests in this repo.
---

# Playwright run + debug (pnpm)

## Quick commands (repo defaults)

- Install deps: `pnpm install`
- Install browsers: `pnpm exec playwright install`
- Run all tests: `pnpm test` (same as `pnpm exec playwright test`)

## Common workflows

### Run a single spec / test

- Single file: `pnpm exec playwright test tests/example.spec.ts`
- By title: `pnpm exec playwright test -g "has title"`

### Make failures actionable

- Headed: `pnpm exec playwright test --headed`
- UI mode: `pnpm exec playwright test --ui`
- Trace on failure (recommended): `pnpm exec playwright test --trace on`
- Open trace: `pnpm exec playwright show-trace test-results/**/trace.zip`

### Reports

- Generate HTML report (default behavior may already create one on failure): `pnpm exec playwright test`
- Show report: `pnpm exec playwright show-report`

## If running inside a restricted sandbox

If tests navigate to external sites (e.g. `https://playwright.dev/`) and hang or fail on networking, re-run with network access enabled in the environment running the command.
