# Claystack Coding Standards (Production-Ready, Non-Negotiable)

**[CRITICAL — APPLY EVERY EDIT/WRITE]**: These rules apply to every line of TypeScript / TSX / React you generate or modify in the Claystack monorepo (`apps/landing`, `apps/tools`, `apps/blog`, `packages/ui`). Violating them is a regression. ESLint + tsc + pre-commit hook + CI mechanically enforce most of these — your job is to write code that passes the first time, not to wait for the linter to find it.

> Companion rules already loaded: `RTK-COMMANDS.md` (token-cheap shell), `CONTEXT7-DOCS.md` (fetch docs before coding any external dep). Visual decisions: read `DESIGN.md` at repo root.

---

## 1. TypeScript & Type Safety

- **MUST NOT** use `any`. If a value is genuinely unknown at the boundary, type it `unknown` and narrow with a type guard or schema.
- **MUST NOT** silence the compiler with `@ts-ignore` or `@ts-expect-error` without a description: only `@ts-expect-error: <reason>` is acceptable, and only when the alternative would force a real `any`.
- **MUST** declare an `interface` or `type` for: component props, hook return values, function arguments / returns crossing module boundaries, and every API request / response shape.
- **MUST** prefer utility types over duplication: `Pick`, `Omit`, `Partial`, `Required`, `Record`, `ReturnType`, `Parameters`. Re-derive — don't re-declare.
- **MUST** preserve end-to-end type safety when interacting with `apps/api`: generate types from the .NET OpenAPI surface or share a Zod schema; never hand-write a duplicate model.
- **MUST** enable `noUncheckedIndexedAccess` semantics: array / record reads return `T | undefined` — handle both branches.
- **MUST** export prop types alongside the component (`export interface ButtonProps {...}`) so consumers can extend them.

```ts
// ✅
interface ParseResult { ok: true; value: number } | { ok: false; error: string }
function parseAge(input: unknown): ParseResult { ... }

// ❌
function parseAge(input: any): any { ... }
```

---

## 2. Performance & Architecture (Core Web Vitals 2026)

- **DEFAULT** every component is a Server Component. **MUST NOT** add `"use client"` unless the file actually requires: an event handler, a React hook, a browser-only API, or third-party client component composition.
- **MUST** annotate every `"use client"` directive with a comment on the same line stating the trigger: `"use client"; // useState for form state`. No vague reasons.
- **MUST** use `next/image` with `width` + `height` (or `fill` + sized parent) for every raster asset. Set `priority` only for above-the-fold LCP candidates.
- **MUST NOT** use `<img>`. ESLint blocks it (`@next/next/no-img-element`). The only exception is `<img>` on an `<svg>` reference for inline icons — and even then, prefer `lucide-react`.
- **MUST** preserve format negotiation: rely on Next's default AVIF + WebP delivery; do not pin to JPEG/PNG.
- **MUST** prevent CLS: every media / iframe / dynamic block ships with explicit `width`/`height` or a sized skeleton. Reserve space — don't pop content in.
- **MUST** code-split anything heavy and rarely-used via `next/dynamic` with `ssr: false` only when justified (browser-only library).
- **MUST** keep client bundles small: import named symbols (`import { Button } from "@claystack/ui"` — already barrel; avoid pulling whole `lodash`).
- **MUST** mark `Card`/`Button`/`Nav` and similar `@claystack/ui` primitives as Server Components in the package — only `Nav.tsx` is allowed to be `"use client"` (mobile drawer state).

```tsx
// ✅
import Image from "next/image";
<Image src="/hero.png" alt="" width={1200} height={600} priority />

// ❌
<img src="/hero.png" />
```

---

## 3. Accessibility (WCAG 2.2 AA)

- **MUST** use semantic HTML first. `<button>` for actions, `<a>` for navigation, `<main>` once per route, `<nav>` for nav, `<article>` for self-contained content, `<section>` with a heading, `<dialog>` for modals (or a Headless library that wires ARIA correctly).
- **MUST NOT** put `onClick` on a `<div>` or `<span>` to make it act like a button. Use `<button type="button">`.
- **MUST** label every interactive element: visible text, `aria-label`, or `aria-labelledby`. Inputs require an associated `<label htmlFor>` — `aria-label` is a fallback, not a default.
- **MUST** provide a visible `:focus-visible` ring on every focusable element. Never `outline: none` without a replacement.
- **MUST** be fully operable via keyboard: every interactive element reachable via Tab, every dialog traps focus, Esc closes overlays, Enter / Space activate buttons.
- **MUST** meet contrast: 4.5:1 for body text, 3:1 for large text and UI controls. Cross-check against `DESIGN.md` swatches before pairing colors.
- **MUST** add `alt=""` (decorative) or descriptive `alt` text to every `<Image>`. Empty string is intentional, not lazy.
- **MUST** set `lang` on `<html>` (already in `app/layout.tsx`); don't strip it.
- **MUST** add `rel="noreferrer"` (or `noopener`) to every `target="_blank"` anchor.

```tsx
// ✅
<button type="button" onClick={open} aria-label="Open menu">
  <Menu className="size-5" aria-hidden="true" />
</button>

// ❌
<div onClick={open}><Menu /></div>
```

---

## 4. Coding Style & Clean Code

- **PREFER** declarative over imperative: `array.map / filter / reduce / find` over mutating `for` loops; ternary or early-return over deeply nested `if`.
- **MUST** separate business logic from UI:
  - Reusable client logic → custom hooks under `app/hooks/` (or `src/hooks/` for the package).
  - Pure functions / formatters → `app/lib/` (or `src/lib/`).
  - Server-only data access → server functions (`"use server"` action or RSC fetch in a `lib/` module).
- **MUST** follow Single Responsibility: one component owns one concern. If a component renders > ~150 LOC or a hook > ~80 LOC, split it.
- **MUST NOT** repeat yourself across components for the same construct — extract a primitive into `@claystack/ui` if it's used by 2+ apps.
- **MUST NOT** introduce abstractions speculatively. Three real call sites first, then refactor. Don't pre-build options for hypothetical future variants.
- **MUST** name things by intent, not type: `useCartTotal`, not `useNumber`; `submitForm`, not `handleClick`. Booleans get an `is/has/can/should` prefix.
- **MUST NOT** leave `console.log` in committed code. `console.warn` and `console.error` are OK for genuine error paths.
- **MUST NOT** comment what the code does — only why, when the why is non-obvious. Identifiers carry the what.

---

## 5. Security

- **MUST** treat every value crossing a system boundary (URL params, form data, headers, third-party API responses, MDX frontmatter) as untrusted. Validate with Zod or an explicit type guard before use.
- **MUST NOT** use `dangerouslySetInnerHTML`. The only exception is sanitized MDX/HTML output passed through DOMPurify (or `isomorphic-dompurify` in RSC) — and the line MUST carry an inline comment naming the sanitizer:

  ```tsx
  // sanitized via isomorphic-dompurify
  <div dangerouslySetInnerHTML={{ __html: clean }} />
  ```

  ESLint blocks `react/no-danger` by default; you must add a per-line `// eslint-disable-next-line react/no-danger` together with the sanitizer comment.

- **MUST NOT** interpolate untrusted strings directly into `href`, `src`, `style`, or any HTML attribute. Use `URL` parsing or whitelist schemes. Never accept `javascript:` URIs.
- **MUST NOT** log secrets, tokens, cookies, or full request/response bodies. Redact before logging.
- **MUST NOT** hardcode secrets, API keys, or credentials. Use `process.env.*` (server-only) and never expose them with `NEXT_PUBLIC_` unless they are genuinely public.
- **MUST** set `rel="noreferrer noopener"` for every `target="_blank"` (also a11y rule above — same defense surface).
- **MUST NOT** disable React's built-in escaping. Don't use `eval`, `new Function()`, or `Function.prototype.constructor`.

---

## Exceptions

If a rule is genuinely impossible to satisfy in a specific spot, document the exception inline:

```ts
// rule-exception: <rule-id> — <one-line reason>
```

`<rule-id>` is either an ESLint rule name or a section number from this file (e.g. `S5-no-danger`). Without that comment the rule wins.

---

## Pre-edit checklist (apply before every Edit/Write)

1. Is this file a Server Component? Default yes. Only add `"use client"` with on-line justification.
2. Did I introduce `any`, `<img>`, `dangerouslySetInnerHTML`, or `console.log`? Stop and fix before saving.
3. Does every interactive element have a label, focus-visible, and keyboard support?
4. Did I declare types for every prop/return/API shape?
5. Did I follow `DESIGN.md` for visuals (Stack Lift, swatch palette, no rotation)?

If any answer is "no", revise before the file leaves your tool call.
