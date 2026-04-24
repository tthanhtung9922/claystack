# Claystack Design System

> *A workshop where raw clay meets engineered stack. Warmth of a kiln-fired surface, precision of a well-structured system. Every pixel feels hand-finished but load-bearing.*

---

## 1. Visual Theme & Atmosphere

Claystack occupies a space between the artisan's studio and the engineer's workshop. The interface is built on a warm bisque canvas (`#F5EDE0`) that evokes sun-dried clay — organic, tangible, unhurried — before any tooling begins. But the moment your eye lands on the grid, the mono spec-labels, or the sharp structural dividers, the "stack" side asserts itself: this surface has been measured, engineered, and deliberately assembled.

The signature typographic move is the duality of **Clay Serif** and **Stack Sans**. Every headline over 24px speaks in Fraunces — a variable serif with warmth and editorial confidence, as if the copy was set by a craftsperson who also happens to understand systems thinking. All UI chrome — buttons, labels, nav links, captions — answers in Geist, a clean workhorse sans that says "this was built, not painted." The two fonts should never compete; they take turns, like a master and apprentice working side by side.

The brand accent — **Terracotta Fired** (`#C65F3C`) — is the product of the kiln, not the raw material. It's not the pale blush of unfired clay; it's the confident, slightly-roughened surface of a pot that's been through heat and survived. Used only for primary CTAs and the highest-signal brand moments, it functions as a stamp of completion — the moment something goes from raw to ready. Gradients appear only as the "Kiln Fire" sweep (`#C65F3C → #E89A6B`), reserved for featured ribbons and hero punctuation marks.

**Key Characteristics:**
- Warm bisque canvas (`#F5EDE0`) evoking sun-dried clay — not paper, not white, not cold
- Typographic duality: Clay Serif (Fraunces) for narrative headlines, Stack Sans (Geist) for UI precision
- Terracotta Fired (`#C65F3C`) as the one saturated accent — the mark of something completed by fire
- All neutrals carry a warm brown undertone — no cool grays anywhere in the system
- Stack Mono (Geist Mono) surfaces as structural ornament: overline spec-labels, metric counters, code
- Radius capped at 24px — clay that has hardened doesn't bend into pills
- Depth through warm ring halos and whisper shadows, never heavy drops — surfaces lift, not float

---

## 2. Color Palette & Roles

### Primary
- **Terracotta Fired** (`#C65F3C`): The core brand color. Used exclusively for primary CTA buttons, brand marks, and the highest-signal moments. Warm enough to feel crafted, saturated enough to command attention.
- **Kiln Ember** (`#A8472A`): The pressed/hover state of Terracotta Fired. Deeper and more authoritative — the color of clay at depth of the kiln, not the surface.
- **Amber Glow** (`#E89A6B`): The warm highlight counterpart. Used as the far stop of the Kiln Fire gradient, and for illustration highlights. Never used as a standalone UI color.

### Secondary & Accent
- **Moss** (`#5E7A4A`): Semantic success. Warm olive-green — the color of the glaze that survived. Used for success states, "live" indicators, positive badges.
- **Saffron** (`#D89A35`): Semantic warning. A warm amber-gold that signals caution without alarm. For warning badges and non-critical alerts.
- **Rust** (`#B23A28`): Semantic error. Deep warm red — terracotta pushed too far into the kiln. Serious, but contextually consistent with the palette.
- **Slate Wash** (`#5A6B7A`): The one cool color in the entire system. Used **only** for input focus rings. Its coolness makes focus states immediately legible without introducing a second brand color.

### Surface & Background
- **Bisque** (`#F5EDE0`): The primary page background. Warm, sand-tinted clay — unfired but purposeful. The emotional foundation of the Claystack identity.
- **Bone Ivory** (`#FBF6EC`): Elevated surface — cards, containers, and panels sitting on Bisque. Slightly lighter, creating the gentlest possible sense of lift.
- **Studio White** (`#FFFFFF`): Reserved for input fields, modals, and maximum-contrast surfaces. Never used as a page background.
- **Hearth** (`#1A1512`): Dark-mode page background. The inside of the kiln — warm charcoal with a red-brown undertone, far warmer than any blue-tinted dark.
- **Forge** (`#2A231E`): Dark-mode elevated surface — cards, drawers, and nav on Hearth. A notch lighter, same warmth.

### Neutrals & Text
- **Graphite** (`#1F1A16`): Primary text color on light surfaces. Near-black with a warm brown undertone — never pure black, never cold.
- **Stoneware** (`#5C524A`): Secondary body text, subheadings, and UI descriptions. A distinctly warm medium-dark.
- **Silt** (`#8E8378`): Tertiary text — captions, metadata, de-emphasized labels. The texture of fine clay dust.
- **Porcelain** (`#E8DCCB`): Primary text on dark surfaces. A warm, fired-clay-tinted off-white — softer than pure white on Hearth.
- **Ash** (`#B0A496`): Secondary text on dark surfaces. Warm mid-gray for descriptions and UI text in dark contexts.

### Border & Structural
- **Slip** (`#EADFCE`): Subtle border on light surfaces. The slip of a potter — thin, barely visible, just enough to contain.
- **Fired Rim** (`#D7C5AB`): Stronger borders, section dividers, and card emphasis. The fired edge of a clay piece — visible but not harsh.
- **Forge Border** (`#3C3028`): Border on dark surfaces. Warm and dark, maintains chromatic consistency.

### Gradient System
- **Kiln Fire**: `linear-gradient(135deg, #C65F3C 0%, #E89A6B 100%)` — The signature gradient. Applied only at featured-card "Kiln Ribbon" top borders, select hero punctuation (overline bars, brand stamps), and loading states. Never as a full-bleed background.
- **Bisque Fade**: `linear-gradient(180deg, #F5EDE0 0%, #FBF6EC 100%)` — Subtle light-mode section transition, suggesting fired depth beneath the surface.
- **Hearth Depth**: `linear-gradient(180deg, #1A1512 0%, #2A231E 100%)` — Dark-mode depth layer for hero and feature sections.

---

## 3. Typography Rules

### Font Families

| Role | Font | Fallback | Personality |
|------|------|----------|-------------|
| **Clay Serif** | Fraunces | `Georgia, serif` | Variable-weight editorial serif — warmth, narrative, craft |
| **Stack Sans** | Geist | `Inter, system-ui, Arial, sans-serif` | Clean, engineered sans — precision, utility, UI chrome |
| **Stack Mono** | Geist Mono | `JetBrains Mono, ui-monospace, monospace` | Structural ornament — spec labels, code, technical counters |

### Hierarchy

| Role | Font | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|------|--------|-------------|----------------|-------|
| Display / Hero | Clay Serif | 64px (4rem) | 500 | 1.10 | normal | Maximum brand impact; one per page |
| Section Title | Clay Serif | 48px (3rem) | 500 | 1.15 | normal | Major section anchors |
| Sub-heading Large | Clay Serif | 36px (2.25rem) | 500 | 1.20 | normal | Feature section heads |
| Sub-heading | Clay Serif | 28px (1.75rem) | 500 | 1.25 | normal | Card titles, named features |
| Sub-heading Small | Clay Serif | 24px (1.5rem) | 500 | 1.30 | normal | Smallest serif heading |
| Lead / Intro | Stack Sans | 20px (1.25rem) | 400 | 1.55 | normal | Hero sub-copy, section intros |
| Body | Stack Sans | 16px (1rem) | 400 | 1.60 | normal | Standard prose and UI text |
| Body Small | Stack Sans | 14px (0.875rem) | 400 | 1.55 | normal | Compact lists, secondary content |
| Caption | Stack Sans | 12px (0.75rem) | 400 | 1.50 | +0.01em | Metadata, image captions, timestamps |
| Label / UI | Stack Sans | 13px (0.8125rem) | 500 | 1.25 | normal | Button text, nav links, form labels |
| Overline | Stack Mono | 11px (0.6875rem) | 400 | 1.60 | +0.08em | Uppercase spec labels on cards — the "stack" fingerprint |
| Code / Terminal | Stack Mono | 14px (0.875rem) | 400 | 1.65 | -0.01em | Inline code, code blocks, CLI |
| Metric | Stack Mono | 32px (2rem) | 400 | 1.00 | normal | Large numerical values, counters |

### Principles
- **Serif for clay (≥ 24px only)**: Clay Serif carries all headline content. Below 24px, switch to Stack Sans — small serifs undermine the precision that "stack" demands.
- **Mono as structural ornament**: Stack Mono is not for body text. It appears as: uppercase overlines on Stack Cards ("LAYER 01 · FOUNDATION"), code blocks, metric counters, and technical metadata. Used sparingly, it signals "this is a system, not just content."
- **Weight ceiling for serifs**: Clay Serif lives at weight 500 across all headline sizes. No bold (700+) serifs — the warmth is in the letterform, not the weight.
- **Generous body line-height (1.55–1.60)**: Reads like a well-typeset document, not a compressed dashboard. Matches the unhurried editorial feel of the Clay identity.
- **Tight headline line-height (1.10–1.30)**: Serif headlines read as titles, not paragraphs. The tight spacing gives them the gravity of a chapter header.

---

## 4. Component Stylings

### Buttons

**Primary — Terracotta Fired**
- Background: Terracotta Fired (`#C65F3C`)
- Text: Studio White (`#FFFFFF`), Stack Sans 13px weight 500
- Padding: 10px 20px
- Radius: 8px — fired and structured, not squishy
- Hover: background shifts to Kiln Ember (`#A8472A`)
- Focus: `0 0 0 2px #C65F3C40` ring (Ember Ring)
- The single most important action on any screen

**Secondary — Bone Ivory**
- Background: Bone Ivory (`#FBF6EC`)
- Text: Graphite (`#1F1A16`), Stack Sans 13px weight 500
- Border: `1px solid #D7C5AB` (Fired Rim)
- Padding: 10px 20px
- Radius: 8px
- Hover: background shifts to Bisque (`#F5EDE0`), border darkens to `#C2AD94`
- Workhouse secondary — warm, clearly interactive

**Ghost**
- Background: transparent
- Text: Graphite (`#1F1A16`), Stack Sans 13px weight 500
- Border: `1px solid #EADFCE` (Slip)
- Padding: 10px 20px
- Radius: 8px
- Hover: background `#F5EDE0` (Bisque), border Fired Rim
- For tertiary actions in low-emphasis contexts

**Dark Primary (Hearth surfaces)**
- Background: Terracotta Fired (`#C65F3C`)
- Text: Studio White (`#FFFFFF`), Stack Sans 13px weight 500
- Padding: 10px 20px
- Radius: 8px
- Hover: Kiln Ember (`#A8472A`)
- Works identically on dark; Terracotta holds against Hearth

**Dark Secondary (Hearth surfaces)**
- Background: Forge (`#2A231E`)
- Text: Porcelain (`#E8DCCB`), Stack Sans 13px weight 500
- Border: `1px solid #3C3028` (Forge Border)
- Padding: 10px 20px
- Radius: 8px
- Hover: border lightens to `#5C4A3A`

### Cards & Containers

**Standard Card**
- Background: Bone Ivory (`#FBF6EC`)
- Border: `1px solid #EADFCE` (Slip)
- Radius: 12px
- Shadow: `0 1px 2px rgba(31,26,22,0.04), 0 8px 24px rgba(31,26,22,0.06)`
- Internal padding: 24px

**Featured Card (with Kiln Ribbon)**
- All Standard Card styles, plus:
- Top border-radius: 2px (flattened to accommodate ribbon)
- Top decoration: 2px gradient bar `linear-gradient(135deg, #C65F3C, #E89A6B)`
- This 2px ribbon is the "Kiln Ribbon" — signals importance without noise

**Dark Card (Hearth context)**
- Background: Forge (`#2A231E`)
- Border: `1px solid #3C3028`
- Radius: 12px
- Shadow: `0 1px 2px rgba(0,0,0,0.12), 0 8px 24px rgba(0,0,0,0.20)`

### Inputs & Forms

- Background: Studio White (`#FFFFFF`)
- Text: Graphite (`#1F1A16`), Stack Sans 15px weight 400
- Placeholder: Silt (`#8E8378`)
- Border: `1px solid #D7C5AB` (Fired Rim)
- Radius: 10px
- Padding: 10px 14px
- Focus: border-color Slate Wash (`#5A6B7A`), `0 0 0 3px rgba(90,107,122,0.18)` ring
- Error: border-color Rust (`#B23A28`), `0 0 0 3px rgba(178,58,40,0.15)` ring
- Label: Stack Sans 13px weight 500, Graphite (`#1F1A16`), 6px below label

### Navigation

- Background: Bisque (`#F5EDE0`) with `backdrop-filter: blur(12px)` on sticky scroll
- Bottom border: `1px solid #EADFCE` (Slip)
- Logo: lowercase wordmark "claystack" in Clay Serif 20px weight 500, Graphite (`#1F1A16`)
- Nav links: Stack Sans 14px weight 400, Stoneware (`#5C524A`), hover shifts to Graphite
- Primary CTA: Terracotta Fired button (compact, 8px padding vertical)
- Secondary link: Ghost button or plain text link with Slip underline on hover
- Position: sticky top-0, z-index elevated

### Image Treatment

- Product screenshots and interface captures: generous radius (16–20px), Slip border
- Illustrations should feel organic, slightly imperfect — sketchy vector or watercolor-adjacent (not tech-diagram flat)
- Code/terminal screenshots: Hearth (`#1A1512`) background, Stack Mono, 16px radius
- Avoid generic stock photography; prefer hands-on-materials or process imagery (studio, workshop, kiln, craft)

### Distinctive Components

**Stack Card**
- A card telling the "clay meets stack" story visually
- Top: mono overline in uppercase Geist Mono 11px, Silt (`#8E8378`), letter-spacing +0.08em — e.g. "LAYER 01 · FOUNDATION"
- Below overline: Clay Serif heading 24–28px, Graphite
- Body: Stack Sans 15px, Stoneware
- Optional: thin Fired Rim (`#D7C5AB`) horizontal rule between overline and heading
- The mono overline is the "stack fingerprint" inside the warm card shell

**Kiln Ribbon**
- A 2px-tall `linear-gradient(135deg, #C65F3C, #E89A6B)` strip
- Placed at the top edge of featured cards or section headers
- Signals: "this is elevated, this has been through the fire"
- Never spans full page width; constrained to card or section container

**Strata Divider**
- A decorative horizontal section separator with three stacked lines:
  - 1px Slip (`#EADFCE`)
  - 1px Fired Rim (`#D7C5AB`)
  - 1px Terracotta Fired at 30% opacity
- Line gap: 2px between each
- Total height: 8px
- Placed between major page sections to suggest geological layering
- On dark surfaces: replace Slip/Fired Rim with Forge Border (`#3C3028`) tints

**Firing State Pill**
- Small status badge: Stack Mono 11px, uppercase, +0.06em letter-spacing
- Padding: 3px 8px, radius 4px (more angled than standard rounded — like a fired clay stamp)
- Variants: Moss fill (`#5E7A4A`, `#EBF3E6` bg), Saffron fill (`#D89A35`, `#FDF3DC` bg), Rust fill (`#B23A28`, `#FAE8E6` bg), Silt fill (`#8E8378`, `#F0EBE4` bg)
- Used for: "LIVE", "STAGED", "DEPRECATED", "FIRING...", "COMPLETE"

---

## 5. Layout Principles

### Spacing System
- Base unit: 8px
- Scale: 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 96 / 128
- Button padding: 10px vertical, 20px horizontal (standard); 8px / 16px (compact)
- Card internal padding: 24px (standard), 32px (featured hero cards)
- Section vertical spacing: 96–128px between major sections
- Component-to-component gap: 24–32px within a section

### Grid & Container
- Max container width: 1200px, centered with 24px horizontal padding
- Hero max-width: 1040px — slightly narrower for editorial feel
- Feature grids: 2-column or 3-column at desktop, single-column at mobile
- Stack Cards: typically 3-column grid, 24px gap
- No full-bleed color sections unless deliberately "Kiln Fire" featured — prefer contained sections with generous padding

### Whitespace Philosophy
> **Editorial warmth on an engineered grid.**

Sections breathe. The serif headlines demand space the way a headline in a design magazine does — padding above a 64px heading should be at least 96px. But that space is measured by the grid, not felt intuitively. Every whitespace decision maps to an 8pt value. Warmth and structure coexist without compromise.

- **Craft approach**: generosity — never cram. Sections read like chapters.
- **Stack approach**: every gap is a multiple of 8px. No fudged 14px or 22px gaps.
- **Content island**: major sections feel self-contained, each with its own distinct temperature (light → dark alternation available for longer pages).

### Border Radius Scale
| Name | Value | Use |
|------|-------|-----|
| Crisp | 4px | Firing State Pills, inline tags |
| Firm | 8px | Buttons, small UI chips |
| Standard | 10px | Input fields |
| Card | 12px | Standard cards and containers |
| Featured | 16px | Featured cards, video embeds |
| Modal | 20px | Modals, drawers, large overlays |
| Cap | 24px | Maximum — hero containers, hero images |

**Rule**: Never exceed 24px on a functional element. Claystack has been fired — it doesn't go round. Pill buttons (`border-radius: 999px`) are not part of this system.

---

## 6. Depth & Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| Flat (0) | No shadow, no border | Bisque background, in-page text |
| Contained (1) | `1px solid #EADFCE` (Slip) | Standard cards, sections, form wrappers |
| Defined (2) | `1px solid #D7C5AB` (Fired Rim) | Featured sections, nav, dividers |
| Whisper (3) | `0 1px 2px rgba(31,26,22,0.04), 0 8px 24px rgba(31,26,22,0.06)` | Standard card hover, elevated inputs |
| Ring (4) | `0 0 0 2px #C65F3C40` or `0 0 0 3px rgba(90,107,122,0.18)` | Focus states, active interactive elements |
| Elevated (5) | `0 2px 4px rgba(31,26,22,0.06), 0 16px 48px rgba(31,26,22,0.10)` | Hero cards, modal overlays, featured banners |

### Shadow Philosophy

Shadows are **warm-tinted** using `rgba(31,26,22,*)` — the RGB decomposition of Graphite (`#1F1A16`). Never use pure black (`rgba(0,0,0,*)`) shadows; they introduce cold blue undertones that break the clay warmth.

The primary shadow mechanism is the **ring** (not a drop shadow): `0 0 0 Npx colorAtOpacity`. This is how interactive states are communicated — a warm halo that appears to grow from within the surface. Drop shadows appear only when an element genuinely needs to feel elevated above the canvas (modals, feature hero cards, sticky nav on scroll).

**Dark mode depth**: On Hearth (`#1A1512`), traditional drop shadows lose contrast. Dark-mode elevation is communicated through `background-color` increments: Hearth → Forge → a third layer at `#382E25`. Shadow opacity doubles on dark surfaces.

---

## 7. Do's and Don'ts

### Do
- Use Bisque (`#F5EDE0`) as the primary light background — the warm clay tone is the foundation of the Claystack identity
- Use Clay Serif (Fraunces) at weight 500 for all headlines ≥ 24px — this is the "clay" fingerprint
- Reserve Terracotta Fired (`#C65F3C`) for primary CTAs and the singular brand moment per page
- Keep all neutrals warm-toned — every gray should have a visible brown undertone
- Use Stack Mono overlines ("LAYER 01 · FOUNDATION") on Stack Cards — mono is the "stack" fingerprint
- Use ring shadows (`0 0 0 2px`) for focus/hover states; warm-tinted drop shadows (`rgba(31,26,22,*)`) for elevation
- Cap border-radius at 24px — fired clay doesn't bend into pills
- Use the Strata Divider at major section breaks to reinforce the "layered system" identity
- Alternate Light (Bisque) and Dark (Hearth) sections on long-form pages for chapter-like rhythm
- Apply Kiln Fire gradient exclusively as a ribbon or micro-punctuation, never as a full-bleed background

### Don't
- Don't use cool blue-grays or blue-tinted dark surfaces anywhere — the system is exclusively warm-toned
- Don't use Clay Serif below 24px — it loses legibility and the serif-sans split becomes meaningless
- Don't use full-pill buttons (`border-radius: 999px`) — Claystack is fired hard
- Don't introduce gradients beyond Kiln Fire, Bisque Fade, and Hearth Depth — three is the limit
- Don't use bold (700+) weight on Clay Serif — weight 500 is the ceiling; authority comes from form, not heaviness
- Don't use pure white (`#FFFFFF`) as a page background — Bisque (`#F5EDE0`) is always the canvas; Studio White is for inputs only
- Don't use heavy multi-layer drop shadows — depth is communicated through rings, borders, and background shifts
- Don't mix sans-serif for headings ≥ 24px — the serif/sans split is the core typographic identity
- Don't use Slate Wash (`#5A6B7A`) for anything other than input focus rings — it is the one cool color and must remain singular
- Don't apply Stack Mono to body text or UI labels — it is structural ornament, not a reading font

---

## 8. Responsive Behavior

### Breakpoints

| Name | Width | Key Changes |
|------|-------|-------------|
| Small Mobile | < 480px | Single column, stacked nav, heading scales to ~36px display |
| Mobile | 480–640px | Single column, compact section padding (48px vertical) |
| Large Mobile | 640–768px | Slightly wider content, some 2-col grids begin |
| Tablet | 768–992px | 2-column grids, condensed nav, 48px section heading |
| Desktop | 992–1200px | Full layout, 3-column grids, hero at 64px |
| Wide | 1200px+ | Container locks at 1200px; content does not stretch |

### Touch Targets
- All buttons: minimum 44px height
- Nav links: 48px touch area (padding-augmented even if visually smaller)
- Card surfaces serve as full touch targets on mobile
- Firing State Pills: minimum 28px height on mobile with `padding: 6px 12px`

### Collapsing Strategy
- **Navigation**: Full horizontal nav → hamburger at < 768px. Drawer slides from right on Hearth background.
- **Stack Cards**: 3-column → 2-column at tablet → single-column at mobile, full-width cards
- **Hero typography**: 64px → 48px → 36px progressive scaling
- **Section padding**: 96–128px → 64px → 48px across breakpoints
- **Strata Dividers**: Full-width at all breakpoints; maintain 3-line structure
- **Kiln Ribbons**: Maintain at all sizes — 2px is always visible

### Image Behavior
- All images and media constrained with `max-width: 100%` and `height: auto`
- Border-radius on images scales proportionally (16px at desktop → 12px at mobile)
- Code/terminal screenshots maintain monospace rendering at all sizes
- No art direction changes between breakpoints; content-based cropping only

---

## 9. Agent Prompt Guide

### Quick Color Reference
```
Brand CTA:        Terracotta Fired (#C65F3C)
Brand Hover:      Kiln Ember (#A8472A)
Brand Gradient:   linear-gradient(135deg, #C65F3C, #E89A6B)
Page Background:  Bisque (#F5EDE0)
Card Surface:     Bone Ivory (#FBF6EC)
Primary Text:     Graphite (#1F1A16)
Secondary Text:   Stoneware (#5C524A)
Tertiary Text:    Silt (#8E8378)
Subtle Border:    Slip (#EADFCE)
Strong Border:    Fired Rim (#D7C5AB)
Dark Canvas:      Hearth (#1A1512)
Dark Surface:     Forge (#2A231E)
Dark Text:        Porcelain (#E8DCCB)
```

### Example Component Prompts

**Hero Section**
> "Create a hero section on Bisque (`#F5EDE0`). Headline: 64px Fraunces weight 500, line-height 1.10, Graphite (`#1F1A16`) color. Sub-copy: 20px Geist weight 400, line-height 1.55, Stoneware (`#5C524A`). Primary CTA button: Terracotta Fired (`#C65F3C`) fill, Studio White text, Geist 13px weight 500, 10px/20px padding, 8px radius. Secondary link: Ghost style, Fired Rim border, Graphite text. Max content width 1040px, 128px vertical padding."

**Stack Card Grid**
> "Build a 3-column card grid on Bisque (`#F5EDE0`). Each card: Bone Ivory (`#FBF6EC`) fill, `1px solid #EADFCE` border, 12px radius, 24px padding, whisper shadow `0 1px 2px rgba(31,26,22,0.04), 0 8px 24px rgba(31,26,22,0.06)`. Add a mono overline at the top: Geist Mono 11px uppercase, Silt (`#8E8378`), letter-spacing +0.08em, e.g. 'LAYER 01 · FOUNDATION'. Below: Clay Serif heading 24px weight 500, Graphite. Then Geist body 15px, Stoneware (`#5C524A`). One card should have a Kiln Ribbon: 2px top gradient bar `linear-gradient(135deg, #C65F3C, #E89A6B)`."

**Primary Button**
> "Create a button with Terracotta Fired (`#C65F3C`) background, Studio White text in Geist 13px weight 500, 10px top/bottom and 20px left/right padding, 8px border-radius. Hover state: Kiln Ember (`#A8472A`) background. Focus state: `0 0 0 3px rgba(198,95,60,0.25)` ring. No drop shadow."

**Kiln-Fired Feature Section (Light)**
> "Design a feature section on Bisque (`#F5EDE0`). Section opens with a Strata Divider: three stacked horizontal lines — 1px `#EADFCE`, 1px `#D7C5AB`, 1px `rgba(198,95,60,0.30)`, each 2px apart. Then 48px Fraunces heading weight 500, Graphite. Lead copy 20px Geist, Stoneware. Below: 2-column card grid using Stack Cards with mono overlines. Section padding 96px vertical."

**Dark Mode — "Inside the Kiln"**
> "Build a dark-mode feature section on Hearth (`#1A1512`). Cards on Forge (`#2A231E`), `1px solid #3C3028` border, 12px radius, same whisper shadow with doubled opacity `0 1px 2px rgba(0,0,0,0.12), 0 8px 24px rgba(0,0,0,0.20)`. Section heading: 48px Fraunces weight 500, Porcelain (`#E8DCCB`). Body: 16px Geist, Ash (`#B0A496`). Primary button: Terracotta Fired (`#C65F3C`), Studio White text — identical to light mode. Keep mono overlines in Ash (`#B0A496`) on dark cards."

### Iteration Guide

1. **Name the surface first** — "on Bisque" or "on Hearth" before specifying any other attribute. The canvas determines everything else.
2. **Specify font family explicitly** — "Fraunces 500 for the heading, Geist for the body" — never assume the agent will infer the serif/sans split.
3. **Reference color names + hex pairs** — "Stoneware (`#5C524A`)" not "dark gray". The name carries the warm-undertone requirement.
4. **For shadows, say "whisper shadow" or "ring focus"** — never "drop shadow" alone; it will default to generic cold black.
5. **Mono overlines need full spec** — "Geist Mono 11px uppercase, +0.08em letter-spacing, Silt color" — shorthand breaks the Stack Card effect.
6. **Kiln Ribbon needs direction** — say "2px gradient bar at top: `linear-gradient(135deg, #C65F3C, #E89A6B)`" — the direction (135deg) is what makes it feel fired, not flat.
7. **Keep Slate Wash singular** — "Slate Wash focus ring on inputs only" — if you use it anywhere else, the system's one cool accent loses its signal value.
