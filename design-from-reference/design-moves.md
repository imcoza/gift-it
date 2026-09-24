# Design Moves Vocabulary

Read this during Phase 2 when filling the Design Plan. Use it to name a specific visual direction for the new page — one that fits the page type and purpose without copying any single site.

Each entry names the move, describes what makes it work, and lists sites that demonstrate it well. Pick one move as the primary direction. A second move can inform a detail — never combine more than two.

---

## Move 1 — Product UI as Hero

**What it is:** The actual interface (screenshot, live component, or working demo) sits at the center of the page. No illustration, no abstract graphic — the product earns attention by being real.

**Why it works:** Immediately shows rather than tells. Developers and builders trust what they can see functioning. Removes the gap between "what you claim" and "what it actually is."

**When to use:** Developer tools, SaaS products, apps with a strong visual identity. Any page where the target user is skeptical of marketing language.

**Design constraints it imposes:**
- Background must recede — dark, neutral, or blurred so the UI pops
- Typography stays out of the way of the product: smaller, secondary
- No decorative illustration — if you add one, you've undermined the move

**Sites that do this well:**
- **Raycast** (raycast.com) — macOS app window floats on dark; extension cards look like a real screen
- **Clerk** (clerk.com) — the `<SignIn />` component IS the hero, styled exactly as it ships
- **Resend** (resend.com) — terminal output (`HTTP 200: {"id": "..."}`) scrolling vertically; the API response is the visual
- **Linear** (linear.app) — actual issue view and agent thread are the marketing content

---

## Move 2 — Terminal / Code Output as Visual

**What it is:** CLI responses, API JSON, code snippets, or build logs are treated as graphic elements — given space, scale, and typographic weight usually reserved for headlines.

**Why it works:** Signals that the product was built by developers, for developers. The "output" demonstrates capability without requiring explanation.

**When to use:** Infrastructure, APIs, CLIs, developer platforms, anything where the primary user writes code for a living.

**Design constraints it imposes:**
- Monospace font must be large enough to read at a glance (≥14px, often 16–18px)
- Background should be dark or near-black — this is terminal territory
- Keep surrounding layout sparse so the code has room to breathe
- No rounded colorful cards — defeats the raw signal

**Sites that do this well:**
- **Resend** (resend.com) — `HTTP 200` responses as the scrolling hero
- **Vercel** (vercel.com) — `▲ vercel deploy` CLI output beside product screenshots
- **Impeccable** (impeccable.style) — `/impeccable polish` commands in an agent thread UI

---

## Move 3 — Monochrome Brutalism

**What it is:** True black or very dark background. White or off-white text only. Zero accent color. Typography at extreme scale (80–120px+) does all the heavy lifting.

**Why it works:** Forces everything irrelevant out of the design. The ideas have to hold weight on their own. Signals confidence — the work doesn't need decoration.

**When to use:** Agencies, studios, editorial content, portfolios of very strong work. Dangerous for SaaS — can read as inaccessible to non-designers.

**Design constraints it imposes:**
- One typeface. One weight range (regular + bold only).
- No gradients, no images unless they're photographic and full-bleed
- Every element earns its place — if it can be removed, remove it
- Interactions must be deliberate: hover reveals, not hover glows

**Sites that do this well:**
- **basement.studio** — full-bleed white text on true black at 80px+; logo bar as only structure
- **paco.me** — radical text-only; two-column layout; a single italic serif as the only flourish
- **Linear changelog** — "Now" as a single 120px word; the date and entry below; nothing else

---

## Move 4 — Committed Warm Dark (Not Black)

**What it is:** Background is a deep warm tone — dark brown, forest green-black, muted olive, or deep slate — rather than the default `#0a0a0a`. It reads as dark but has character.

**Why it works:** Stands out from every other dark-mode site while staying sophisticated. Warm dark backgrounds are much rarer than neutral dark, making the site instantly recognizable.

**When to use:** Creative tools, indie software, studios with a strong craft identity. Doesn't work for enterprise — feels too artisanal.

**Design constraints it imposes:**
- Commit to the warm tone across all surfaces — mixing warm and cool reads as accidental
- Accent color should be muted and warm (sage, ochre, terracotta) — never electric blue or neon
- Typography should complement: a slightly warm white (`#F5F0EB` range) works; pure `#FFFFFF` looks harsh
- No shadows — surfaces are flat, defined by tone difference only

**Sites that do this well:**
- **Neco Studio** (neco.studio) — deep warm brown-black (`#1a1a14` range); sage green CTA; custom logotype
- **Stripe Press** (press.stripe.com) — near-black top; transitions to cream below; photographic book spines

---

## Move 5 — 3D World as Navigation

**What it is:** The page itself is a 3D environment. Content is discovered by moving through a rendered space — not by scrolling.

**Why it works:** Transforms passive browsing into an experience. Memorable by design. Works as a statement about technical capability.

**When to use:** Portfolios of creative developers or studios whose identity IS technical creativity. Does not translate to commercial products — frustrates users who want to find information quickly.

**Design constraints it imposes:**
- The 3D environment must be fast (< 3s to interactive)
- Must have a flat fallback or non-interactive path for accessibility
- Lighting, physics, and audio (if included) must be intentional — not default three.js settings

**Sites that do this well:**
- **Bruno Simon** (bruno-simon.com) — driveable Three.js world; title spelled in 3D letters on the ground
- **Lusion** (lusion.co) — pure WebGL; project thumbnails are live 3D scenes; zero UI chrome

---

## Move 6 — Deliberate Cultural Identity

**What it is:** The site embeds a specific cultural or geographic aesthetic — typography, script, color, or art direction that signals a clear origin or creative tradition rather than "global tech default."

**Why it works:** Impossible to imitate with a template. The identity comes from knowing something deeply rather than applying a style trend.

**When to use:** Agencies and studios with a genuine cultural point of view. Works for creative, fashion, and cultural brands. Needs to be earned — never applied as decoration.

**Design constraints it imposes:**
- Every element must be consistent with the cultural direction — no mixing
- Typography from that culture's tradition, not just a "foreign" font as ornament
- Motion and interaction should follow the same aesthetic logic

**Sites that do this well:**
- **monopo.london** — Tokyo-born agency in London; Japanese type inside a glass sphere; navy/orange fluid blob; three-city live clock in nav

---

## Move 7 — Consumer Warmth on a Technical Product

**What it is:** A product that is genuinely complex (crypto, auth, infrastructure) is presented with the visual language of a consumer app — clean white, friendly typography, real illustrations, conversational copy.

**Why it works:** Lowers the emotional barrier to entry. The design signals "this is for you" to people who would otherwise assume they're not technical enough.

**When to use:** Products targeting a broader audience than their technical category usually reaches. Financial tools, crypto, security, developer tools with a consumer tier.

**Design constraints it imposes:**
- White or very light background — dark signals "for experts"
- Typography must be approachable: rounded corners on buttons, generous padding
- No jargon in headlines — the copy must match the visual warmth
- Icons and illustrations should be custom, not generic Heroicons

**Sites that do this well:**
- **Family** (family.co) — crypto wallet; pure white; rounded coin illustrations; "Your favorite crypto wallet" as headline
- **Craft** (craft.do) — productivity app; warm sage green; real user notes (sourdough, travel) as the illustrations

---

## Move 8 — Editorial Publication Layout

**What it is:** The site is structured like a magazine or book — strong typographic scale, issue numbers, a named section ("Now", "Vol. 2"), dates as primary navigation elements.

**Why it works:** Signals craft, longevity, and intellectual seriousness. Makes a software product feel like something worth reading rather than something to sign up for.

**When to use:** Changelogs, documentation, company blogs, products that want to be associated with ideas and culture rather than just features.

**Design constraints it imposes:**
- One clear type hierarchy: a display scale for titles, a reading scale for body — no in-between
- Dates and section markers are structural, not decorative
- Photographs or video should be editorial quality — no stock
- No cards — use prose layout with breathing room

**Sites that do this well:**
- **Linear changelog** (linear.app/changelog) — "Now" at 120px; date-driven entries; category filter as nav
- **Stripe Press** (press.stripe.com) — book spines as the entire hero; serif + precision; no product screenshots at all

---

## How to pick during Phase 2

Answer these three questions:

1. **Who is the primary reader?** Developer → Move 1 or 2. Designer/creative → Move 3 or 6. Consumer → Move 7. General user → Move 8.

2. **What is the page's job?** Persuade technically skeptical users → Move 1 or 2. Show craft and confidence → Move 3, 4, or 6. Lower barriers → Move 7. Build brand over time → Move 8.

3. **What would be unexpected here?** The best choice is often the move no one in the product's category is using. If every competitor uses dark product screenshots (Move 1), try editorial layout (Move 8). If every competitor uses consumer warmth (Move 7), try monochrome brutalism (Move 3).

Name your chosen move in the Design Plan under "Visual mode" and "Three non-obvious decisions."
