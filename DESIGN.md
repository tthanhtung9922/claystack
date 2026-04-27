# Claystack Design System — Clay Craft × Stack Forward

> **The dual identity.** Claystack pairs Clay's warm, hand-made craft language with a Stack-forward sensibility — layered, technical, modern, future-facing. The cream canvas, food-named swatches, and Be Vietnam Pro character stay intact. Space Mono is elevated to co-equal status. The signature interaction is no longer a playful tilt, but a deliberate **Stack Lift** — a button that rises and reveals layered swatch shadows beneath it, like papers stacked on a desk.

## 1. Visual Theme & Atmosphere

Claystack's surface is a warm, playful celebration of color that treats every product moment like a craft — not an enterprise chore. The foundation is warm cream (`#faf9f7`) and oat-toned borders (`#dad4c8`, `#eee9df`) that give every surface the tactile quality of handmade paper. Against this artisanal canvas, a vivid swatch palette explodes with personality — Matcha, Slushie, Lemon, Ube, Pomegranate, Blueberry, Dragonfruit — each named like flavors at a juice bar, not colors in an enterprise UI kit.

The typography is anchored by **Be Vietnam Pro**, a warm geometric sans-serif with Vietnamese-first glyph coverage, loaded via `next/font/google` at weights 400/500/600. At display scale (80px, weight 600), Be Vietnam Pro uses aggressive negative letter-spacing (-3.2px) that compresses headlines into punchy, billboard-like statements. **Space Mono** is the technical co-pilot — used not just for code but for spec labels (`[STACK:01]`), version tags (`v1.0.0`), build numbers (`BUILD 0426`), and any metadata that wants to feel precise, layered, and future-leaning. The Be Vietnam Pro + Space Mono pairing is the typographic embodiment of the brand: warm geometric character meets terminal precision.

The signature interaction — what makes Claystack feel like Claystack — is the **Stack Lift**. On hover, a button rises (`translateY(-3px)`) and reveals two offset swatch-colored shadow layers beneath it (`4px 4px 0 swatch-A, 8px 8px 0 swatch-B`). It looks like the button has been picked up off a stack of colored cards. This replaces Clay's tilted hover with a motion that's still physical, still playful, still hard-edged — but now reads as **layered, modern, forward-moving** instead of slanted. Combined with generously rounded containers (24px–40px radius), dashed borders alongside solid ones, a multi-layer shadow with inset highlight, and subtle 8px dot-grid watermarks on technical surfaces, Claystack feels made by people who genuinely enjoy making things — and who happen to ship software.

**Key Characteristics:**

- Warm cream canvas (`#faf9f7`) with oat-toned borders (`#dad4c8`) — artisanal, not clinical
- Named swatch palette: Matcha, Slushie, Lemon, Ube, Pomegranate, Blueberry, Dragonfruit
- Be Vietnam Pro — warm geometric, Vietnamese-first glyph coverage
- **Space Mono elevated** — spec labels, version tags, build numbers, code, all metadata
- **Stack Lift hover** — `translateY(-3px)` + revealed two-layer swatch shadow stack (no rotation)
- **Stack Stripe divider** — 3-line horizontal sediment, the brand's wayfinding mark
- **Spec Labels** — bracketed mono micro-text for technical voice (`[STACK:01]`, `v1.0.0`)
- **Grid Watermark** — subtle 8px dot-grid background on technical surfaces
- Generous border radius: 24px cards, 40px sections, 1584px pills
- Mixed border styles: solid + dashed in the same interface
- Multi-layer shadow with inset highlight: `0px 1px 1px` + `-1px inset` + `-0.5px`

## 2. Color Palette & Roles

### Primary

- **Clay Black** (`#000000`): Text, headings, default foreground
- **Stack Graphite** (`#1f1d1a`): Mono spec text — slight warm undertone, never pure black-on-cream
- **Pure White** (`#ffffff`): Card backgrounds, button backgrounds, inverse text
- **Warm Cream** (`#faf9f7`): Page background — the warm, paper-like canvas

### Swatch Palette — Named Colors with Stack Semantics

Each swatch carries a Stack-semantic role. Use the role to pick a color when status, state, or emphasis is being communicated; ignore the role and pick by aesthetic when it's purely decorative.

**Matcha (Green) — `signal · active · success`**

- **Matcha 300** (`#84e7a5`): light accent
- **Matcha 600** (`#078a52`): mid green — primary "active" tone
- **Matcha 800** (`#02492a`): deep green for dark sections

**Slushie (Cyan) — `info · build · live`**

- **Slushie 500** (`#3bd3fd`): bright cyan accent
- **Slushie 800** (`#0089ad`): deep teal

**Lemon (Gold) — `draft · warning · pending`**

- **Lemon 400** (`#f8cc65`): warm pale gold
- **Lemon 500** (`#fbbd41`): primary gold
- **Lemon 700** (`#d08a11`): deep amber
- **Lemon 800** (`#9d6a09`): dark amber

**Ube (Purple) — `process · compile · transform`**

- **Ube 300** (`#c1b0ff`): soft lavender
- **Ube 800** (`#43089f`): deep purple
- **Ube 900** (`#32037d`): darkest purple

**Pomegranate (Pink/Red) — `error · blocker · stop`**

- **Pomegranate 400** (`#fc7981`): warm coral-pink

**Blueberry (Navy Blue) — `archive · stable · shipped`**

- **Blueberry 800** (`#01418d`): deep navy

**Dragonfruit (Magenta) — `accent · highlight · new`**

- **Dragonfruit 300** (`#ff9ec7`): light pink accent
- **Dragonfruit 600** (`#f0177a`): hot magenta — primary highlight tone
- **Dragonfruit 800** (`#8a0047`): deep magenta for dark sections

### Neutral Scale (Warm)

- **Warm Silver** (`#9f9b93`): Secondary/muted text, footer links
- **Warm Charcoal** (`#55534e`): Tertiary text, dark muted links
- **Dark Charcoal** (`#333333`): Link text on light backgrounds

### Surface & Border

- **Oat Border** (`#dad4c8`): Primary border — warm, cream-toned structural lines
- **Oat Light** (`#eee9df`): Secondary lighter border
- **Cool Border** (`#e6e8ec`): Cool-toned border for contrast sections
- **Dark Border** (`#525a69`): Border on dark sections
- **Light Frost** (`#eff1f3`): Subtle button background (at 0% opacity on hover)
- **Grid Dot** (`rgba(85, 83, 78, 0.18)`): 8px dot-grid watermark on technical surfaces

### Badges & States

- **Badge Blue Bg** (`#f0f8ff`): Blue-tinted badge surface
- **Badge Blue Text** (`#3859f9`): Vivid blue badge text
- **Focus Ring** (`rgb(20, 110, 245) solid 2px`): Accessibility focus indicator

### Shadows

- **Clay Shadow** (`rgba(0,0,0,0.1) 0px 1px 1px, rgba(0,0,0,0.04) 0px -1px 1px inset, rgba(0,0,0,0.05) 0px -0.5px 1px`): Multi-layer with inset highlight — "pressed into clay" signature
- **Stack Lift** (`4px 4px 0 0 <swatch-A>, 8px 8px 0 0 <swatch-B>, rgba(0,0,0,0.08) 0px 2px 4px`): Hover state — two revealed swatch layers + soft contact shadow. Default swatch pairing: Lemon 400 + Ube 300, but any Matcha/Slushie/Pomegranate combination works for variant buttons.

## 3. Typography Rules

### Font Families

- **Primary**: `Be Vietnam Pro` — loaded via `next/font/google`, weights 400/500/600, `subsets: ['latin', 'latin-ext', 'vietnamese']`, `variable: '--font-be-vietnam-pro'`
- **Monospace**: `Space Mono` — co-equal in role, used for ALL technical metadata (spec labels, versions, builds, code, file paths, timestamps)

### Hierarchy

| Role              | Font           | Size               | Weight  | Line Height    | Letter Spacing     | Notes                                              |
| ----------------- | -------------- | ------------------ | ------- | -------------- | ------------------ | -------------------------------------------------- |
| Display Hero      | Be Vietnam Pro | 80px (5.00rem)     | 600     | 1.00 (tight)   | -3.2px             |                                                    |
| Display Secondary | Be Vietnam Pro | 60px (3.75rem)     | 600     | 1.00 (tight)   | -2.4px             |                                                    |
| Section Heading   | Be Vietnam Pro | 44px (2.75rem)     | 600     | 1.10 (tight)   | -0.88px to -1.32px |                                                    |
| Card Heading      | Be Vietnam Pro | 32px (2.00rem)     | 600     | 1.10 (tight)   | -0.64px            |                                                    |
| Feature Title     | Be Vietnam Pro | 20px (1.25rem)     | 600     | 1.40           | -0.4px             |                                                    |
| Sub-heading       | Be Vietnam Pro | 20px (1.25rem)     | 500     | 1.50           | -0.16px            |                                                    |
| Body Large        | Be Vietnam Pro | 20px (1.25rem)     | 400     | 1.40           | normal             |                                                    |
| Body              | Be Vietnam Pro | 18px (1.13rem)     | 400     | 1.60 (relaxed) | -0.36px            |                                                    |
| Body Standard     | Be Vietnam Pro | 16px (1.00rem)     | 400     | 1.50           | normal             |                                                    |
| Body Medium       | Be Vietnam Pro | 16px (1.00rem)     | 500     | 1.20–1.40      | -0.16px to -0.32px |                                                    |
| Button            | Be Vietnam Pro | 16px (1.00rem)     | 500     | 1.50           | -0.16px            |                                                    |
| Button Large      | Be Vietnam Pro | 24px (1.50rem)     | 400     | 1.50           | normal             |                                                    |
| Button Small      | Be Vietnam Pro | 12.8px (0.80rem)   | 500     | 1.50           | -0.128px           |                                                    |
| Nav Link          | Be Vietnam Pro | 15px (0.94rem)     | 500     | 1.60 (relaxed) | normal             |                                                    |
| Caption           | Be Vietnam Pro | 14px (0.88rem)     | 400     | 1.50–1.60      | -0.14px            |                                                    |
| Small             | Be Vietnam Pro | 12px (0.75rem)     | 400     | 1.50           | normal             |                                                    |
| Uppercase Label   | Be Vietnam Pro | 12px (0.75rem)     | 600     | 1.20 (tight)   | 1.08px             | `text-transform: uppercase`                        |
| **Spec Label**    | **Space Mono** | **11px (0.69rem)** | **400** | **1.20**       | **0.5px**          | **`text-transform: uppercase`, e.g. `[STACK:01]`** |
| **Version Tag**   | **Space Mono** | **12px (0.75rem)** | **400** | **1.20**       | **0**              | **e.g. `v1.0.0`, `BUILD 0426`**                    |
| **Code Inline**   | **Space Mono** | **0.92em**         | **400** | **inherit**    | **0**              | **Inline code in body text**                       |
| Badge             | Be Vietnam Pro | 9.6px              | 600     | —              | —                  | Pill badges                                        |

### Principles

- **Two-voice typography**: Be Vietnam Pro is warmth, character, narrative. Space Mono is precision, metadata, time. Use them deliberately — Be Vietnam Pro speaks, Mono labels.
- **Three-weight hierarchy as identity**: Weights 600/500/400 map strictly to headings/UI/body — `font-semibold` for headings, `font-medium` for UI elements, `font-normal` for body. Never deviate.
- **Aggressive display compression**: -3.2px at 80px, -2.4px at 60px alongside generous body line-height (1.60) creates dramatic contrast.
- **Weight 600 for headings, 500 for UI, 400 for body**: Three-tier system, strict roles.
- **Spec Label is the stack signature**: Bracketed Space Mono micro-text (`[STACK:01]`, `[v1.0.0]`) above headings or beside cards is the typographic mark of Claystack — never use plain uppercase Be Vietnam Pro when a spec label voice is wanted.

## 4. Component Stylings

### Buttons

**Primary (Solid with Stack Lift)**

- Background: `#000000`
- Text: `#ffffff`
- Padding: 12px 20px
- Border: none
- Radius: 12px (or 1584px pill for hero CTAs)
- Default shadow: `rgba(0,0,0,0.1) 0px 1px 1px, rgba(0,0,0,0.04) 0px -1px 1px inset` (clay shadow)
- **Hover (Stack Lift)**:
  - `transform: translateY(-3px)`
  - `box-shadow: 4px 4px 0 0 #f8cc65, 8px 8px 0 0 #c1b0ff, rgba(0,0,0,0.08) 0px 2px 4px`
  - Two revealed swatch layers (Lemon 400 → Ube 300) appear behind the button as if it lifted off a stack
  - `transition: transform 220ms cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 220ms ease-out` — slight overshoot spring
- Focus: `rgb(20, 110, 245) solid 2px` outline

**White Solid (Stack Lift on dark/swatch sections)**

- Background: `#ffffff`
- Text: `#000000`
- Padding: 12px 20px
- Radius: 12px
- Hover: same Stack Lift but with swatch pair Matcha 300 (`#84e7a5`) → Slushie 500 (`#3bd3fd`) — fresh on dark canvases
- Use: Primary CTA on swatch-colored sections

**Ghost Outlined**

- Background: transparent
- Text: `#000000`
- Padding: 10px 16px
- Border: `1px solid #717989`
- Radius: 4px
- Hover: `translateY(-2px)`, single-layer offset shadow `4px 4px 0 0 #fc7981` (Pomegranate 400) — quieter Stack Lift, only one layer revealed
- Use: Secondary actions

**Spec Button (Mono micro-CTA)**

- Background: transparent
- Text: `#1f1d1a` (Stack Graphite)
- Font: Space Mono 11px uppercase, letter-spacing 0.5px
- Padding: 6px 10px
- Border: `1px dashed #dad4c8`
- Radius: 4px
- Hover: border solid, background `#eee9df`, no Stack Lift — restraint signals it's a utility, not a hero action
- Use: "View source", "Read spec", "[v1.0.0]" — anywhere a button needs to whisper, not shout

### Cards & Containers

**Standard Card**

- Background: `#ffffff` on cream canvas
- Border: `1px solid #dad4c8` (warm oat) or `1px dashed #dad4c8` for secondary
- Radius: 12px (standard), 24px (feature), 40px (section)
- Shadow: `rgba(0,0,0,0.1) 0px 1px 1px, rgba(0,0,0,0.04) 0px -1px 1px inset, rgba(0,0,0,0.05) 0px -0.5px 1px`

**Stack Card** _(signature)_

- Spec Label at top: Space Mono 11px uppercase, `[STACK:NN]` or `[v1.0.0]`, color Warm Charcoal
- Be Vietnam Pro 32px weight 600 heading directly below, -0.64px tracking
- Body 16px Be Vietnam Pro below
- Optional thin Matcha 600 (`#078a52`) top accent line, 2px, full-width — marks the card as "active"
- Hover: Stack Lift (translateY(-3px) + 2-layer swatch shadow)
- Use: Feature highlights, product modules, anywhere a "module" feel is wanted

### Inputs & Forms

- Text: `#000000`
- Border: `1px solid #717989`
- Radius: 4px
- Focus: `rgb(20, 110, 245) solid 2px` outline
- Helper text: Space Mono 11px, Warm Charcoal — keeps form metadata in the technical voice

### Navigation

- Sticky top nav on cream background
- Be Vietnam Pro 15px weight 500 for nav links
- Claystack logo left-aligned
- CTA buttons right-aligned with pill radius
- Border bottom: `1px solid #dad4c8`
- Optional Spec Label slot in nav for build/version (`v1.0.0`, Space Mono 11px) — far right, before CTA
- Mobile: hamburger collapse at 767px

### Image Treatment

- Product screenshots in white cards with oat borders
- Colorful illustrated sections with swatch background colors
- 8px–24px radius on images
- Full-width colorful section backgrounds

### Distinctive Components

**Swatch Color Sections**

- Full-width sections with swatch-colored backgrounds (Matcha green, Slushie cyan, Ube purple, Lemon gold)
- White text on dark swatches, black text on light swatches
- Each section tells a distinct product story through its color

**Stack Lift (Hover Signature)**

- Replaces Clay's rotateZ tilt — Claystack's defining interaction
- `translateY(-3px to -4px)` + two revealed swatch-color offset shadows (`4px/4px` and `8px/8px`)
- Spring easing: `cubic-bezier(0.34, 1.56, 0.64, 1)` with slight overshoot
- Default swatch pair: Lemon 400 + Ube 300 on light surfaces; Matcha 300 + Slushie 500 on dark
- The shadow direction (down-right) reads as "lifted up off the page" — physical, layered, forward — not slanted

**Spec Label**

- Space Mono 11px uppercase, letter-spacing 0.5px, color Stack Graphite (`#1f1d1a`) or Warm Charcoal
- Format: `[STACK:01]`, `v1.0.0`, `BUILD 0426`, `[ACTIVE]`
- Lives above headings, beside cards, in nav corners — the typographic stamp that says "this is technical, this is precise, this has metadata"

**Stack Stripe**

- 3 horizontal lines, 1px each, 4px gap between them
- Top: Matcha 600, middle: Lemon 500, bottom: Ube 800 (or any 3-swatch combination)
- Used as a section divider OR the bottom-edge accent of feature cards
- The "sediment" — visual shorthand for "things are layered here"

**Grid Watermark**

- 8px dot grid, dots `2px × 2px`, color `rgba(85, 83, 78, 0.18)`
- CSS: `background-image: radial-gradient(circle, rgba(85,83,78,0.18) 1px, transparent 1px); background-size: 8px 8px;`
- Use sparingly — on hero backgrounds behind content, on technical "spec" surfaces, behind code blocks
- Never on swatch-colored sections (the warmth conflicts)

**Dashed Border Elements**

- Dashed borders (`1px dashed #dad4c8`) alongside solid borders
- Used for secondary containers, decorative elements, "draft" or "wip" surfaces
- Adds a hand-drawn, craft-like quality

## 5. Layout Principles

### Spacing System

- Base unit: 8px
- Scale: 1px, 2px, 4px, 6.4px, 8px, 12px, 12.8px, 16px, 18px, 20px, 24px

### Grid & Container

- Max content width centered
- Feature sections alternate between white cards and colorful swatch backgrounds
- Card grids: 2–3 columns on desktop
- Full-width colorful sections break the grid
- Footer with generous 40px radius container
- **Stack offset layout**: Adjacent feature cards in a grid can be offset vertically by 8–16px to imply layered, stacked depth — never more than 16px (it stops reading as "intentional" and starts reading as "broken")

### Whitespace Philosophy

- **Warm, generous breathing**: Cream background provides warm rest between content blocks. Spacing is generous but not austere — it feels inviting, like a well-set table.
- **Color as spatial rhythm**: Alternating swatch sections create rhythm through hue. Each color section is its own "room."
- **Craft-like density inside cards**: Within cards, content is compact and well-organized, contrasting with generous outer spacing.
- **Stack-stagger on grids**: Two-column or three-column card grids may stagger by 8–16px to suggest layering — purely optional, but a recognizable Claystack signature when used.

### Border Radius Scale

- Sharp (4px): Ghost buttons, inputs, spec buttons
- Standard (8px): Small cards, images, links
- Badge (11px): Tag badges
- Card (12px): Standard cards, primary buttons
- Feature (24px): Feature cards, images, panels
- Section (40px): Large sections, footer, containers
- Pill (1584px): Hero CTAs, pill-shaped buttons

## 6. Depth & Elevation

| Level                 | Treatment                                                                                   | Use                                                       |
| --------------------- | ------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Flat (Level 0)        | No shadow, cream canvas                                                                     | Page background                                           |
| Clay Shadow (Level 1) | `rgba(0,0,0,0.1) 0px 1px 1px, rgba(0,0,0,0.04) 0px -1px inset, rgba(0,0,0,0.05) 0px -0.5px` | Cards, buttons — multi-layer with inset highlight         |
| Stack Lift (Level 2)  | `4px 4px 0 0 <swatch-A>, 8px 8px 0 0 <swatch-B>, rgba(0,0,0,0.08) 0px 2px 4px`              | Hover state — two revealed swatch layers + contact shadow |
| Focus (Level 3)       | `rgb(20, 110, 245) solid 2px`                                                               | Keyboard focus ring                                       |

**Shadow Philosophy**: Claystack's shadow system is uniquely three-layered at rest: a downward cast (`0px 1px 1px`), an upward inset highlight (`0px -1px 1px inset`), and a subtle edge (`0px -0.5px 1px`). This creates the "pressed into clay" quality where elements feel both raised AND embedded. On hover, the **Stack Lift** swaps inset embedding for revealed depth — two flat swatch-colored offset shadows appear as if peeling back from beneath the element, like a stack of colored cards being separated. The motion is upward and slightly forward (`translateY(-3px)`) — never tilted, never rotated. Stack, not slant.

### Decorative Depth

- Full-width swatch-colored sections create dramatic depth through color contrast
- Dashed borders add visual texture alongside solid borders
- Stack Stripe (3-line sediment) marks transitions between content layers
- Grid Watermark on technical surfaces gives a blueprint/terminal undertone
- Product illustrations with warm, organic art style

## 7. Do's and Don'ts

### Do

- Use warm cream (`#faf9f7`) as the page background — the warmth is the identity
- Use `font-semibold` (600) for headings, `font-medium` (500) for UI, `font-normal` (400) for body — Be Vietnam Pro weight hierarchy is structural
- Use the named swatch palette for section backgrounds AND as Stack Lift shadow layers
- Apply **Stack Lift** on hover: `translateY(-3px)` + two-layer swatch offset shadow
- Use Space Mono for ALL technical metadata: spec labels, versions, builds, file paths, timestamps
- Use the Spec Label format `[STACK:NN]` or `v1.0.0` to mark technical surfaces
- Use warm oat borders (`#dad4c8`) — never neutral gray
- Mix solid and dashed borders for visual variety
- Use generous radius: 24px for cards, 40px for sections
- Use weight 600 for headings, 500 for UI, 400 for body — strict roles
- Optionally stagger card grids by 8–16px to imply Stack depth

### Don't

- Don't use cool gray backgrounds — the warm cream (`#faf9f7`) is non-negotiable
- Don't use neutral gray borders (`#ccc`, `#ddd`) — always use the warm oat tones
- **Don't use the Clay tilted hover** (`rotateZ(-8deg)`, `translateY(-80%)`) — Claystack's signature is Stack Lift, not slant
- Don't mix more than 2 swatch colors in the same section (still applies — restraint over chaos)
- Don't use Be Vietnam Pro for technical metadata (versions, builds, paths) — that's Space Mono territory
- Don't use small border radius (<12px) on feature cards — the generous rounding is structural
- Don't use standard blur shadows for hover — Stack Lift is hard offset, no blur on the swatch layers
- Don't put Grid Watermark on swatch-colored sections — it conflicts with the warmth
- Don't forget the Spec Label voice — without it, technical surfaces lose the stack feel and become generic Clay clones
- Don't stagger more than 16px on Stack offsets — past that it stops reading as intentional layering and starts reading as broken alignment

## 8. Responsive Behavior

### Breakpoints

| Name         | Width     | Key Changes                                    |
| ------------ | --------- | ---------------------------------------------- |
| Mobile Small | <479px    | Single column, tight padding                   |
| Mobile       | 479–767px | Standard mobile, stacked layout                |
| Tablet       | 768–991px | 2-column grids, condensed nav                  |
| Desktop      | 992px+    | Full layout, 3-column grids, expanded sections |

### Touch Targets

- Buttons: minimum 44px tap area (12px padding × 16px text × 12px padding ≈ 44px)
- Nav links: 15px font with generous spacing
- Mobile: full-width buttons for easy tapping

### Collapsing Strategy

- Hero: 80px → 60px → smaller display text
- Navigation: horizontal → hamburger at 767px; Spec Label slot collapses into menu
- Feature sections: multi-column → stacked
- Colorful sections: maintain full-width but compress padding
- Card grids: 3-column → 2-column → single column
- **Stack offsets disabled below 768px** — staggered grids collapse to flat-aligned stack on mobile (the offset stops reading correctly at narrow widths)

### Stack Lift on Touch

- Reduce to `translateY(-2px)` + single revealed swatch layer on `:active` for touch devices (`@media (hover: none)`) — preserves the signature feel without the spring delay
- Skip the cubic-bezier overshoot on touch — feels sluggish on tap

### Image Behavior

- Product screenshots scale proportionally
- Colorful section illustrations adapt to viewport width
- Rounded corners maintained across breakpoints

## 9. Agent Prompt Guide

### Quick Color Reference

- Background: Warm Cream (`#faf9f7`)
- Text: Clay Black (`#000000`)
- Mono spec text: Stack Graphite (`#1f1d1a`)
- Secondary text: Warm Silver (`#9f9b93`)
- Border: Oat Border (`#dad4c8`)
- Green / signal: Matcha 600 (`#078a52`)
- Cyan / info: Slushie 500 (`#3bd3fd`)
- Gold / draft: Lemon 500 (`#fbbd41`)
- Purple / process: Ube 800 (`#43089f`)
- Pink / error: Pomegranate 400 (`#fc7981`)
- Stack Lift default swatch pair: Lemon 400 (`#f8cc65`) + Ube 300 (`#c1b0ff`)

### Example Component Prompts

- **Hero**: "Create a hero on warm cream (#faf9f7) background with subtle 8px dot-grid watermark behind content. Spec Label `[STACK:01]` in Space Mono 11px uppercase, color Stack Graphite. Headline at 80px Be Vietnam Pro weight 600, line-height 1.00, letter-spacing -3.2px, black text. Subtitle at 20px weight 400, line-height 1.40, #9f9b93 text. Two buttons: black solid pill (12px radius) with Stack Lift hover (Lemon 400 + Ube 300 shadow stack), and ghost outlined (4px radius, 1px solid #717989) with single-layer Pomegranate Stack Lift."

- **Swatch section**: "Design a colorful section with Matcha 800 (#02492a) background. Section Heading at 44px Be Vietnam Pro weight 600, letter-spacing -1.32px, white text. Body at 18px weight 400, line-height 1.60, #84e7a5 text. White Stack Card inset with oat border (#dad4c8), 24px radius — includes `[v1.0.0]` Space Mono spec label, 32px Be Vietnam Pro title, 16px body. Hover triggers Stack Lift with Matcha 300 + Slushie 500 swatch shadow pair."

- **Stack Lift button**: "Build a primary button: black background, white text, 16px Be Vietnam Pro weight 500, 12px radius, 12px/20px padding. Default shadow is the multi-layer clay shadow. On hover: `translateY(-3px)`, box-shadow `4px 4px 0 0 #f8cc65, 8px 8px 0 0 #c1b0ff, rgba(0,0,0,0.08) 0px 2px 4px`, transition 220ms cubic-bezier(0.34, 1.56, 0.64, 1). DO NOT rotate or tilt — Claystack hovers lift, never slant."

- **Stack Card**: "Create a Stack Card: white background, 1px solid #dad4c8 border, 24px radius. Top row: Spec Label `[STACK:03]` in Space Mono 11px uppercase, color Warm Charcoal, letter-spacing 0.5px. Below: title 32px Be Vietnam Pro weight 600, letter-spacing -0.64px. Body 16px Be Vietnam Pro weight 400. 2px Matcha 600 top accent line indicates active state. Default clay shadow; hover triggers Stack Lift with Lemon 400 + Ube 300 layers."

- **Spec Label**: "Render a Spec Label: Space Mono 11px weight 400, text-transform uppercase, letter-spacing 0.5px, color #1f1d1a. Format options: `[STACK:01]`, `v1.0.0`, `BUILD 0426`, `[ACTIVE]`. Used above headings, beside cards, in nav corners as the technical voice marker."

- **Stack Stripe divider**: "Render a Stack Stripe: 3 horizontal lines, 1px each, 4px gap. Top line Matcha 600 (#078a52), middle Lemon 500 (#fbbd41), bottom Ube 800 (#43089f). Width: 48px. Use as section divider or feature card bottom-edge accent."

- **Grid Watermark surface**: "Add a Grid Watermark to a hero or technical surface: `background-image: radial-gradient(circle, rgba(85,83,78,0.18) 1px, transparent 1px); background-size: 8px 8px;` on a #faf9f7 base. Layer content above with z-index 1. Never apply on swatch-colored backgrounds."

### Iteration Guide

1. Start with warm cream (#faf9f7) — never cool white. Add Grid Watermark only on technical/spec surfaces.
2. Swatch colors are for full sections, not small accents — go bold with Matcha, Slushie, Ube. Use the stack-semantic mapping when the color carries meaning (signal/info/process/etc.).
3. Oat borders (#dad4c8) everywhere — dashed variants for decoration or "draft" surfaces.
4. Three-weight hierarchy is mandatory — 600 headings, 500 UI, 400 body — strict roles.
5. **Hover is Stack Lift — translateY + two revealed swatch shadow layers, never rotation.** This is the signature interaction; treat it like a brand asset.
6. Generous radius: 24px cards, 40px sections — nothing looks sharp or corporate.
7. Three weights: 600 (headings), 500 (UI), 400 (body) — strict roles. Space Mono carries all technical metadata.
8. Spec Label voice (`[STACK:NN]`, `v1.0.0`) marks technical surfaces — when in doubt about whether a surface should feel "stack" or "clay," ask if a Spec Label belongs there. If yes, lean stack. If no, lean clay craft.
