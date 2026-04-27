# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Claystack — design-first personal web platform. Three public surfaces sharing one design system:

| Subdomain             | App                 | Repo           |
| --------------------- | ------------------- | -------------- |
| `claystack.dev`       | Landing / portfolio | `apps/landing` |
| `tools.claystack.dev` | Utility tools       | `apps/tools`   |
| `blog.claystack.dev`  | Blog                | `apps/blog`    |

## Architecture

Monorepo — pnpm workspaces + Turborepo — with 5 git submodules:

```
apps/
  landing/   → claystack-landing   (Next.js 16)
  tools/     → claystack-tools     (Next.js 16)
  blog/      → claystack-blog      (Next.js 16)
  api/       → claystack-api       (.NET 10, Clean Architecture + DDD + CQRS)
packages/
  ui/        → claystack-ui        (@claystack/ui — shared design system)
```

## Development

```bash
pnpm install        # install all workspace deps
pnpm dev            # run all apps in dev mode (Turborepo)
pnpm build          # build all apps
pnpm lint           # lint all
pnpm typecheck      # typecheck all
```

Working in a single submodule:

```bash
cd apps/landing && pnpm dev
```

Submodule commits must be pushed inside the submodule first, then the root pointer bumped in a separate commit.

## Design System

`DESIGN.md` at root is the authoritative design system spec (394 lines, 9 sections, "Clay Craft × Stack Forward" identity). **Read it before any visual changes.** Signature interaction is **Stack Lift** on hover (`translateY(-3px)` + revealed two-layer swatch offset shadow) — never use a tilted/`rotateZ` hover.

Shared implementation lives in `packages/ui` (`@claystack/ui`):

- Design tokens: Tailwind v4 `@theme` directives in `src/styles/theme.css` (warm-cream canvas + named swatch palette + Be Vietnam Pro/Space Mono type scale + clay/stack-lift shadows).
- Components: Button (3 variants), Card (4 variants), StackCard, Input, Nav, SpecLabel, SpecBadge, SpecButton, StackStripe, GridWatermark.
- All Next.js apps import `@claystack/ui` as `"workspace:*"` and load `theme.css` via `globals.css` (with `@source "../../../packages/ui/src"` so Tailwind v4 scans the package).
- Both fonts load via `next/font/google` — no local files needed. Be Vietnam Pro (`variable: '--font-be-vietnam-pro'`) with `vietnamese` subset for i18n; Space Mono for mono metadata.

<!-- code-review-graph MCP tools -->

## MCP Tools: code-review-graph

**IMPORTANT: This project has a knowledge graph. ALWAYS use the
code-review-graph MCP tools BEFORE using Grep/Glob/Read to explore
the codebase.** The graph is faster, cheaper (fewer tokens), and gives
you structural context (callers, dependents, test coverage) that file
scanning cannot.

### When to use graph tools FIRST

- **Exploring code**: `semantic_search_nodes` or `query_graph` instead of Grep
- **Understanding impact**: `get_impact_radius` instead of manually tracing imports
- **Code review**: `detect_changes` + `get_review_context` instead of reading entire files
- **Finding relationships**: `query_graph` with callers_of/callees_of/imports_of/tests_for
- **Architecture questions**: `get_architecture_overview` + `list_communities`

Fall back to Grep/Glob/Read **only** when the graph doesn't cover what you need.

### Key Tools

| Tool                        | Use when                                               |
| --------------------------- | ------------------------------------------------------ |
| `detect_changes`            | Reviewing code changes — gives risk-scored analysis    |
| `get_review_context`        | Need source snippets for review — token-efficient      |
| `get_impact_radius`         | Understanding blast radius of a change                 |
| `get_affected_flows`        | Finding which execution paths are impacted             |
| `query_graph`               | Tracing callers, callees, imports, tests, dependencies |
| `semantic_search_nodes`     | Finding functions/classes by name or keyword           |
| `get_architecture_overview` | Understanding high-level codebase structure            |
| `refactor_tool`             | Planning renames, finding dead code                    |

### Workflow

1. The graph auto-updates on file changes (via hooks).
2. Use `detect_changes` for code review.
3. Use `get_affected_flows` to understand impact.
4. Use `query_graph` pattern="tests_for" to check coverage.

<!-- rtk-instructions v2 -->
<!-- RTK command reference moved to .claude/rules/RTK-COMMANDS.md (loaded every session) -->
<!-- /rtk-instructions -->

## Coding Standards (mandatory)

Production-ready coding rules for every TS/React/Next.js edit live in `.claude/rules/CODING-STANDARDS.md` (auto-loaded each session — non-negotiable). Five sections: TypeScript & Type Safety, Performance & Architecture (RSC default, `next/image`, CLS), Accessibility (WCAG 2.2 AA), Coding Style & Clean Code, Security.

Mechanically enforced by:

- **ESLint flat config** at root (`eslint.config.mjs`) — `next/core-web-vitals`, `next/typescript`, type-aware `recommendedTypeChecked`, `eslint-plugin-better-tailwindcss` (Tailwind v4), strict `react/no-danger`, `@next/next/no-img-element`, `react/jsx-no-target-blank`, `no-console`, `@typescript-eslint/no-explicit-any` and `no-unsafe-*`.
- **Prettier** + `prettier-plugin-tailwindcss` (`prettier.config.mjs`).
- **Pre-commit hook** via `simple-git-hooks` + `lint-staged` runs `code-review-graph detect-changes --brief && pnpm lint-staged` — every staged file is formatted + linted before commit.
- **CI** via `.github/workflows/ci.yml` runs `format:check`, `lint`, `typecheck`, `build` on every PR and push to `main`.

Useful scripts: `pnpm format`, `pnpm format:check`, `pnpm lint`, `pnpm lint:fix`, `pnpm typecheck`, `pnpm build`.
