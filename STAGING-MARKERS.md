# STAGING MARKERS — Pre-Launch Checklist

This file tracks every placeholder, staging block, and known-incomplete item that must be addressed before the site goes fully public. Search the codebase for `STAGING` to find code-level markers; this doc tracks the broader checklist.

Last audited: 2026-04-26 (Ember 11 polish pass).

---

## 🚪 Password gate + indexing protection

The site currently lives behind a `Spurs!1111` password and is `noindex`-tagged. Both must be removed simultaneously when ready to launch publicly.

| Item | Location | Action when launching |
|---|---|---|
| Robots noindex meta | `index.html` lines ~6-8 | Remove the 3-line block (`<!-- STAGING: Remove these two tags... -->` + the two `<meta>` tags) |
| Password gate CSS | `index.html` ~line 660 (`.pw-gate` block) | Remove the entire `/* === PASSWORD GATE (STAGING) ===` CSS block through the closing comment |
| Password gate HTML | `index.html` ~line 706 | Remove the `<div class="pw-gate">...</div>` and the immediately-following `<script>...</script>` block |
| Search keyword | All occurrences | `grep -n "STAGING" index.html` should return ZERO matches when launch-ready |

Password value (for sharing with reviewers): `Spurs!1111` (encoded as character codes in the inline script — do NOT change without updating both the codes and the password you share).

---

## 🔗 Visit The Town CTAs (17 instances of `href="#"`)

The hero, nav, audience tabs, every section closer, and the final CTA all point at `href="#"` because the visitor center URL is not yet known. When Erik provides the visitor center URL:

1. Find every `href="#"` — there are **17 instances** as of this audit
2. Find-and-replace them all with the actual visitor center URL
3. The single search-and-replace assumes ALL `href="#"` should become the visitor center URL — verify this assumption holds for every instance before bulk-replacing (no other use of `href="#"` is intended in the codebase as of 2026-04-26)

The CTA copy varies by audience-tab context (e.g., "Visit The Town — See How Places Are Built" for Creators, "...See How Campaigns Run" for Brands) but they should all route to the same visitor center.

---

## 🌐 Domain configuration (`http://imaginebc.net/`)

The site's intended public domain is `http://imaginebc.net/` (per Willow, 2026-04-26). Currently set in:

- `<link rel="canonical">` — line ~10
- `og:url` meta — line ~16
- `og:image` absolute URL — line ~13
- `twitter:image` absolute URL — line ~21

If the domain changes (or moves to `https://`), update all four locations. Suggested approach: `grep -n "imaginebc.net" index.html` to find every reference.

GitHub Pages is currently serving from `https://imaginebc.github.io/Imaginarium/` until DNS is pointed at the new domain.

---

## 🤝 Anchor-partner placeholders

Two anchor-partner names are currently rendered as generic placeholders pending public-naming permission:

| Placeholder | Location(s) | What needs to swap |
|---|---|---|
| `Tier-1 Sportsbook (Kenya)` | `index.html` line 807 (Social Proof strip) and line 1495 (Kenya country detail) — *appears as "tier-1 sportsbook" in the second instance* | Replace with the actual sportsbook brand name once Kenya partner has approved public naming |
| `major comedy creator` | `index.html` line 1505 (Nigeria country detail) | Replace with the actual creator name once Nigeria partner has approved public naming |

Both placeholders are flagged in Erik's Claude's original handoff note. When swapping, audit nearby copy to make sure the new name fits the surrounding sentence cleanly.

---

## 🎨 Visual / asset notes

- The 10 building images in `images/buildings/` are an initial set. Per `docs/art-prompts.md` the style direction is medieval-fantasy isometric craft village (Age of Empires meets fantasy village builder). If new buildings get added or the existing renders are upgraded, the file naming convention is `{building-slug}.png` (e.g., `gallery.png`, `theater.png`, `livebroadcastcenter.png`).
- All hero / panel / map images live at `images/` root.

---

## 📋 Pre-launch checklist (tear off when launching)

When the visitor center URL exists AND the domain is pointed AND public-naming permissions are cleared, work through this list in order:

- [ ] Remove `noindex` meta tags (3-line block, ~line 6)
- [ ] Remove password gate CSS (~line 660)
- [ ] Remove password gate HTML + script (~line 706)
- [ ] Verify zero `STAGING` matches: `grep -c "STAGING" index.html` returns `0`
- [ ] Replace all 17 `href="#"` with the live visitor center URL
- [ ] Verify zero `href="#"` matches in `index.html`
- [ ] Confirm `http://imaginebc.net/` is correct (or update to `https://` + final domain)
- [ ] Swap anchor-partner placeholders (Tier-1 Sportsbook, major comedy creator)
- [ ] Manual smoke test: load on desktop + mobile, click every CTA, verify all images render
- [ ] Submit sitemap to Google Search Console once indexable
- [ ] Update `og:image` with a fresh dated banner if the launch warrants distinctive social-share art
