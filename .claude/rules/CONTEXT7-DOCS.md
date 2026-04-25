---
description: REQUIRED — fetch latest official documentation before writing code for any language, framework, library, or package.
paths:
  - "**/*"
---

# Universal Research-First Rule

## When to activate

**ALWAYS** before writing, editing, or advising on code that involves any external dependency — library, framework, SDK, API, or package — in any programming language.

## Rule

**[CRITICAL — NON-NEGOTIABLE]**: You MUST NOT generate code from memory or static training data. Use `mcp__context7__resolve-library-id` and `mcp__context7__query-docs` to retrieve the latest API references, implementation patterns, and syntax BEFORE writing any code.

### Required workflow (strict sequence)

For every request involving a technology or library:

1. **Resolve** — `mcp__context7__resolve-library-id` to get the exact library ID.
2. **Fetch** — `mcp__context7__query-docs` to retrieve current documentation for the specific component or function needed.
3. **Analyze** — read the result; identify breaking changes, new patterns, or deprecated APIs.
4. **Implement** — only after completing steps 1–3.

## Why this rule exists

- **Version drift**: Training data lags behind reality. Libraries ship breaking changes continuously.
- **Hallucination prevention**: Stops the model from inventing APIs, props, or methods that don't exist in the current version.
- **Best practices drift**: Last year's recommended pattern may be today's anti-pattern.

## Exceptions (the only cases where fetching docs may be skipped)

1. The exact pattern already exists in the file or directory you're working in — follow the internal convention.
2. The task is pure algorithmic logic with no external library dependency (e.g., sorting, string formatting).
3. The user has explicitly provided a code snippet or documentation excerpt in the prompt.
