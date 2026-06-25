# OMO Book Pages QA

## What Was Tested

- Static site generation for `course/book-omo-ko`.
- Internal HTML links across the generated book.
- Current fork source-path correction from old `src/...` references to `packages/omo-opencode/src/...`.
- Local HTTP serving for the generated static site.
- Browser rendering in system Google Chrome through Playwright on desktop and mobile viewports.

## What Was Observed

- `01-build.txt`: generator produced 47 pages from the copied `book-omo-ko` source.
- `02-internal-links.txt`: generated HTML page count is 47 and broken internal links are 0.
- `03-source-resolution.txt`: generated pages include GitHub source links and current fork path mentions; unresolved references are preserved as non-404 text.
- `04-local-http.txt`: root, 1장, 26장, and 부록 H returned HTTP 200 locally; 1장 includes the current fork correction and source reference sections.
- `05-browser-check.json`: desktop pages and mobile 1장 render without horizontal overflow; representative pages include the fork correction note and source links.

## Why It Is Enough

This change does not touch OpenCode/Codex runtime code, package source, hooks, tools, agents, MCPs, config schemas, installers, or CLI behavior. The relevant risk is static-site correctness: generation reproducibility, navigation, source-link correctness, and readable rendering. The evidence covers those surfaces directly.

## What Was Omitted

- `opencode-qa` and `codex-qa` were not run because no OpenCode/Codex-connected runtime component was changed.
- Full package `bun test`, `bun run typecheck`, and `bun run build` were not run because the change is an isolated static course site under `course/book-omo-ko` and does not affect package compilation.
