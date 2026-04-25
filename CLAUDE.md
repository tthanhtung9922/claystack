# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Claystack — design-first personal web platform. Three public surfaces sharing one design system:

| Subdomain | App | Repo |
|-----------|-----|------|
| `claystack.dev` | Landing / portfolio | `apps/landing` |
| `tools.claystack.dev` | Utility tools | `apps/tools` |
| `blog.claystack.dev` | Blog | `apps/blog` |

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

`DESIGN.md` at root is the authoritative design system spec (403 lines). **Read it before any visual changes.**

Shared implementation lives in `packages/ui` (`@claystack/ui`):
- Design tokens: Tailwind v4 `@theme` directives mapping DESIGN.md exactly
- Components: Button (3 variants), Card, StackCard, FiringStatePill, KilnRibbon, StrataDivider, Input, Nav
- All Next.js apps import `@claystack/ui` as `"workspace:*"` and load `theme.css` via `globals.css`

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

| Tool | Use when |
|------|----------|
| `detect_changes` | Reviewing code changes — gives risk-scored analysis |
| `get_review_context` | Need source snippets for review — token-efficient |
| `get_impact_radius` | Understanding blast radius of a change |
| `get_affected_flows` | Finding which execution paths are impacted |
| `query_graph` | Tracing callers, callees, imports, tests, dependencies |
| `semantic_search_nodes` | Finding functions/classes by name or keyword |
| `get_architecture_overview` | Understanding high-level codebase structure |
| `refactor_tool` | Planning renames, finding dead code |

### Workflow

1. The graph auto-updates on file changes (via hooks).
2. Use `detect_changes` for code review.
3. Use `get_affected_flows` to understand impact.
4. Use `query_graph` pattern="tests_for" to check coverage.
