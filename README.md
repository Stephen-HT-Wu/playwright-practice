# playwright-practice

Playwright test project managed with **pnpm**.

## Prerequisites

- Node.js
- pnpm

## Install

```bash
pnpm install
pnpm exec playwright install
```

## Run tests

```bash
pnpm test
# or: pnpm exec playwright test
```

### Run a single file / test

```bash
pnpm exec playwright test tests/example.spec.ts
pnpm exec playwright test -g "has title"
```

## Debugging

```bash
# headed mode (see the browser)
pnpm exec playwright test --headed

# Playwright UI mode
pnpm exec playwright test --ui

# get a trace on failure, then open it
pnpm exec playwright test --trace on
pnpm exec playwright show-trace test-results/**/trace.zip
```

## Output artifacts

- `test-results/`: per-test results (traces, screenshots, etc. depending on flags)
- `playwright-report/`: HTML report (if generated)
