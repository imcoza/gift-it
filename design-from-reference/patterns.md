# Anti-Pattern Catalog & Detector Checklist

Use this as a final pass before any design is considered complete. Every item below is a red flag. If any apply, fix them before shipping.

---

## Category 1 — Typography Tells

| Pattern | Why it's a tell | Fix |
|---|---|---|
| Italic serif display headline | Signals "AI editorial aesthetic" — every generator defaults to this | Use weight contrast on the same sans-serif family |
| All-caps body text with wide letter-spacing | Overused in SaaS templates 2021–2024 | Use normal-case with a clear weight hierarchy |
| Gradient text (background-clip: text) | AI generation default for "premium" | Use solid color or weight contrast |
| Multiple font families (3+) | Signals "found these on Google Fonts" | One family, two weights max in body |
| Thin fonts (weight 100–200) for body copy | Unreadable at small sizes, overused in minimal templates | Use 400 for body, 300 only for display above 48px |
| Body copy wider than 75 characters | Reader loses their place | `max-width: 68ch` on prose containers |
| Every section uses a different font treatment | No system, just decoration | Establish a scale and stick to it |

---

## Category 2 — Color Tells

| Pattern | Why it's a tell | Fix |
|---|---|---|
| AI beige / warm cream background (`#F5F0EB` range) | Default "natural tech" palette every LLM produces | Neutral white `#FAFAFA` or intentional dark |
| Purple gradient CTA button | The most common AI-generated button | Solid accent color, no gradient |
| "Electric" colors on dark background (neon green, hot pink) | The other default "premium dark mode" tell | Desaturated accent, 60–70% saturation max |
| Rainbow feature grid (icon1 blue, icon2 green, icon3 orange…) | No color logic, just visual noise | Monochromatic icons or single accent |
| Colored section backgrounds (alternating blue, white, purple) | Template inheritance | Single background with stroke separators |
| Semi-transparent colored borders (`border: 1px solid rgba(255,255,255,0.1)`) used everywhere | Makes everything look the same | Use color tokens with intention, not by default |
| Accent color on headings | Reduces hierarchy, not increases it | Accent on CTAs and links only |

---

## Category 3 — Layout & Component Tells

| Pattern | Why it's a tell | Fix |
|---|---|---|
| Hero eyebrow pill chip ("🚀 Introducing X") | Every SaaS launch page since 2022 | If you must label the category, use plain small caps text |
| Three features in a row with icons above text | The default grid pattern | Alternating layout or numbered list approach |
| Nested cards (card inside card inside card) | Confuses visual depth | Cards at one level only |
| Decorative pulsing status dot | "Active" theater | Use a static dot or plain text label |
| Side-tab accent border (4px left border, color) | Over-used "selection" pattern | Use background fill or a plain left margin |
| "Floating" cards with heavy shadows and blur | Depth theater | Flat cards with stroke border |
| Full-bleed section background just to add contrast | Template padding | Use vertical whitespace for separation |
| Testimonial avatar + name + company + star rating + quote in a card | Generic social proof template | One strong quote, flush left, source as footnote |
| CTA section with two buttons + subtitle + illustration | Default "bottom of page" template | Single CTA, one line of supporting text |

---

## Category 4 — Interaction & Motion Tells

| Pattern | Why it's a tell | Fix |
|---|---|---|
| Scale-up on hover (`transform: scale(1.05)`) on cards | Default Tailwind hover effect | `opacity` change or `translateY(-2px)` if needed |
| Scroll-triggered fade-in with stagger on every element | Every landing page builder does this | Reserve animation for meaningful state changes |
| Background blur on sticky header | Performance cost + visual noise | Solid background with a subtle border |
| Loading skeleton everywhere, including on static content | Over-engineered for content that doesn't load | Only on genuinely async content |
| Button "glow" effect on hover (box-shadow with color) | Template effect | Remove or use a clean border transition |

---

## Category 5 — Content & Copy Tells

| Pattern | Why it's a tell | Fix |
|---|---|---|
| Headline formula: "The [adjective] way to [verb] your [noun]" | Every SaaS headline from 2020–2025 | Make a direct claim or ask a direct question |
| Feature named with an em dash: "Fast — and beautiful" | AI copywriting pattern | Plain sentence: "Fast and built to last." |
| "Built for [persona]" as a section headline | Generic | Name the actual use case the person has |
| Bullet points that start with bold fragment + dash | "**Speed** — ship faster" | Either prose or a table, not hybrid |
| Subheadline that restates the headline | "The fastest tool. Work faster than ever." | Subheadline must add information, not echo |

---

## Final Checklist

Run this before handing off the design:

**Typography**
- [ ] One type family throughout
- [ ] Maximum 2 different weights in body text
- [ ] Display headline is not italic serif
- [ ] No gradient text
- [ ] Prose containers have `max-width` set
- [ ] Line heights are readable (1.5× for body, 1.1× for display)

**Color**
- [ ] Background is not AI beige (`#F5F0EB` range)
- [ ] Accent color appears on at most two element types
- [ ] No gradient on buttons or CTAs
- [ ] Borders are subtle (not colored, not decorative)
- [ ] Text has clear primary/secondary contrast (not everything the same weight or opacity)

**Layout**
- [ ] No three-icon feature grid
- [ ] No hero eyebrow pill chip
- [ ] No nested cards
- [ ] No decorative pulsing elements
- [ ] Content width is bounded (not stretching to full container on wide screens)
- [ ] Single CTA per section

**Code quality**
- [ ] Color, type, and spacing use CSS custom properties (not hardcoded hex in every rule)
- [ ] Document order matches reading order (no CSS reordering of content)
- [ ] Hover states have purpose, not just a visual effect
- [ ] Focus styles are visible (not removed)
- [ ] No inline styles for layout — all structural CSS is in stylesheets

---

## Inspiration Reference

These sites demonstrate the principles in this skill. Study their decisions, not their aesthetics:

- **Linear** (linear.app) — precision spacing, dark-as-default, typography as navigation
- **Vercel** (vercel.com) — true-black dark, single accent, CLI aesthetic as content
- **Stripe** (stripe.com) — gradient only on hero, rich product content, consistent blue system, editorial type scale
- **Raycast** (raycast.com) — dark mode done correctly, interface screenshots as the hero, no decorative illustration
- **Craft** (craft.do) — light mode done correctly, editorial whitespace, content-first layout

Study what each of them does *not* do. The restraint is the design.
