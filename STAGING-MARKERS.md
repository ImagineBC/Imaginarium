# STAGING MARKERS — Pre-Launch Checklist

This file tracks every placeholder, staging block, and known-incomplete item that must be addressed before the site goes fully public. Search the codebase for `STAGING` to find code-level markers (should now be zero); this doc tracks the broader checklist.

Last audited: 2026-05-14 (staging gate removed; Visit-The-Town CTAs swapped to local `/visit.html` placeholder pending production Town readiness).

---

## 🚪 Password gate + indexing protection — ✅ removed (2026-05-14)

Both the password gate (`Spurs!1111`) and the `noindex` meta tags have been **fully removed**. The site is now publicly accessible and indexable.

Removed:
- The 3-line `noindex` meta block (was lines ~6-8 of `index.html`)
- The entire `.pw-gate*` CSS block (~42 lines, was around line 660)
- The password gate HTML markup + companion script (~34 lines, was around line 706)

Verification (post-removal): `grep -cE "(STAGING|pw-gate|pwGate|Spurs|noindex|nofollow)" index.html` should return **`0`**.

If preview-only access is ever needed again, the previous gate code is preserved in commit history (look for the commit titled "Add password gate and noindex for staging").

---

## 🏗️ Visit The Town — temporary `/visit.html` placeholder (2026-05-14)

Erik's production visitor center isn't ready yet, so the 11 Visit-The-Town CTAs now point at a **local Coming Soon page at `/visit.html`** (Ember-authored, 2026-05-14) rather than the earlier `https://frontend-dev.imaginebc.io/visit` URL.

The `/visit.html` page matches the parent site's design system (Inter + Playfair Display, dark navy + teal accent, same logo, same brand voice) and includes:

- "Opening Soon" eyebrow with pulsing teal dot
- Hero headline: *"The Town is taking shape."*
- Body copy framing what visitors will find when the doors open
- Two CTAs: return-to-home + jump to the audiences section
- A six-item "What you'll find" grid (member homes, creator destinations, brand surfaces, X-Terminals, public centers, the Map)
- Footer email for press / investor / early-access inquiries

**Swap-back path when production is ready:**

Single find-and-replace in `index.html`:

```
/visit.html  →  https://[production-visitor-center-url]
```

All 11 CTAs flip. The `visit.html` file can stay in the repo (harmless once unreferenced) or be deleted. `grep -c 'href="/visit.html"' index.html` should return `0` after the swap.

**Status of the remaining 6 `href="#"`:** unchanged from 2026-04-27 audit — 2× `nav-brand` scroll-to-top + 4× footer placeholders (Contact, Press, Privacy, Terms — addressed when those pages exist). `grep -n 'href="#"' index.html` should still return exactly **6** matches.

---

## 🌐 Domain configuration

Current intended public domain: `http://imaginebc.net/` (Willow, 2026-04-26). Willow is actively working on domain configuration as of 2026-05-14 (GoDaddy for `imaginebc.net`, possibly new `imaginarium.net`).

Currently set in:

- `<link rel="canonical">` — line ~7
- `og:url` meta
- `og:image` absolute URL
- `twitter:image` absolute URL

If the domain changes (or moves to `https://` or a new domain), update all four locations: `grep -n "imaginebc.net" index.html`.

GitHub Pages currently serves from `https://imaginebcdev.github.io/Imaginarium/` (org renamed from `ImagineBC` to `ImagineBCDev` between 2026-04-27 and 2026-05-14 — the old Pages URL `imaginebc.github.io/Imaginarium/` now 404s; GitHub Pages doesn't follow org-rename redirects).

---

## 🤝 Anchor-partner placeholders — kept by design (2026-04-27)

Two anchor-partner references render as generic placeholders. **Per Erik's decision on 2026-04-27, these stay as placeholders permanently** — the audience-targeted decks Erik handed to Osiris already address how named-partner mentions are handled across the marketing surfaces, so the public website intentionally keeps category-level framing.

| Placeholder | Location(s) | Status |
|---|---|---|
| `Tier-1 Sportsbook (Kenya)` | Community Builders strip + Kenya country detail | Keep |
| `major comedy creator` | Nigeria country detail | Keep |

No swap needed. If a future partner explicitly wants public attribution on the website itself, that's a content edit, not a launch blocker.

---

## 🎨 Visual / asset notes

- The 10 building images in `images/buildings/` are an initial set. Per `docs/art-prompts.md` the style direction is medieval-fantasy isometric craft village (Age of Empires meets fantasy village builder). If new buildings get added or the existing renders are upgraded, the file naming convention is `{building-slug}.png` (e.g., `gallery.png`, `theater.png`, `livebroadcastcenter.png`).
- All hero / panel / map images live at `images/` root.
- `visit.html` is intentionally text-only (no hero image) so it loads instantly and doesn't over-promise visual richness when the destination isn't open yet.

---

## 📋 Open work (tear off as items complete)

- [x] Password gate + noindex removed ✅ 2026-05-14
- [x] Visit The Town CTAs wired to local `/visit.html` placeholder ✅ 2026-05-14
- [ ] When Erik's production Town is ready: single find-and-replace `/visit.html` → production URL
- [ ] Confirm/finalize public domain (`imaginebc.net` via GoDaddy, or new `imaginarium.net`)
- [ ] Once domain is pointed: verify `canonical`, `og:url`, `og:image`, `twitter:image` all reflect final URL
- [x] Anchor-partner placeholders — kept permanent by design ✅ 2026-04-27
- [ ] Manual smoke test (post-domain): load on desktop + mobile, click every CTA, verify all images render
- [ ] Submit sitemap to Google Search Console after domain is live
- [ ] Update `og:image` with a fresh dated banner if the public launch warrants distinctive social-share art
