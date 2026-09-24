---
name: design-from-reference
description: Design a new page that serves the same purpose as a given reference, without copying or borrowing from its visual style. The reference is used only to extract the page's objective. All design decisions come from design-moves.md and the user's own constraints. Use when the user provides a reference and wants a fresh, professional page built for the same purpose. Triggers on: "redesign this", "same purpose but different UI", "make something that does what this does", "rebuild this page", "reference for inspiration", "use this as reference".
---

# Design From Reference

The reference is a purpose signal, not a design input. It tells you what the page needs to accomplish. The moment that purpose is confirmed, the reference is set aside. Everything from that point — structure, visual direction, components, type, color — comes from the design vocabulary in `design-moves.md` and the constraints the user provides.

Follow the six phases in order. Phases 0–2 are gates. Do not proceed past each until the output is confirmed.

---

## Phase 0 — Extract & Verify Purpose

The only thing the reference contributes is purpose. Extract it, confirm it matches the target, then close the reference.

**Step 1 — Extract the reference's purpose.**
From the reference (URL, screenshot, or description), answer:
- Who is this page for?
- What is the one thing a visitor comes here to do or understand?
- What decision or action does the page drive?

State as one sentence: *"This reference page exists to [action/outcome] for [audience]."*

**Step 2 — Extract the target's purpose.**
From what the user has told you, answer the same three questions for what they want to build.

State as one sentence: *"The page I'm building exists to [action/outcome] for [audience]."*

**Step 3 — Compare and gate.**

- **Purposes match** → confirm alignment with the user in one line. Proceed to Phase 1.
- **Purposes don't match** → stop. Tell the user what purpose you extracted from each, explain the mismatch, and ask:
  1. Was the reference chosen incorrectly — do they have a better one?
  2. Is the target's purpose different from what you understood — can they clarify?
  3. Is the reference just loose inspiration for a different purpose — in which case this skill is the wrong tool.
- **Target purpose is unclear** → stop. Ask directly: What will visitors come here to do? Who are they? What should they leave having done or understood?

Never assume the purposes match because the user handed you a reference.

---

## Phase 1 — Understand the Content Need

Purpose is confirmed. Now use the reference — for the last time — to understand what content blocks a page of this type typically requires. Look at content function only. Ignore layout, colors, typography, and visual style entirely.

Answer these questions:

**1.1 What content blocks does this type of page need?**
List each block by its job, not its appearance. Example: "A section that establishes credibility before asking for commitment" — not "a testimonials carousel".

**1.2 What is the information hierarchy?**
Order the blocks: what does the user need to understand first, second, third? Rank them 1 through N.

**1.3 What is the primary action?**
One action. What is the single thing the page should move the user toward?

**1.4 What user hesitation does the page need to address?**
What would make the target user not take the action? Name the 1–2 real objections the content needs to answer.

After completing 1.1–1.4, the reference is no longer referenced in any subsequent phase.

---

## Phase 2 — Gather User Constraints

Before any design decisions are made, ask the user for the following. Do not proceed to Phase 3 until you have answers — or explicit confirmation that they have no preference on a given item.

Ask these as a single grouped message, not one at a time:

1. **Brand color** — is there an existing accent color, brand palette, or hex code to use? Or should the design pick one from scratch?
2. **Tech stack** — what is this being built in? (HTML/CSS, React, Next.js, etc.) This affects token naming and component approach.
3. **Existing content** — is there copy, images, or content already written that must be used? Or is the agent generating content from the purpose?
4. **Mode preference** — dark, light, or no preference?
5. **Hard constraints** — anything that must be in the design (a specific section, a required element) or must not be (no modals, no carousels, etc.)?

If the user says "no preference" or "up to you" on any item — record that and make the decision yourself in Phase 4. Do not ask again.

---

## Phase 3 — Select a Design Move

Read `design-moves.md` in full. Then answer the three selection questions from that file:

1. **Who is the primary reader?** (Developer / Designer / Consumer / General user)
2. **What is the page's job?** (Persuade technically skeptical users / Show craft and confidence / Lower barriers / Build brand over time)
3. **What would be unexpected here?** What move does no one in this product's category use?

Based on your answers, select one move as the primary direction. A second move may inform a single detail — never combine more than two.

**Present to the user:**
- The move name
- Why it fits the purpose and audience
- What design constraints it imposes
- One sentence on what makes it unexpected or non-obvious for this context

Then wait for confirmation. If the user wants a different move, accept it, update your reasoning, and proceed. Do not start the Design Plan until the move is confirmed.

---

## Phase 4 — Write the Design Plan

The Design Plan is derived entirely from: the confirmed purpose (Phase 0), the content need (Phase 1), user constraints (Phase 2), and the confirmed Design Move (Phase 3). The reference does not appear here.

Fill every field. Vague entries ("good spacing", "clean layout") are not acceptable. If you are making the decision yourself, make it specific and state it as a decision.

```
DESIGN PLAN
===========

Page purpose (one sentence):


Selected Design Move:
Move-specific constraints applied:
  -
  -
  -


Content blocks (ordered by hierarchy, from Phase 1):
  1.
  2.
  3.
  4.


Primary action the page drives:


User hesitations the content addresses:
  1.
  2.


Visual mode:      [ ] Dark   [ ] Light   [ ] System-respecting
Decision source:  [ ] User specified   [ ] Agent decision (reason: )


Type system:
  Display:    [family · size · weight · line-height]
  Body:       [family · size · weight · line-height]
  Label/meta: [family · size · weight]
  Rule: one family. Two weights max in body copy. Move constraints take precedence.


Color system:
  Background:   [hex — NOT AI beige, NOT warm cream unless Move 4 or 7]
  Surface:      [1 step from background]
  Text primary: [hex · contrast ratio vs background]
  Text secondary: [hex · contrast ratio]
  Accent:       [hex · used for: CTAs only / links only / status only]
  Border:       [hex — subtle, structural, never decorative or colored]
  Source:       [ ] User-provided   [ ] Agent-selected (move-justified)


Spacing rhythm:
  Base unit:  8px
  Section gap:    [n × 8px]
  Component gap:  [n × 8px]
  Element gap:    [n × 8px]


Layout:
  Grid:           [columns · max-width · gutter]
  Prose max-width: 68ch
  Hero composition: [specific description — not "centered hero with gradient"]
  Mobile behavior:  [specific — not just "responsive"]


Density:
  [ ] Editorial — generous whitespace, large type (landing, marketing)
  [ ] Balanced  — moderate density, clear sections (docs, product page)
  [ ] Product   — compact, information-forward (app, dashboard)


Three non-obvious decisions:
  1. [Specific, unexpected — something that signals the design was thought, not generated]
  2. [A constraint that creates discipline]
  3. [A type or layout choice that signals craft]
```

Do not proceed to Phase 5 until every field is filled.

---

## Phase 5 — Build

Build order is fixed. Do not compress or reorder steps.

1. **HTML structure first.** No CSS. Document order must match content hierarchy from the Design Plan. Reading order = DOM order.
2. **Typography tokens.** CSS custom properties for all sizes, weights, line-heights. Apply globally before any layout.
3. **Color tokens.** `--color-bg`, `--color-surface`, `--color-text-primary`, `--color-text-secondary`, `--color-accent`, `--color-border`. Apply globally.
4. **Spacing scale.** `--space-1` through `--space-16` (multiples of 8px). Every margin, padding, and gap uses these tokens.
5. **Layout.** CSS Grid or Flexbox. No absolute positioning for content blocks.
6. **Components.** Style each component in isolation before composing the page. Apply the Move's specific constraints during this step.
7. **Interactions last.** Hover, focus, transitions. Move constraints govern what is and isn't allowed.
8. **Final pass.** Run the checklist in `patterns.md` before handing off. Zero exceptions.

---

## Additional resources

- Design move vocabulary and selection guide: [design-moves.md](design-moves.md)
- Anti-pattern catalog and final checklist: [patterns.md](patterns.md)
