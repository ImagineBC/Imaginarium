# Website Content Bible — imaginebc.net

**Created:** 2026-06-13 · **Status:** LIVING. Update in the **same change-set** as any edit to `index.html` content.

> **What this doc is.** A section-by-section memorialization of the **complete content** of the public marketing site (`index.html`) — what every block says, why it exists, what art it uses, and how it reads after the 2026-06-13 Discovery-Tier + ScoutX update. It is the content record; it is **not** the operations/deploy guide.
>
> **Sibling doc (do not confuse):** the *operations* bible lives OUTSIDE this repo at `Documents/Website-planning/WEBSITE_BIBLE.md` (same filename, different folder) and covers the repo location, deploy pipeline, branch strategy, and Osiris hand-off. Read that one before learning *how* to ship; read **this** one to know *what the site says*.
>
> This file is a peer to the repo's own `PROJECT_LOG.md` / `CHANGES.md` / `STAGING-MARKERS.md` and ships inside the website repo (`github.com/ImagineBCDev/Imaginarium`). It is never served as a page (GitHub Pages serves only `index.html`).

---

## 0. The 2026-06-13 release in one paragraph

The site previously modeled creators as a **binary** — you either own a building or you're a member who earns. This release adds the missing middle: the **discovery tier** (the emerging creator who submits content into public centers with no building, no BizBase) and the **graduation ladder** that turns members into creators. It also introduces **ScoutX**, a new X-Terminal selling pre-breakout talent intelligence to labels, agencies, and influencer marketers. Positioning evolved per the **Option 2** decision: subtitle + a second hero badge now; the headline-level "two-tier creator economy" rewrite (Option 3, with the meta/SEO/OG cascade) is held until ScoutX is servicing a live client. Throughout, the discovery story is framed **globally** — Africa is the proof-of-value beachhead, not the ceiling; a creator anywhere should feel invited.

---

## 1. Site identity & theme (unchanged this release)

| Token | Value | Used for |
|---|---|---|
| `--bg-primary` | `#0a0e1a` | page background |
| `--accent-teal` | `#56AF9B` | members, primary CTA, brand |
| `--accent-gold` | `#F39C12` | brands |
| `--accent-blue` | `#4A90E2` | **creators + discovery tier + ScoutX (creator-side terminal)** |
| `--accent-red` | `#E74C3C` | funders |
| `--accent-violet` | `#A78BFA` | institutional X-Terminals (CredX/TelcoX/RetailX/BrandX) |

- **Fonts:** Playfair Display (display headings) + Inter (body). **Style:** dark, painterly medieval-fantasy "Imaginarium town" art at golden hour, globally-diverse cast.
- **Single-file site:** all HTML + `<style>` + `<script>` inline in `index.html`. No build step.
- **Every CTA routes to** `https://frontend-dev.imaginebc.io/visit` (the one deliberate doorway).
- **Paths are relative** (GitHub Pages serves the mirror at the `/Imaginarium/` subpath).
- **Meta/headline:** kept on the existing "world's first Behavioral Intelligence Platform powered by a creator economy" line (Option 3 deferred — do **not** change `<title>`/OG/Twitter/canonical until a live ScoutX client exists).

---

## 2. Global chrome

- **Nav:** brand → Flywheel · Who It's For · X-Terminals · Thesis · Beachhead · **Visit The Town** (CTA). Blur-on-scroll. *(Ladder + ScoutX intentionally NOT added to the top nav to avoid crowding; they live in the footer + body.)*
- **Footer — Platform column** (this release added two links): The Flywheel · **The Creator Ladder** (`#ladder`) · X-Terminals · **ScoutX** (`#scoutx`) · The Town · The Thesis.
- **Scripts:** `switchTab()` (audience tabs), `switchIndustry()` (industry sub-pills — now includes the **talent/ScoutX** pill), **`switchCreatorTier()`** (NEW — Emerging/Established sub-toggle; also swaps the Creators panel image), scroll-reveal `IntersectionObserver`, and the stats-bar count-up animation.

---

## 3. Section-by-section content (current state, after this release)

Order: **Nav → Hero → Social Proof → Flywheel → Audience Tabs → Creator Ladder → Town → Stats → X-Terminals → ScoutX → Anchor Tiers → Thesis → Beachhead → Why Africa → Final CTA → Footer.** (Creator Ladder and ScoutX are the two net-new sections.)

### 3.1 Hero
- **Badges:** `Africa is the proof • The world is the market` **+ (NEW) `Where the world's next creators are discovered`** (blue dot).
- **Headline (unchanged):** "The world's first **Behavioral Intelligence Platform** powered by a creator economy."
- **Subtitle (CHANGED):** now weaves the discovery clause into the Creators sentence — "…and the next ones are *discovered here*: submit your work into a public center, build an audience, and climb to your own building."
- **CTAs:** Visit The Town + segment buttons (Creators/Brands/Industry/Funders).

### 3.2 Social Proof
- Partner bar: Signature Bank · T2 Mobile (4M+) · Vukile · The Oni of Ife · Slikour Onlife · Tier-1 Sportsbook (Kenya) · Kenya Forestry Service · M-Pesa · Shoprite · MTN Nigeria (MoMo). *(Talent-buyer logos to be added here when ScoutX clients sign — sales-gated.)*

### 3.3 Flywheel — "Four Steps. Compounding Returns."
- Steps: **1** Brands Fund Campaigns → **2** Members Earn & Spend → **3** Creators Cash Out Directly → **4** Signal Flows to X-Terminals.
- **(NEW) Supply-side loop callout** below the four steps — "The Supply-Side Loop — Members Become Creators": the members who earn in Step 2 also submit work into Amplify/Nexus/B4Famous, get featured, and graduate into creators, deepening Step 1's reach and Step 4's signal. Makes the flywheel self-feeding on the supply side, not just demand.

### 3.4 Audience Tabs — "Same Pitch. Scaled to Whoever's Listening."
Five tabs: Creators · Brands · Industries · Funders · Members.

- **Creators (RESTRUCTURED into a two-tier sub-toggle):**
  - **Emerging — Get Discovered** (NEW, default): "Get Discovered. No Building Required." Submit permissionlessly into Amplify/Nexus/B4Famous; get featured; build an audience & earn; graduate to your own building (links to `#ladder`). Image: `creators-emerging-panel.png`.
  - **Established — Own Your Building** (the original panel, preserved verbatim): "Build a Place People Actually Visit." Direct cash, your building/rules, sponsor-funded reach multiplier, referral annuity. Image: `creators-panel.png`.
  - The sub-toggle swaps both the copy block and the panel image via `switchCreatorTier()`.
- **Brands (unchanged):** "Verified Humans. Intentional Attention. Compounding Returns." 98%/0-bot, anchor-as-tenant, BrandX.
- **Industries (CHANGED — added a 5th pill):** Financial (CredX) · Telcos (TelcoX) · Retail & FMCG (RetailX) · Media·Betting·Faith (verticals) · **Talent & Media (ScoutX, NEW)**. ScoutX pill copy: "See the Breakout Before the World Does." — buyer blocks for Influencer/Brand Marketing, Labels/A&R/Distributors (worldwide, Afrobeats→hip-hop→gospel→comedy), Agencies/Streaming/Esports.
- **Funders (CHANGED — added a 4th feature):** existing two-layer/Africa-beachhead/moat story **+ (NEW) "Two Data Products, One Engine"**: every member is a latent creator (supply scales permissionlessly), and ScoutX is a second enterprise revenue line on an orthogonal buyer set — a multiple-expander.
- **Members (CHANGED — added a 4th feature):** existing earn/town/privacy story **+ (NEW) "You Could Be Discovered Here Too"**: one submission away from being a creator; links to `#ladder`.

### 3.5 Creator Ladder — "From Member to Movement." (NEW SECTION, id=`ladder`)
The single most important net-new section. Five follower-driven rungs, **canonical values sourced from `ManageMembersController.cs:142-148`** (token-driven, presented as current defaults):

| Rung | Followers | Token | Unlocks |
|---|---|---|---|
| Member | 0 | — | earn, spend, **submit into public centers** |
| Creator Studio | 50 | `REFERRAL-THRESHHOLD-BIZBASE` | BizBase creator tooling |
| Monetization | 100 | `REFERRAL-THRESHHOLD-MONETIZATION` | content can earn |
| Discoverable | 150 | `REFERRAL-THRESHHOLD-SEARCH` | platform search |
| Own Your Building | 500 | `REFERRAL-THRESHHHOLD-PUBLICACCESS` | full public channel (destination, teal-highlighted) |

- Footnote on the section: thresholds are configuration-driven and may be tuned per market — values shown are current defaults. **If Erik retunes the tokens, update these numbers here and on the page.**
- No image — pure CSS rung cards. CTA: "Visit The Town — Start Your Climb."

### 3.6 The Town — "A Living Town — Where the Signal Is Generated"
- **(NEW) Proving-grounds callout** above the building grid: B4Famous (breakout talent), Amplify (music), The Nexus (gaming) are on-ramps where any verified member submits work.
- **Building grid (now 10 cards):** **B4Famous (NEW, first card, "Get discovered" badge)** · The Gallery · Arcade · Theater · **The Nexus ("Get discovered" badge)** · The Compound · Green Room · The Mart · **Amplify ("Get discovered" badge)** · Town Hall. Plus "+40 more public centers."
- B4Famous building type: "Breakout Talent Discovery." Image: `images/buildings/b4famous.png`.

### 3.7 Stats Bar
- 200K+ Verified Members · 4 Markets · 85% Value In-Country · 98% Engagement. *(A discovery-tier stat — creators discovered / member→creator conversions — to be added once real data exists.)*

### 3.8 X-Terminals — "Meet the X-Terminals"
- **Grid now 5 cards:** CredX (banks) · TelcoX (operators) · RetailX (commerce/FMCG) · BrandX (brands/SMEs) · **ScoutX (NEW — "For Labels, Agencies & Talent Buyers," blue accent, "Newest" tag)**. Grid widened to `repeat(5,1fr)`.
- Plus vertical adaptations: Media · Betting · Faith.

### 3.9 ScoutX Feature Section — "Discover Talent Before the World Does." (NEW SECTION, id=`scoutx`)
- Banner image: `images/scoutx-visual.png` (16:9).
- Three buyer cards: Influencer & Brand Marketing · Labels/A&R/Distributors · Agencies/Streaming/Esports.
- **Consent-by-construction block:** ScoutX only surfaces creators who **opted into discovery by submitting their own work** — a service *to* the creator, not surveillance *of* them. No scraping, no shadow profiles. (Ties to the platform's L1/L2/L3 sovereignty principle.)

### 3.10 Anchor Tiers — "Three On-Ramps. One Platform."
- Run Campaigns (BrandX) · Anchor in the Town · Lease an X-Terminal. **(CHANGED)** the "Lease" card now lists **ScoutX** among the terminals and adds "labels & talent buyers" to the Best-for line.

### 3.11 Thesis · 3.12 Beachhead · 3.13 Why Africa · 3.14 Final CTA
- **Thesis (unchanged):** Layer 1 Creator Economy + Layer 2 Behavioral Intelligence; the moat is participatory > surveillance data.
- **Beachhead (unchanged):** South Africa live; Kenya/Nigeria/Uganda launching; global rollout phases ending at U.S. buy-side.
- **Why Africa (CHANGED, one card):** "Creator-Dense Culture" now ties to ScoutX talent-discovery and frames the genres as among the world's fastest-growing exports — "the model travels everywhere; the supply of emerging talent runs hot here." Reinforces Africa = proof, not ceiling.
- **Final CTA (CHANGED):** subtitle adds the discovery invitation; a second **"Get Discovered"** button joins "Visit The Town."

---

## 4. Asset inventory (images/)

New this release (all painterly Imaginarium style, globally-diverse cast):

| File | Aspect | Used by |
|---|---|---|
| `images/buildings/b4famous.png` | 4:3 (720×540) | Town strip B4Famous card |
| `images/scoutx-visual.png` | 16:9 (720×405) | ScoutX feature-section banner |
| `images/creators-emerging-panel.png` | 4:3 (720×540) | Creators → Emerging tab visual |

*(All three are WebP-encoded with a `.png` extension — renders fine in modern browsers via content sniffing.)* Pre-existing art (hero, panels, building cards, x-terminals-visual, why-africa-hero, traction map, etc.) unchanged.

---

## 5. Deferred / sales-gated (do NOT ship until the trigger lands)

- **Headline Option 3** ("…powered by a two-tier creator economy — where the next creators are discovered") + the `<title>`/meta/OG/Twitter/canonical cascade — **gated on a live ScoutX client** (a sales milestone, not a build milestone).
- **Discovery stats** in the stats bar — when real data exists.
- **Talent-buyer logos** in social proof — as ScoutX clients sign.
- **First-breakout traction proof** in the Beachhead — when it happens.

---

## 6. Maintenance contract

Update this file in the same change-set whenever you change site content. If you retune the ladder thresholds (§3.5), change them here **and** on the page. For *how to ship* (branch/PR/Osiris hand-off), see the operations bible at `Documents/Website-planning/WEBSITE_BIBLE.md`.
