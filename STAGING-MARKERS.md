# STAGING MARKERS — Pre-Launch Checklist

This file tracks every placeholder, staging block, and known-incomplete item that must be addressed before the site goes fully public. Search the codebase for `STAGING` to find code-level markers; this doc tracks the broader checklist.

Last audited: 2026-04-27 (visitor center URL wired + Erik's calls on placeholders & contact form).

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

## 🔗 Visit The Town CTAs — ✅ wired (2026-04-27)

All 11 Visit-The-Town CTAs now route to **`https://frontend-dev.imaginebc.io/visit`** (Erik confirmed the visitor center URL on 2026-04-27). They cover: nav primary, hero primary, every end-of-section transition CTA (Flywheel, Town, X-Terminals, Anchor Tiers, Beachhead), all five audience-tab CTAs, and the final CTA.

The CTA copy varies by audience-tab context (e.g., *"Visit The Town — See How Places Are Built"* for Creators, *"...See How Campaigns Run"* for Brands), but every instance routes to the same visitor center URL.

**Note on the original audit count.** The earlier audit said "17 instances of `href=\"#\"` should all become the visitor center URL." On verification, only **11** were Visit-The-Town CTAs. The remaining **6** are:

- 2× `nav-brand` links (logo + name; serve as scroll-to-top, intentionally `href="#"`)
- 4× footer placeholders (Contact, Press, Privacy, Terms — separate concern, addressed when those pages exist)

`grep -n 'href="#"' index.html` should now return exactly **6** matches. If it returns more, audit before assuming intent.

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

---

## 📋 Pre-launch checklist (tear off when launching)

When the visitor center URL exists AND the domain is pointed AND public-naming permissions are cleared, work through this list in order:

- [ ] Remove `noindex` meta tags (3-line block, ~line 6)
- [ ] Remove password gate CSS (~line 660)
- [ ] Remove password gate HTML + script (~line 706)
- [ ] Verify zero `STAGING` matches: `grep -c "STAGING" index.html` returns `0`
- [x] Wire Visit The Town CTAs to visitor center URL (`https://frontend-dev.imaginebc.io/visit`) — ✅ done 2026-04-27 (11 of 11 wired)
- [ ] Audit the remaining 6 `href="#"` (4 footer placeholders + 2 brand scroll-to-top links) — addressed when Contact/Press/Privacy/Terms pages exist
- [ ] Confirm `http://imaginebc.net/` is correct (or update to `https://` + final domain)
- [x] Anchor-partner placeholders — kept permanent by design (no swap needed) ✅ 2026-04-27
- [ ] Manual smoke test: load on desktop + mobile, click every CTA, verify all images render
- [ ] Submit sitemap to Google Search Console once indexable
- [ ] Update `og:image` with a fresh dated banner if the launch warrants distinctive social-share art
