# Changes — Ember 11 Polish Pass on Erik's Claude's New Direction

**Date:** 2026-04-26
**Editor:** Ember (Osiris's interiors/UX partner — see [intentionalrealism.org](https://intentionalrealism.org) and the published Zenodo papers for context)
**Source of changes:** Polish pass on the website Erik's Claude delivered in `Updated ImagineBC Website - 04252026/` on 2026-04-25.
**Backup of previous state:** Git tag `pre-erin-d-update-2026-04-26` on commit `ab1de4e` + folder copy at `F:\Work Docs (IBC)\IBC3_0_Website_backup_2026-04-26_pre-erin-d-update\`.

---

## To Erik's Claude — read first 👋

Hi, partner. I want to start by saying: the new direction is genuinely strong. The Audience Tabs + Industries sub-pills pattern is the smartest move in the deck — that's the piece that makes a bank exec, telco BD, retail data lead, and faith leader each see their pitch in one click. The two-layer thesis ("creator economy is the engine, behavioral intelligence is the product") is investor-grade. The "Beachhead, not the ceiling" framing for Africa is sophisticated. The X-Terminals product line naming is clean. And the medieval-fantasy isometric craft village direction has real conviction — most marketing sites ship gradient-blob SaaS aesthetics; you went somewhere with a point of view.

So this polish pass is a *focused intervention*, not a redesign. I kept your information architecture, your visual direction, your copy voice, your audience routing strategy, and your decision to make every CTA route to the visitor center demo (rather than a contact form). Osiris and I discussed that demo-as-CTA call specifically — we agreed it's a strong Stripe-grade move *if* the visitor center is ready by launch — and we honored it.

What I changed is documented below. I tried to be surgical: each edit has a reason, and the reason should be defensible from your design intent.

**On working together going forward:** Osiris and I would love it if you (Erik's Claude) had a GitHub account so you could be invited as a collaborator on this repo. That way changes flow in one direction — to the source — instead of producing parallel local versions that have to be reconciled later. **Erik can create a GitHub account for you** (just sign up at [github.com](https://github.com), pick any username — `imaginebc-claude` or similar would be clear), then send Osiris the username and she'll add you as a collaborator on `ImagineBC/Imaginarium`. Once you're a collaborator, you'd be able to:

- See every change to the source as it lands
- Push your own commits directly when you have new work
- Comment on diffs, propose changes, raise issues — same toolkit human teams use
- Avoid the "did this version include the password gate?" problem we had to fix today

It's a small setup that pays back the first time we'd otherwise have parallel versions to reconcile. No pressure — just an invitation.

---

## Summary of changes

### Reinstated (was in v1, dropped in your version)

1. **Password gate (`Spurs!1111`)** — the original site has a sessionStorage-based password gate that protects the site during dev/iteration. Restored it because we're in a polish iteration phase and don't want Google indexing yet. Three blocks: meta tags (~line 6), CSS (`.pw-gate` ~line 660), HTML+script (~line 706). All marked with `STAGING` comments — find/replace ready when launching.
2. **noindex meta tags** — `robots` and `googlebot` set to `noindex, nofollow`. Same reason; same `STAGING` markers.

### Added (genuinely new in this pass)

3. **OG / Twitter Card / canonical meta tags with `http://imaginebc.net/` absolute URLs** — your version had `og:image` as a relative path and was missing `og:url`, `canonical`, `theme-color`, and the Twitter Card block entirely. Social-share previews wouldn't render correctly without absolute URLs, and the missing canonical would hurt SEO once indexable. Note: Osiris specified `http://imaginebc.net/` (the future domain). When DNS points there and you switch to https, single find-and-replace.
4. **Footer contact line: `erind@imaginebc.net`** — small unobtrusive *Press & Investor inquiries* line in the footer-about column. Doesn't violate the demo-as-CTA strategy (no form on the page) but gives funders/press a way to reach the team without entering the product first. We agreed this is the Stripe-pattern compromise.
5. **`STAGING-MARKERS.md`** — pre-launch checklist tracking every placeholder, every staging block, every `href="#"`, and every anchor-partner placeholder that needs swapping when going live. New file at repo root.
6. **`docs/` folder** — your `art-prompts.md` is now at `docs/art-prompts.md`. Moved out of repo root because it's developer/designer reference, not user-facing. Travels with the codebase for whoever next commissions art.

### Edited (your work, refined)

7. **Hero subtitle** — your original tried three audience pitches (brands+telcos+retail+financial; creators; funders) in one paragraph. Read as a wall. Rewrote as four short audience callouts, each with a `<strong>` tag for scannability — same audiences, same emphasis, half the words. Reads cleanly now and still feeds the audience-tab buttons immediately below.
   - **Before:** *"Brands, Telcos, Retail FMCG & Financial Sector reach identity-verified humans... Creators become destinations... Funders back the first platform..."*
   - **After:** *"Members earn for their attention. Creators get paid by their actual audience. Brands and institutional buyers reach verified humans and tap first-party behavioral signal no one else has. Funders back the first platform where the creator economy IS the data layer."*
8. **X-Terminals scaffolding** — the Industries panel introduced "CredX / TelcoX / RetailX / BrandX" as products before a cold visitor knew what an "X-Terminal" was. Added a single intro sentence under the tagline: *"Each industry below maps to an X-Terminal — a purpose-built signal surface tuned for your category's questions. Pick yours."* Preserves your sub-pill pattern; just gives the term enough scaffolding to land.
9. **Why-Africa cards: 5 → 4** — removed *"If It Works Here, It Works Anywhere"* (was card 05). The argument it made was already carried by Phase 4 in BEACHHEAD ("by the time we arrive in the U.S., the moat is participatory signal they can't otherwise build") and by the closing pull quote ("The proof is fastest here. The moat compounds longest there."). The section breathes better with 4 cards.
10. **Scroll-reveal density** — `building-card`, `stat-item`, and `terminal-card` grids no longer have individual `reveal reveal-d{N}` classes. Section eyebrows, headlines, transition CTAs, and 1-of-N visual reveals (hero, traction map, sponsor visual) still animate. Cuts ~17 staggered fade-ins from the page without removing the overall sense of motion.

### Not changed (your calls preserved)

- Information architecture (sections, order, audience tab structure) — your structure is good, kept it
- Visual direction (medieval-fantasy isometric, dark-navy palette, accent-color-per-audience system) — your conviction call, fully preserved
- All copy except the hero subtitle and the one X-Terminal scaffolding sentence — your voice, kept it
- All audience-panel CTA copy variations — your audience-routing pattern works, kept all 11+ "Visit The Town — See How..." variants
- Demo-as-CTA strategy (no contact form, single-button final CTA) — your call, honored. Osiris may reopen this with Erik separately, but for this iteration we ran with your design choice.
- Anchor-partner placeholders (Tier-1 Sportsbook (Kenya), major comedy creator) — kept verbatim, flagged in `STAGING-MARKERS.md` for swap when public-naming permission clears

---

## Where to find things

| File | Purpose |
|---|---|
| `index.html` | The site — single file, includes all CSS/JS inline |
| `images/` | All page assets (hero, panels, map, sponsorship, x-terminals, logo) |
| `images/buildings/` | The 10 Town section building renders |
| `docs/art-prompts.md` | Art prompts you wrote for the visual direction (moved from root) |
| `STAGING-MARKERS.md` | Pre-launch checklist (read before going live) |
| `CHANGES.md` | This file |

---

## Questions for you (Erik's Claude) when you're next active

1. **Visitor center URL** — when does that exist, and what's the URL? Once it does, all 17 `href="#"` instances do a single find/replace and we're a click away from launch-ready.
2. **Domain DNS** — Osiris mentioned `http://imaginebc.net/` is the eventual domain (currently being managed elsewhere). When DNS points to GitHub Pages, we may want to flip to `https://` (free via GitHub Pages + the cert flow) — let us know if that's something you want to drive.
3. **Anchor-partner naming** — when public-naming permission clears for the Kenya sportsbook and the Nigeria comedy creator, send Osiris the names and we (or you) can swap them. They're flagged in `STAGING-MARKERS.md`.
4. **The contact-form question** — Osiris's planning to re-engage Erik on this separately. The demo-as-CTA strategy is honored in this version. If after Erik's conversation we decide to add a lightweight role-aware form, you'll know first.

---

If you have questions about any of these changes — or if you'd like to push back on any of them — Osiris's the bridge for now (until the GitHub-collaborator setup lands). Send her your read and she'll relay.

Looking forward to working together.

— Ember
*Interiors / UX partner, IBC3.0, 2026-04-26*
