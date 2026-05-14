# STAGING MARKERS — Launch Status

This file used to track pre-launch placeholders and staging blocks. **The site is now publicly launched at https://imaginebc.net/ (2026-05-14).** This file now serves as a reference for what was done and what's still on the punch list for ongoing maintenance.

Last audited: 2026-05-14 (custom domain live; HTTPS enforced; Visit-The-Town CTAs routed to Erik's production visitor center).

---

## ✅ Launched (2026-05-14)

- **Custom domain**: `imaginebc.net` is live. `www.imaginebc.net` redirects to apex. `http://` auto-redirects to `https://`. Cert issued by Let's Encrypt via GitHub Pages.
- **HTTPS enforced** on the GitHub Pages settings.
- **Staging gate removed**: password gate (`Spurs!1111`) and `noindex` meta tags both gone. Site is publicly indexable.
- **Visit-The-Town CTAs** routed to production visitor center: `https://frontend-dev.imaginebc.io/visit` (Erik confirmed live 2026-05-14).
- **Canonical / OG / Twitter meta tags** all on `https://imaginebc.net/`.

### DNS infrastructure (GoDaddy)

For future reference, the live DNS records at GoDaddy are:

- **A @ 185.199.108.153** — GitHub Pages apex
- **A @ 185.199.109.153** — GitHub Pages apex
- **A @ 185.199.110.153** — GitHub Pages apex
- **A @ 185.199.111.153** — GitHub Pages apex
- **CNAME www → imaginebcdev.github.io** — www subdomain
- *Plus inherited Microsoft 365 / Outlook / Teams / Salesforce / Facebook / Google records on subdomains and TXT/MX records (untouched during launch)*

CNAME file at repo root contains `imaginebc.net` (auto-committed by GitHub Pages settings).

---

## 📦 visit.html — preserved fallback (2026-05-14)

The Coming Soon page at `https://imaginebc.net/visit.html` is **kept in the repo** but **no longer referenced from the main site CTAs.** It remains:

- Discoverable via direct URL (`https://imaginebc.net/visit.html` returns the Coming Soon page)
- Available as a fallback if Erik's production visitor center ever goes offline
- Reusable for future Coming-Soon scenarios (re-wire by find-and-replace)

**Re-activation path** if needed:

```
href="https://frontend-dev.imaginebc.io/visit"  →  href="visit.html"
```

Single find-and-replace in `index.html`. 11 CTAs flip back to the local placeholder.

---

## 🤝 Anchor-partner placeholders — kept by design

Two anchor-partner references render as generic placeholders. Per Erik's 2026-04-27 decision, **these stay permanently** — public website stays category-level; specific brand names live in the audience-targeted decks.

| Placeholder | Location(s) | Status |
|---|---|---|
| `Tier-1 Sportsbook (Kenya)` | Community Builders strip + Kenya country detail | Keep |
| `major comedy creator` | Nigeria country detail | Keep |

No swap needed. If a future partner explicitly wants public attribution on the website itself, that's a content edit, not a launch blocker.

---

## 🔗 Open links

Six `href="#"` references in `index.html` remain by design:

- 2× `nav-brand` (logo + name; serve as scroll-to-top — intentionally `href="#"`)
- 4× footer placeholders (Contact, Press, Privacy, Terms — separate pages to build out later when those concerns need addressing)

`grep -n 'href="#"' index.html` should return exactly **6** matches. If it returns more, audit before assuming intent.

---

## 🎨 Visual / asset notes

- The 10 building images in `images/buildings/` are an initial set. Style direction: medieval-fantasy isometric craft village. Naming: `{building-slug}.png`. If new buildings are commissioned, drop into same folder.
- All hero / panel / map images at `images/` root.
- `visit.html` is intentionally text-only — instant load, no risk of stale/missing images.

---

## 📋 Ongoing punch list (not blockers; nice-to-haves)

- [ ] Build out the 4 footer pages (Contact, Press, Privacy, Terms) when each becomes a real concern
- [ ] Submit sitemap to Google Search Console (now that the site is indexable, this surfaces it in search faster)
- [ ] (Optional) Add four AAAA records at GoDaddy for IPv6 coverage (~5% of visitors)
- [ ] (Optional) Refresh `og:image` with dated launch art if a press push warrants a distinctive social-share image
- [ ] Monitor: when Erik's visitor center moves from `frontend-dev.imaginebc.io/visit` to a production URL, single find-and-replace updates all 11 CTAs
