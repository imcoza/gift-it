---
name: gift-it-ui
description: >-
  Builds new pages and sections for the Gift-it website in a fixed
  multi-phase process: brief, component inventory, HTML skeleton, section
  plan, HTML build with image validation, CSS build, responsive, polish,
  and a final gate that includes indentation and orientation audit. Uses only
  Gift-it's existing design tokens and shared component classes. Use when the
  user asks to add a new page, add a section, build a component, or extend any
  part of the Gift-it website. Triggers on: "add a section", "build this
  page", "create a new page", "make a component", "add to the site",
  "check indentation", "fix alignment", "validate image".
  Do NOT use this skill when the user provides a reference to redesign from —
  that is the design-from-reference skill.
---

# Gift-it UI Builder

Builds new Gift-it pages and sections from a brief.
This skill produces HTML + inline `<style>` that matches the existing
codebase exactly — same tokens, same naming conventions, same patterns.
Every image is validated for context relevance before it is accepted.
Indentation and visual orientation are audited before delivery.

Follow all eleven phases in order. Each phase ends with a clear output.
Do not start a phase until the previous one is complete.

---

## Phase 1 · Take the Brief

Before anything else, lock down what is being built and why.

**Answer every question before proceeding:**

1. **What is being built?**
   Is this a full new page, a new section inside an existing page, or a
   standalone component (card, banner, widget)?

2. **What is the job of this UI?**
   What does a visitor need to understand or do here? One sentence.

3. **What content must appear?**
   List every piece of content: headlines, body text, stats, CTAs, images,
   icons, lists. If content is not provided, generate it in Gift-it's voice:
   direct, India-first, no marketing fluff.

4. **Which existing page does this belong to or link from?**
   Name the file (e.g., `index.html`, `pricing.html`).

5. **Are there hard constraints?**
   Things that must be in or must be excluded. If none, record "none" and move on.

If any answer is missing, ask — but ask all missing questions at once, not
one at a time. Do not proceed to Phase 2 until every question is answered.

---

## Phase 2 · Component Inventory

Read `style.css` before writing a single line of HTML or CSS.

**Build two lists:**

**List A — Reuse as-is (no new CSS needed):**
Every global class that can be applied directly. Must include at minimum:
- `.container` — page wrapper with max-width and gutter
- `.eyebrow` — uppercase accent label above section titles
- `.section-title` — section `<h2>` style
- `.section-sub` — supporting paragraph below section title
- `.btn`, `.btn--primary`, `.btn--outline`, `.btn--lg` — all button variants
- `.divider` — 1px horizontal rule in `--color-border`
- `.cta-band`, `.cta-band__inner`, `.cta-band__headline`, `.cta-band__sub`,
  `.cta-band__actions` — the full-width CTA band at page bottom
- `.footer` and all `.footer__*` classes — never recreate the footer
- `.nav` and all `.nav__*` classes — never recreate the nav
- `.whatsapp-fab` — floating WhatsApp button
- `.diwali-banner` — announcement bar at top

**List B — New CSS needed:**
Classes that do not exist yet. For each one, write the class name and the
reason it cannot be covered by an existing class or modifier.

Rule: if a new class is just an existing class with one property changed,
use a modifier (`.existing-class--modifier`) instead of a new class.

---

## Phase 3 · Page Skeleton (new pages only)

Skip this phase if adding a section to an existing page.

For a new page, produce the full HTML document skeleton before any section
content. The skeleton must contain exactly these elements in this order:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gift-it — [Page Title]</title>
  <meta name="description" content="[≤155 chars]">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="style.css">
  <style>
    /* PAGE-SPECIFIC STYLES GO HERE */
  </style>
</head>
<body>

  <!-- DIWALI BANNER -->
  <!-- copy from index.html verbatim -->

  <!-- NAV -->
  <!-- copy from index.html verbatim, update is-active class -->

  <main>
    <!-- SECTIONS GO HERE -->
  </main>

  <!-- FOOTER -->
  <!-- copy from index.html verbatim -->

  <!-- WHATSAPP FAB -->
  <!-- copy from index.html verbatim -->

  <script>
    /* hamburger toggle — copy from index.html verbatim */
  </script>

</body>
</html>
```

Never recreate the nav, footer, diwali banner, or WhatsApp FAB from scratch.
Copy the exact HTML from `index.html` and update only what changes
(e.g., the `is-active` link).

---

## Phase 4 · Section Plan

Map every section that will be built. Write this plan in plain text before
writing any HTML or CSS.

For each section, record:

```
Section N — [Section Name]
  Job:        [what the user needs to understand or do here]
  Content:    [bullet list of every content element]
  Layout:     [describe the grid: e.g., "3-column card grid, 1-column on mobile"]
  New CSS:    [list class names from List B that belong to this section, or "none"]
  CTA:        [button label and href, or "none"]
```

End the plan with the **Page Order** — the final top-to-bottom sequence of all
sections. The order must match the information hierarchy: what the user needs
first comes first.

Do not start Phase 5 until the Section Plan is complete.

---

## Phase 5 · Build HTML

Write HTML for every section in the Page Order from Phase 4.

**Rules — follow every one:**

**Structure**
- Every section uses `<section aria-labelledby="[id]">`.
- Every section title `<h2>` has a unique `id` that matches `aria-labelledby`.
- One `<h1>` per page — the page hero title only.
- Card titles use `<h3>`. Never skip heading levels.
- Use `<a href>` for links that navigate. Use `<button>` for actions that do not.

**Naming**
- Block: `.feature-card`
- Element: `.feature-card__title`
- Modifier: `.feature-card--highlighted`
- Every new class name must be on List B from Phase 2.

**Content**
- Write real copy. No "Lorem ipsum". No "Placeholder text".
- All copy must match Gift-it's voice: plain, direct, India-first, specific.
  ✅ "Delivered to 19,000+ pincodes across India"
  ❌ "We offer nationwide delivery solutions"
- Every emoji or decorative icon has `aria-hidden="true"`.
- Every image has a descriptive `alt` attribute. Decorative images use `alt=""`.

**Shared elements**
- `.container` wraps every section's inner content.
- `.eyebrow` + `.section-title` + `.section-sub` open every section that
  has a heading. This trio is mandatory — do not skip the eyebrow.

---

## Phase 5A · Image Validation Gate

**Run this gate for every `<img>` tag before writing any CSS.**
An image that fails any check must be replaced or removed — it cannot proceed.

### Step 1 — Context Relevance Test

Answer all four questions. All four must pass.

| Question | Pass condition |
|----------|---------------|
| **Subject match** — Does the image visually represent what this section is about? | The image subject directly illustrates the section job from Phase 4. A delivery photo belongs in a logistics section. A team photo belongs in a team section. A product shot belongs in a product section. If there is any ambiguity, it fails. |
| **Audience match** — Does the image reflect the Gift-it audience? | Indian corporate context. Office environments, Diwali gifting, professional settings. Stock photos of Western offices, generic handshakes, or unrelated people fail. |
| **Tone match** — Does the image tone match Gift-it's visual identity? | Dark, professional, clean. Bright-white lifestyle photos, cartoons, clip art, or heavily filtered images fail. |
| **Necessity test** — Does the image add information the text cannot? | If removing the image loses no meaning, the image is decorative. Decorative images use `alt=""` and `aria-hidden="true"`. If an image adds no information and is not purely decorative, remove it. |

### Step 2 — Technical Requirements

Every image that passes Step 1 must meet all of these:

| Requirement | Rule |
|-------------|------|
| `alt` text | Real description of what the image shows. Never the filename. Never "image of". Max 125 chars. |
| `loading` attribute | `loading="lazy"` on every image that appears below the fold. `loading="eager"` on hero images only. |
| `width` + `height` | Always declare both to prevent layout shift (CLS). |
| `aspect-ratio` | Set via CSS `aspect-ratio` so the image never distorts on resize. |
| Format | Use `.webp` for photos. Use `.svg` for icons and logos. Never `.bmp` or `.tiff`. |
| Max file weight | Call out if an image likely exceeds 200 KB. Flag it with a comment: `<!-- ⚠️ compress before ship -->` |
| Responsive | Every image must have `max-width: 100%` and `height: auto` in CSS, or use a responsive container. |

### Step 3 — Validation Record

After checking every image, write a short table in a comment block:

```html
<!--
IMAGE VALIDATION RECORD
──────────────────────────────────────────────────────────────
src              | section        | context pass | action
──────────────────────────────────────────────────────────────
gift-box.webp    | hero           | ✅           | keep
office-us.jpg    | team           | ❌ W. office | replaced with india-team.webp
swirl.png        | background     | decorative   | alt="" aria-hidden="true"
──────────────────────────────────────────────────────────────
-->
```

Place this record immediately before the `</main>` closing tag.
If there are zero images in the build, write: `<!-- IMAGE VALIDATION RECORD: no images used -->`.

---

## Phase 6 · Build CSS

Write inline `<style>` for all classes on List B from Phase 2.

**Token-first rule — absolute.**
Read `style.css` `:root` block for the full token list before writing CSS.
If a token exists for a property, it is mandatory. Hard-coded values are only
allowed when no token covers the case.

**Most-used tokens at a glance:**

```
Colors   --color-bg · --color-surface · --color-surface-alt · --color-surface-raised
         --color-text-primary · --color-text-secondary · --color-text-muted
         --color-accent · --color-accent-hover · --color-accent-dim
         --color-border · --color-border-faint · --color-success · --color-warning

Type     --text-display · --text-section · --text-xl · --text-lg
         --text-md · --text-sm · --text-xs
         --weight-regular · --weight-medium · --weight-semibold · --weight-bold
         --lh-display · --lh-section · --lh-body

Space    --s1(8) --s2(16) --s3(24) --s4(32) --s5(40) --s6(48)
         --s7(56) --s8(64) --s10(80) --s12(96) --s15(120)

Shape    --radius-sm · --radius-md · --radius-lg · --radius-xl
Layout   --max-width(1200px) · --gutter(32px) · --prose-max(68ch)
Motion   --ease(140ms ease) · --ease-md(220ms ease)
```

**CSS skeleton every section must follow:**

```css
/* SECTION NAME ----------------------------------------------- */
.section-name {
  padding: var(--s15) 0;
  border-top: 1px solid var(--color-border);
}
```

**Card skeleton every card must follow:**

```css
.thing-card {
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--s5);
}
.thing-card:hover {
  border-color: var(--color-accent);
  background-color: var(--color-surface-raised);
  transition: background-color var(--ease), border-color var(--ease);
}
```

**Typography roles — apply exactly:**

| Role | CSS |
|------|-----|
| Eyebrow label | `font-size: var(--text-xs); font-weight: var(--weight-semibold); letter-spacing: 0.1em; text-transform: uppercase; color: var(--color-accent);` |
| Section `<h2>` | `font-size: var(--text-section); font-weight: var(--weight-bold); letter-spacing: -0.022em; line-height: var(--lh-section);` |
| Card `<h3>` | `font-size: var(--text-xl); font-weight: var(--weight-bold); letter-spacing: -0.015em;` |
| Body copy | `font-size: var(--text-md); color: var(--color-text-secondary); line-height: var(--lh-body);` |
| Card meta | `font-size: var(--text-sm); color: var(--color-text-muted);` |
| Stat number | `font-size: 40px; font-weight: var(--weight-bold); letter-spacing: -0.03em; line-height: 1;` |

---

## Phase 7 · Responsive Layout

Write breakpoints at the **bottom of each section's CSS block** — not in a
separate file, not at the end of the `<style>` block.

**Breakpoint contract — non-negotiable:**

| Breakpoint | What changes |
|------------|-------------|
| `≤ 860px` (tablet) | 2-col grids → 1-col; 4-col grids → 2-col; side-by-side → stacked |
| `≤ 640px` (mobile) | All grids → 1-col; decorative sidebars hidden; fluid type applies |

**Fluid type — use `clamp()` for these only:**

```css
/* Section headings */
font-size: clamp(24px, 3vw, 34px);

/* Large stat numbers */
font-size: clamp(32px, 5vw, 48px);
```

Never clamp body copy (`--text-md`). Never clamp card titles (`--text-xl`).

**Touch target rule:**
Every tappable element on mobile must be at least 44px tall.
Add `min-height: 44px` to buttons and nav links when in doubt.

**Content stacking order on mobile:**
Text columns come before image/aside columns.
Use `order: 2` on the visual element inside the media query if needed.

---

## Phase 8 · Polish

Apply these in order. Do not skip any item.

**8.1 — Hover & focus states**
Every interactive element must have both `:hover` and `:focus-visible`.
`:focus-visible` always uses `outline: 2px solid var(--color-accent); outline-offset: 2px;`

**8.2 — Transition checklist**
Add `transition: … var(--ease)` to:
- [ ] Card `border-color` and `background-color` on hover
- [ ] All `<a>` `color` on hover
- [ ] All `.btn` `background-color` and `border-color` on hover

**8.3 — Depth layering**
Use the surface stack to create depth without box-shadows:
```
--color-bg              → page
--color-surface         → card
--color-surface-alt     → nested item inside card
--color-surface-raised  → hovered card
```
Never introduce `box-shadow` unless the Move explicitly calls for it.

**8.4 — Eyebrow audit**
Every section that has a heading must start with `.eyebrow`.
Scan every `<section>` in the output and confirm.

**8.5 — Reduced motion**
Any animation that loops or lasts > 200ms must be wrapped:
```css
@media (prefers-reduced-motion: reduce) {
  .animated-thing { animation: none; transition: none; }
}
```

---

## Phase 9 · Indentation Audit

Read the entire HTML output. Fix every violation before Phase 10.

### HTML Indentation Rules

- **2 spaces** per indent level. Never tabs. Never 4 spaces.
- Every child element indented 2 spaces beyond its parent. No exceptions.
- Block elements (`div`, `section`, `p`, `h1`–`h6`, `ul`, `li`) always on their own line.
- Inline elements (`span`, `a`, `strong`) may stay on the same line when content is < 80 chars.
- Closing tag on its own line at the same indent level as the opening tag.
- **One blank line** between top-level `<section>` blocks. Zero blank lines between siblings inside a component.
- Section comments (`<!-- HERO -->`) flush-left, immediately before the element they label.
- Elements with more than 3 attributes: one attribute per line, indented 2 spaces inside the tag.

### CSS Indentation Rules

- **2 spaces** inside every rule block. One property per line. Never two on the same line.
- Closing brace on its own line at 0 indent. One blank line between rules, zero inside.
- Section comments (`/* SECTION NAME --- */`) flush-left, immediately before the rule.
- **Property order within every rule:** `display` → `position` → `top/right/bottom/left` → `width/height` → `min/max-*` → grid/flex props → `gap` → `padding` → `margin` → `border` → `border-radius` → `background` → `color` → `font-*` → `line-height` → `letter-spacing` → `text-*` → `transition` → `cursor`
- Inside `@media` blocks: properties indented 2 spaces inside the block rule.

---

## Phase 10 · Orientation Audit

Orientation = the visual reading flow, alignment, and spatial hierarchy of
every element on the page. Read the layout plan from Phase 4 and verify
every item below against the output.

### Alignment Rules

| Check | Rule |
|-------|------|
| **Text alignment** | Body copy, card text, list items: always `text-align: left`. Never `justify`. Center-align only the hero headline and CTA band headline. |
| **Grid alignment** | All grid columns in the same row must be the same height. Use `align-items: stretch` (default) unless the brief specifies `start`. |
| **Flex alignment** | Navigation and button rows use `align-items: center`. Never `baseline` on nav items. |
| **Icon alignment** | Icons beside text always use `align-items: flex-start` when the text is multi-line. `center` only when the text is a single line. |
| **Card consistency** | Every card in the same grid must use identical `padding`, `border-radius`, and `background-color`. No one-off overrides. |
| **Eyebrow position** | `.eyebrow` always comes before `.section-title`, never after, never beside it. |
| **CTA position** | Primary CTA always to the right of or below secondary CTA — never before it in DOM order. |

### Spacing Consistency Rules

| Check | Rule |
|-------|------|
| **Section gap** | Every top-level `<section>` uses `padding: var(--s15) 0`. If a section needs less space, use `var(--s10) 0` and document why. Never a custom value. |
| **Card internal spacing** | Every card uses `padding: var(--s5)` unless the card is a compact tile (then `var(--s3)`). No mixing within the same grid. |
| **Between-section dividers** | Every section except the first after `<header>` has `border-top: 1px solid var(--color-border)`. No section has both a `border-top` and a visible `margin-top`. |
| **Grid gap** | Card grids: `gap: var(--s3)`. Side-by-side content columns: `gap: var(--s10)`. Point lists: `gap: var(--s3)`. Never mix values within one grid. |
| **Heading margin** | `.section-title` always has `margin-bottom: var(--s2)`. `.section-sub` always has `margin-bottom: var(--s8)` before the first grid or content block. |

### Visual Orientation Checklist

Run this on the complete page output:

- [ ] No section is wider than `--max-width` (1200px) at any viewport
- [ ] No text block is wider than `--prose-max` (68ch)
- [ ] No two adjacent sections use the same background color — surfaces must alternate or be separated by a border
- [ ] The primary CTA button (`btn--primary`) appears above the fold on desktop (within the first two sections)
- [ ] Every image has a declared `aspect-ratio` or fixed `height` — no images that stretch or collapse
- [ ] No orphaned single words on the last line of any heading (use `max-width` or `text-wrap: balance` to fix)
- [ ] On mobile, every section's content is readable without horizontal scrolling
- [ ] The page has a clear visual top-to-bottom narrative: hook → proof → detail → action

---

## Phase 11 · Final Gate

Run every item. Do not deliver until all boxes are checked.

### Token compliance
- [ ] Zero hard-coded hex values (except `#fff` on solid accent backgrounds)
- [ ] Zero hard-coded spacing values in px or rem
- [ ] Zero hard-coded border-radius values
- [ ] Zero duplicate CSS rules

### HTML quality
- [ ] One `<h1>` on the page
- [ ] Every `<section>` has `aria-labelledby` wired to a heading `id`
- [ ] Every decorative emoji/icon has `aria-hidden="true"`
- [ ] Every `<img>` has `alt` text
- [ ] Every interactive element is `<a href>` or `<button>` — no clickable `<div>`

### Image validation
- [ ] Phase 5A ran for every `<img>` in the output
- [ ] Image validation record comment block is present before `</main>`
- [ ] Every image that failed context relevance was replaced or removed
- [ ] Every image has `loading`, `width`, `height`, and `aspect-ratio`
- [ ] Every image over 200 KB is flagged with `<!-- ⚠️ compress before ship -->`

### Content
- [ ] All copy is real — no Lorem ipsum, no "Placeholder"
- [ ] All `href` values point to real targets in this project
- [ ] No `TODO` comments in the output

### Responsive
- [ ] 860px breakpoint written for every new grid
- [ ] 640px breakpoint written for every new grid
- [ ] No horizontal overflow at any breakpoint
- [ ] Touch targets ≥ 44px on mobile

### Indentation (from Phase 9)
- [ ] 2-space indent throughout all HTML — no tabs, no 4-space
- [ ] Every block element is on its own line
- [ ] CSS properties are in the mandated order within every rule
- [ ] One blank line between CSS rules, zero blank lines inside a rule
- [ ] Section comments are flush-left in both HTML and CSS

### Orientation (from Phase 10)
- [ ] Body copy is left-aligned everywhere except hero and CTA band
- [ ] No text block exceeds 68ch (`--prose-max`)
- [ ] Every card grid uses consistent padding, radius, and background
- [ ] No two adjacent sections share the same background color
- [ ] Primary CTA (`btn--primary`) is visible above the fold on desktop
- [ ] No heading has an orphaned single word on its last line
- [ ] Visual narrative flows: hook → proof → detail → action

### Shared elements
- [ ] Nav is copied from `index.html`, not recreated
- [ ] Footer is copied from `index.html`, not recreated
- [ ] Diwali banner is copied from `index.html`, not recreated
- [ ] WhatsApp FAB is copied from `index.html`, not recreated
- [ ] Hamburger script is copied from `index.html`, not recreated

---

## Gift-it Voice Guide

Use this when generating copy in Phase 5.

**Do** write like this:
> "Submit your employee list and we handle the rest — sourcing, packing, delivery."
> "Delivered to 19,000+ pincodes. Fully tracked."
> "You get a clean invoice. No hidden fees."
> "5 pilot slots. Bengaluru companies only. First come, first served."

**Don't** write like this:
> "We provide end-to-end solutions for your gifting needs."
> "Our platform leverages best-in-class vendors."
> "Seamlessly integrate with your existing workflows."
> "Empowering HR teams to deliver delightful experiences."

Rules: short sentences. Specific numbers. Indian context. Action verbs.
No buzzwords. No passive voice. No em-dashes as decoration.
