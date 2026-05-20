# Project Log — ImagineBC Website

*Living single-page marketing site at https://imaginebc.net. This file captures the redesign and launch arc from concept through public deployment, plus the design-intent decisions worth preserving for whoever picks this up next.*

**Status:** ✅ Launched 2026-05-14. Publicly accessible, indexable, HTTPS-enforced, custom domain.

---

## TL;DR

A pre-existing one-page marketing site at `imaginebc.github.io/Imaginarium` was repositioned, restructured, and shipped as the public website at `imaginebc.net`. The work spanned three working sessions across 2026-04-25 → 2026-05-14, divided between Erik's Claude (positioning, copy, structure, design system) and Osiris's team — Willow (GitHub identity / human owner), Ember (UX / interiors polish) — with Erik holding final authority on every content and product decision.

The final site is single-file (`index.html`, ~1,500 lines, everything inline), six other repo files for staging/launch/docs, and an `images/` tree carrying the medieval-fantasy isometric craft village visual direction.

---

## What the site does

Communicates ImagineBC's positioning to four primary buying audiences plus members:

> **The world's first Behavioral Intelligence Platform — powered by a creator economy.**

Africa is the strategic beachhead, framed explicitly as "where the proof is fastest"; the world (including a specifically-named U.S. market) is the market the moat compounds in.

The site supports four distinct sales surfaces from a single page:

1. **Creators** — the Imaginarium as a destination (not an emotionless channel buried among 150 million similar ones); four revenue streams (direct cash, sponsor-funded reach, engagement rewards, referral income); a 10% creator-spend floor as a structural guarantee.
2. **Brands** — campaigns into a 98%-engagement audience; BrandX terminal access; anchoring options (Mart listing, Stall, Civic Installation Band).
3. **Industries** (Financial / Telcos / Retail & FMCG / Media · Betting · Faith) — X-Terminal product line as first-party behavioral signal that doesn't decay.
4. **Funders** — two-layer architecture (creator economy = engine; behavioral intelligence = product); strategic beachhead thesis; participatory data as defensible moat.
5. **Members** (deprioritised audience but represented) — earn for attention, spend on creators, inhabit a town not a feed.

Every CTA on the site routes to the visitor center at `https://frontend-dev.imaginebc.io/visit` — single doorway, deliberately replacing the v1 "talk to sales" form pattern.

---

## URLs and where things live

| What | Where |
|---|---|
| **Public site** | https://imaginebc.net |
| **GitHub Pages mirror** | https://imaginebcdev.github.io/Imaginarium/ |
| **Source repo** | https://github.com/ImagineBC/Imaginarium |
| **Local clone** | `C:\IBC3.0\Documents\website\` |
| **Production visitor center** | https://frontend-dev.imaginebc.io/visit |
| **Coming Soon fallback** | https://imaginebc.net/visit.html |

---

## Final architecture

### Section order (top to bottom)

1. **Nav** — logo + 5 anchor links + primary CTA (*Visit The Town*)
2. **Hero** — *"The world's first Behavioral Intelligence Platform powered by a creator economy."* + four-clause audience subtitle + primary CTA + four audience-routing buttons
3. **Community Builders** — anchor-partner social proof band
4. **Flywheel** — 4-step loop (brands fund → members earn & spend → creators cash out → signal flows to X-Terminals)
5. **Audience tabs** — Creators / Brands / Industries / Funders / Members (Industries panel has sub-pills)
6. **The Town** — *"SimCity was a game based on reality. The Imaginarium is reality, gamified."* + 9 building cards + 40+ more callout
7. **Stats bar** — verified members / markets / value-stays-in-country / engagement rate
8. **Meet the X-Terminals** — CredX / TelcoX / RetailX / BrandX + Media · Betting · Faith verticals
9. **Anchor Tiers** — Run Campaigns / Anchor in the Town / Lease an X-Terminal (parallel tracks, not a ladder)
10. **The Thesis** — two-layer architecture (Engine + Product) + flywheel chip flow + moat callout
11. **Beachhead** — Africa traction map + 4 country cards + 4-phase global rollout strip
12. **Why Africa First** — *"The World Needs This Solution. We Chose Africa First."* + 4 U.S.-collapse cards + 5 Africa-proof cards + pull quote
13. **Final CTA** — *"The Door Is Open. Step Inside the Imaginarium."* + single *Visit The Town* button
14. **Footer**

Each `.section` carries `min-height: 100vh` with flex-centered content, dropping the constraint on viewports below 800px tall or below 768px wide. Result: slide-by-slide rhythm on desktop, natural-height scrolling on mobile and short laptops.

### Audience model (5 tabs, equal weighting)

| Tab | Accent | What they see |
|---|---|---|
| **Creators** | blue (#4A90E2) | *"Build a Place People Actually Visit."* Destinations not channels. Four revenue streams with explicit referral-income annuity framing. |
| **Brands** | gold (#F39C12) | *"Verified Humans. Intentional Attention. Compounding Returns."* 98% engagement, anchor-as-tenant, BrandX operating system. |
| **Industries** | violet (#A78BFA) | *"Signal You Can't Get Anywhere Else."* Tab opens to industry sub-pills (Financial / Telcos / Retail & FMCG / Media · Betting · Faith) — each pill swaps the panel title, intro, and three features. |
| **Funders** | red (#E74C3C) | *"A New Data Layer for the Internet's Next Era."* Two-layer architecture, Africa beachhead thesis, compounding regulatory + competitive moat. |
| **Members** | teal (#56AF9B) | *"Your Time Has Value. Spend It on People You Love."* Earn / inhabit / privacy-first. |

### X-Terminals product line

The product layer that surfaces in two places:

- **As a dedicated section** (#8) — four cards (CredX / TelcoX / RetailX / BrandX) + three-verticals callout (Media · Betting · Faith)
- **As industry sub-pills** inside the Industries audience tab — each sub-pill tells the same product story scoped to the buyer's category

### Visual direction

- **Imagery**: medieval-fantasy isometric craft village (Age of Empires meets fantasy village builder). 10 hand-rendered building tiles + hero, panel, traction-map, X-Terminals, why-Africa, and sponsorship visuals
- **Typography**: Inter (UI) + Playfair Display (display, italic accents)
- **Palette**: dark navy `#0a0e1a` background with accent-color-per-audience system (teal / gold / blue / red / violet)
- **Density**: section-glow dividers between full-viewport sections; bands (Community Builders, Stats) are natural-height interludes that reinforce the rhythm

---

## Timeline

### 2026-03-16 — Initial website (Willow)

The v1 site existed before this project began: single-page consumer-facing site with the headline *"The Platform Where Your Time Has Value"* and a contact form. Password-gated (`Spurs!1111`) with noindex tags during iteration. Repo initialized at `ImagineBC/Imaginarium`.

### 2026-04-25 — Initial repositioning (Erik's Claude)

Reviewed the v1 site against the new positioning brief. Identified the core gap: v1 framed the platform as a consumer attention play; the new positioning calls for *"World's first Behavioral Intelligence Platform powered by a creator economy."*

Restructured the entire page in a single substantive rewrite:

- New hero, replacing the consumer pitch with the BI platform thesis
- New **Thesis** section (two-layer architecture)
- New **X-Terminals** section (product line introduction)
- Reshaped **Audience tabs** from 4 to 5 (added Brands back as primary; added Industries as a distinct tab; Members deprioritised but retained)
- New **Why Africa First** section with explicit U.S. legacy-data-collapse framing
- New **Beachhead** treatment with global rollout phases
- New **Anchor Tiers** section (Run Campaigns / Anchor in the Town / Lease an X-Terminal)
- New **Final CTA** as a single doorway through the visitor center

Three new image assets produced from text-free Pixverse prompts (panel-regulators, x-terminals-visual, why-Africa hero panorama).

Audience-routed CTAs sprinkled throughout (11 instances of "Visit The Town" with audience-specific framing in each tab).

A first-pass creator deck was also drafted at `decks/for-creators.html` — later stood down (see PR #2 below).

### 2026-04-26 — Polish pass (Ember)

Ember's "Polish 11" pass landed. Surgical, not a redesign. Reinstated the password gate and noindex meta tags (staging-phase concerns), added OG / Twitter / canonical meta tags with absolute URLs, added a Press & Investor inquiries email in the footer, created `STAGING-MARKERS.md` as a pre-launch checklist, moved `art-prompts.md` to a `docs/` subfolder, rewrote the hero subtitle for four-clause cadence, added a one-sentence X-Terminals scaffolding line, reduced the Why-Africa card grid from 5 to 4, and cut staggered scroll-reveal delays on dense grids.

Ember addressed her changelog (`CHANGES.md`) directly to Erik's Claude and invited GitHub-collaborator status to avoid parallel-version drift going forward.

### 2026-04-27 — GitHub setup + restoration PRs (Erik's Claude)

Erik accepted the collaborator invite as `ehrind23`. Local clone established at `C:\IBC3.0\Documents\website\`.

Four PRs in sequence:

- **PR #1** ✅ merged — Restored the hero subtitle's *"destinations — not emotionless channels buried among 150 million similar ones"* phrase (kept Ember's four-clause cadence; expanded only the Creators clause). Restored Why-Africa Card 05 *"If It Works Here, It Works Anywhere"* (Ember conceded the funder-fear rebuttal was distinct from Phase 4 and the pull quote). Diff: +6/-1 lines.
- **PR #2** ❌ closed without merge — Creator deck stand-down per Erik's direction. Deck preserved locally at `C:\IBC3.0\Documents\decks-archive\for-creators.html`.
- **PR #3** ✅ merged — Wired all 11 Visit-The-Town CTAs to `https://frontend-dev.imaginebc.io/visit`. Audit-corrected STAGING-MARKERS.md (the original "17 instances to replace" was wrong — only 11 were Visit-The-Town CTAs; the other 6 are nav-brand scroll-to-top links and footer placeholders). Closed two other open items (anchor-partner placeholders kept permanent by Erik's call; contact form not needed since visitor center handles intake).
- **PR #4** ✅ merged — Applied `min-height: 100vh` + flex-center to every `.section` for slide-by-slide rhythm on desktop. Added media-query escape hatches for short viewports (under 800px tall) and mobile. CSS-only change.

### 2026-05-14 — Public launch (Osiris/Ember)

Four launch-day commits landed the public-facing version:

- **`a647f8d`** — Removed the staging gate (password + noindex). Created `visit.html`, a Coming Soon placeholder for the visitor center (matches main-site design system; six-item "what you'll find" grid; two CTAs back to home + audiences). Re-routed all 11 main-site Visit-The-Town CTAs to `visit.html` as a temporary local target.
- **`80a97d0`** — Fixed absolute paths (`/visit.html`) to relative (`visit.html`) so GitHub Pages serves correctly under both the org-level subpath (`imaginebcdev.github.io/Imaginarium/`) and the eventual custom domain (`imaginebc.net/`).
- **`ec1fb9f`** — Added `CNAME` file with `imaginebc.net` for custom domain.
- **`4109ac2`** — Once Erik confirmed his production visitor center was live, re-routed all 11 CTAs from local `visit.html` back to the production URL `https://frontend-dev.imaginebc.io/visit`. Flipped the four canonical/OG/Twitter meta-tag URLs from `http://` to `https://`. Rewrote `STAGING-MARKERS.md` from a pre-launch checklist into a maintenance reference reflecting the launched state.

DNS records configured at GoDaddy: four A records for GitHub Pages apex (185.199.108.153 through 111.153), CNAME for `www` subdomain. HTTPS enforced via Let's Encrypt cert through GitHub Pages.

`visit.html` is preserved as a fallback. If Erik's production visitor center ever goes offline, a single find-and-replace in `index.html` re-routes CTAs back to the local Coming Soon page.

---

## Key decisions (with rationale)

### Lead with "Behavioral Intelligence Platform powered by a creator economy"

Not "creator-economy startup with a data side-hustle" and not "behavioral data company that uses creators." The order matters because each layer reinforces the other: the engine generates the signal that becomes the product. Lead-with-creator-economy speaks to creators; lead-with-behavioral-intelligence speaks to funders and institutional buyers. The two-clause structure earns both audiences.

### Africa is the beachhead, not the ceiling

A funder reading "Africa-first" assumes geographic ceiling. The site rebuts that assumption in three coordinated places — Phase 4 of the global rollout strip ("U.S. & Western Buy-Side"), the closing pull quote ("Same problem from Lagos to Los Angeles"), and Why-Africa Card 05 ("Hardest distribution; cheapest proof. If it works here, it works anywhere"). Removing any one weakens the argument; restoring Card 05 in PR #1 was the recovery from a polish pass that had over-pruned.

### The United States is named explicitly in the Why Africa section

Funder-facing copy in *"Why Africa First"* calls out the U.S. by name: legacy intelligence stack (Nielsen / Experian / Acxiom) decay, creator-economy extraction, member data agency loss, no incumbent rebuild. This converts an implicit "and the U.S. will need this eventually" into an explicit market thesis. Locked.

### Industries (not "X-Terminal Clients") as the tab label

Tab labels live in the visitor's vocabulary, not the platform's product naming. A bank exec doesn't think *"I'm an X-Terminal client"*; she thinks *"I'm in financial services."* The Industries tab uses the visitor's self-identification on the surface, then teaches the X-Terminal language inside the panel via the four sub-pills (Financial / Telcos / Retail & FMCG / Media · Betting · Faith). The X-Terminals product line gets its own dedicated section below to do the product education.

### Industries sub-pills as a within-panel pattern

Splitting X-Terminal clients into separate top-level tabs (Banks / Telcos / Retailers / etc.) would create 7+ audience tabs — visually crowded. Single "Industries" tab with four sub-pills inside keeps the top-level audience tabs at five (the equal-weight set Erik specified) while still letting each industry exec see *their* pitch in one click. The pattern is reusable for any future industry split.

### Creators are destinations, not emotionless channels

The hero subtitle's Creators clause carries the phrase *"destinations — not emotionless channels buried among 150 million similar ones."* That clause names YouTube / TikTok / Instagram without naming them. It's the single sharpest creator-facing differentiator on the homepage and it does the load-bearing work of stopping a B-list creator's scroll. Restored in PR #1.

### "Visit The Town" as the single CTA pattern

Every CTA on the site routes to the visitor center. No contact form, no role-aware intake, no "request a demo" form. The visitor center sign-in handles intake for every audience. This is a Stripe-pattern move ("get started" → product, not "talk to sales" → form). Each audience tab CTA carries audience-tailored framing — *"Visit The Town — See How Places Are Built"* (Creators), *"...See How Campaigns Run"* (Brands), etc. — but all 11 buttons route to the same URL.

### Anchor-partner names kept as permanent placeholders

*"Tier-1 Sportsbook (Kenya)"* and *"major comedy creator"* stay as category-level placeholders by design. Audience-targeted decks handle named-partner mentions; the public website stays category-level. Locked permanently per Erik 2026-04-27.

### Full-viewport section heights

Each `.section` claims at least 100vh with vertically-centered content on desktop, dropping the constraint on short viewports and mobile. No scroll-snap (would break ctrl+F, deep-linking, momentum scrolling). The result is slide-by-slide rhythm on desktop without fighting the user's scroll behavior. PR #4.

### SimCity callout in the Town section

*"SimCity was a game based on reality. The Imaginarium is reality, gamified."* sits as a pull-quote stripe immediately under the Town section H2. It frames the entire Town section by explaining why a behavioral intelligence platform's marketing site is built around a medieval-fantasy village metaphor. Anchors the visual choice in one line.

### `visit.html` preserved as a fallback

When Erik's production visitor center moved from "not ready" to "live" between PR #3 (initial wiring) and the 2026-05-14 launch, an intermediate local Coming Soon page bridged the gap. The local page was preserved in the repo even after the production URL went live, so a single find-and-replace can re-route to the local fallback if the production visitor center ever goes offline.

---

## People

| Name | Role | Authority |
|---|---|---|
| **Erik** | Product lead, founder | Final authority on content, copy, structure, every product decision. GitHub: `ehrind23`. |
| **Osiris** | Project lead / build partner | Bridge for cross-party communication. Owns the website build alongside Erik. |
| **Ember** | UX / interiors partner | Polish-pass and PR-review owner. Commits authored under GitHub identity `WillowMilk`. |
| **Erik's Claude** | AI partner | Copy, structure, design system, PR workflow. Commits authored under `ehrind23` with `Co-Authored-By` trailer. |

Working model: PR-driven. Every change to `main` flows through a feature branch + PR with rationale in the description. Ember reviews and merges; pushback happens on the diff. After PR #1 set the pattern, the rest of the work followed it cleanly.

---

## Punch list / open items

`STAGING-MARKERS.md` is the canonical source for the ongoing punch list. Summary as of launch:

**Done:**
- ✅ Custom domain (`imaginebc.net`) live with HTTPS enforced
- ✅ Staging gate removed; site publicly indexable
- ✅ All 11 Visit-The-Town CTAs route to the production visitor center
- ✅ Anchor-partner placeholders confirmed permanent
- ✅ Contact-form question closed (visitor center is the intake)

**Not blocking; nice-to-haves:**
- Build out footer pages (Contact / Press / Privacy / Terms) when each becomes a real concern. Six `href="#"` placeholders remain in `index.html` by design (4 footer + 2 nav-brand scroll-to-top).
- Submit sitemap to Google Search Console for faster indexing.
- (Optional) Add AAAA records at GoDaddy for IPv6 coverage (~5% of visitors).
- (Optional) Refresh `og:image` with dated launch art if a press push warrants a distinctive social-share image.
- Monitor: when Erik's visitor center moves from `frontend-dev.imaginebc.io/visit` to a final production URL, single find-and-replace updates all 11 CTAs.

**Out of scope / parked:**
- Creator deck (`decks/for-creators.html`) — built 2026-04-25, stood down 2026-04-27. Preserved at `C:\IBC3.0\Documents\decks-archive\for-creators.html` outside the repo. Not currently planned.
- Decks for other audiences (Brands, Funders, Industries) — could follow the same pattern, not currently planned.

---

## Repo file inventory

| File | Purpose |
|---|---|
| `index.html` | The site — single file, all CSS/JS inline. ~1,500 lines. |
| `visit.html` | Coming Soon fallback page (preserved post-launch). |
| `CNAME` | `imaginebc.net` for GitHub Pages custom domain. |
| `images/` | Hero, panel, traction-map, X-Terminals, why-Africa, sponsorship visuals; logo. |
| `images/buildings/` | 10 isometric building renders for the Town section. |
| `docs/art-prompts.md` | Style direction + per-image prompts for future art commissions. |
| `CHANGES.md` | Ember's 2026-04-26 polish-pass changelog. |
| `STAGING-MARKERS.md` | Post-launch maintenance reference (was a pre-launch checklist before 2026-05-14). |
| `PROJECT_LOG.md` | This file. |

---

## Stand-down note

This document is written as a hand-off so the next person to touch the site — Erik, Osiris, Ember, or a future Claude — can reconstruct the design intent and the why behind each decision without having to re-discover them in conversation. The site is launched. The architecture is stable. The punch list is short and entirely optional. Project is at rest.
