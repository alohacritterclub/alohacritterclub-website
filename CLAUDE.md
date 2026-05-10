# Improving Aloha Critter Club Website

Working folder for improvements to alohacritterclub.org — the site for Aloha Critter Club, a Hawaii 501(c)(3) nonprofit running after-school animal welfare + SEL clubs.

## Organization context

- **Name:** Aloha Critter Club
- **Type:** 501(c)(3) public charity, IRC 170(b)(1)(A)(vi), Hawaii (origin: Keaukaha Elementary)
- **EIN:** 86-1496578 (effective date of exemption: January 13, 2021; source: IRS Letter 947 dated 2021-05-08)
- **Mailing address:** P.O. Box 1281, Kea'au, HI 96749
- **Fiscal year:** calendar year (accounting period ending Dec 31); Form 990/990-EZ/990-N filing required annually
- **Site:** https://alohacritterclub.org — site traffic served by Netlify since 2026-04-22 (apex A and `www` CNAME at Wix point to Netlify hosting). GitHub repo: https://github.com/alohacritterclub/alohacritterclub-website. **DNS authority and domain registrar both still at Wix** (Tucows backend); full consolidation onto Netlify scheduled for 2026-06-01 (see Phase 7 below). Domain renews 2026-12-14, yearly cycle.
- **Companion web app:** `app.alohacritterclub.org` — Firebase-hosted (A → 199.36.158.100), iOS app shipped via App Store, Android (Google Play) launch pending. Maintained by lead engineer in separate Claude sessions; **do not modify any app-related infrastructure or DNS records**.
- **Mission:** After-school clubs where kids become animal experts and practice social-emotional learning (SEL)
- **Reach:** ~70 students in FY2025 across 5 schools: Pahoa Elementary, Kea'au Elementary, Kea'au High School, Mountain View Elementary, Kua O Ka La Charter School *(prior figure of ~84 students / 97% attendance was an earlier snapshot — verify which to use in public-facing copy)*
- **Founder / Board President:** Kristin Spear
- **Other board:** Aakash Shah (Secretary), Nicholle Hug (Treasurer), Sarah Ortega, Leah Gowron
- **Contact:** alohacritterclub@gmail.com, Instagram @alohacritterclub
- **Donation mechanism today:** Venmo **Charity Profile** QR on homepage, handle `@alohacritterclub3` — tax receipts issued automatically

## Why this project exists

1. **SEO:** `site:alohacritterclub.org` returns zero Google results — the site is not indexed. Branded searches surface Facebook, a 2021 Hawaii News Now article, and a Keaukaha Elementary page, but not the nonprofit's own site.
2. **Donations:** Venmo Charity Profile is in place (tax receipts handled), but the homepage has no framed ask, no desktop-clickable donate button, and no recurring-gift path. Individual giving is structurally thin — see baseline below.

## FY2025 financial baseline (use for donation copy + ask sizing)

Source: `~/Downloads/Aloha Critter Club Income & Expenses Tracker 2025.xlsx` (reviewed 2026-04-22).

**Income — $6,550.76** *(excl. $300 petty-cash wash)*
- Atherton Grant: $5,000 (76%)
- Rollover from FY2024: $790.81 (12%)
- Individual donations: $759.95 across 3 gifts (12%) — largest was a $509.95 anonymous Venmo gift in Dec 2025

**Expenses — $6,001.21** *(excl. $300 petty-cash wash)*
| Category | Amount | Per student (÷70) |
|---|---|---|
| School Supply Stipend | $2,100.00 | $30.00 |
| Community Events | $2,055.37 | $29.36 |
| Teacher Stipend | $1,000.00 | $14.29 |
| Operational (Wix, certificates, tent) | $574.84 | $8.21 |
| Field Trip Fees | $270.00 | $3.86 |
| Bank Charge | $1.00 | $0.01 |

**Net surplus:** ~$550

**Dollar → impact anchors (grounded in actual 2025 spend):**
- **$25** — one student's club supplies for a semester (actual ≈ $20–21; $25 rounds safely above)
- **$75** — a student field trip (exact: Mountain View → Magical Creatures, May 2025)
- **$150** — a school field trip (exact: Kua O Ka La → Magical Creatures, April 2025)
- **$250** — a full semester's supplies for one school (exact: standard School Supply Stipend)
- **$500** — a teacher stipend for a full club cycle (exact)
- **$86** — average full-year cost to serve one student ($6,001 ÷ 70)

**Strategic takeaway:** 76% grant dependency on Atherton. If that grant doesn't renew, revenue drops to ~$1,550/yr. Donation-process work is structural risk mitigation, not just a nice-to-have.

## Working agreement (updated 2026-04-22)

- **Migrating from Wix to Netlify.** Decision made 2026-04-22 — terminal-based workflow fits Kristin's timeline better than ongoing Wix edits.
- Claude drives code + deploys from terminal; Kristin reviews via Netlify preview URLs.
- Wix site stays live until new site is approved and DNS is cut over. No downtime at cutover.
- One concern per session when possible (migration phase, SEO, donations, content rewrites).

## Migration to Netlify — phase plan (in progress)

**Stack:** Astro (static site generator) + Netlify (hosting + forms) + GitHub (code + version history) + optional Decap CMS for non-terminal editing.

- [x] **Phase 0 — Prerequisites** (complete 2026-04-22). Tools: Homebrew 5.1.7, node v25.9.0, npm 11.12.1, gh 2.91.0. Accounts: GitHub `alohacritterclub`, Netlify signed up via GitHub OAuth (email: `alohacritterclub@gmail.com`). Domain registrar: **Wix** (renews 2027-01-13; DNS cutover via Wix panel in Phase 4, no transfer needed). CMS layer: **Decap** (Phase 3 — GUI editing at `/admin`, auth via GitHub OAuth + Netlify Identity).
- [x] **Phase 1 — Local build** (complete 2026-04-22). Astro 6.1.9 minimal template, TypeScript strict. Stack: `src/layouts/Layout.astro` + `src/components/{Header,Footer,DonationAsk}.astro` + 4 pages (`index`, `about`, `events`, `contact`). Brand applied: colors (`#2d81a6` primary, `#faba0e` accent, `#8cbf1c` green, `#64b5e3` light), fonts (Fredoka One display, Arvo body, via Google Fonts), tagline "One Paw At A Time." in hero + footer. Logo at `/images/logo.png`. Venmo QR at `/images/venmo-qr.png`. Redirects config in `netlify.toml` for `/event` → `/events` and `/who-we-are` → `/about`.
- [x] **Phase 2 — GitHub + Netlify staging** (complete 2026-04-22). Repo: https://github.com/alohacritterclub/alohacritterclub-website (public, `main` branch, initial commit `1abe2be`). Netlify site auto-generated name `stellular-valkyrie-159d1a` (rename pending). Staging URL: https://stellular-valkyrie-159d1a.netlify.app. Auto-deploys on push to `main`. Netlify team name: "Critter Leads".
- [deferred 2026-04-22] **Phase 3 — Decap CMS.** Attempted with Netlify Identity + Git Gateway; Identity invite flow failed (feature in maintenance mode for new accounts — known issue). Admin scaffolding removed. Decision: defer CMS; Kristin messages for edits at current low volume. Revisit with Sveltia CMS + GitHub OAuth App if edit frequency grows past ~1/month.
- [x] **Phase 4 — DNS cutover** (complete 2026-04-22). Wix DNS updated: apex A record → `75.2.60.5`, `www` CNAME → `stellular-valkyrie-159d1a.netlify.app`. DNS propagated globally within ~1hr. SSL auto-issued by Netlify/Let's Encrypt. https://alohacritterclub.org now serves the Astro build. Redirects verified working: `/event` → `/events`, `/who-we-are` → `/about`.
- [x] **Phase 5 — Shut down Wix** (complete 2026-05-02). Wix Premium plan ("Light", 3-year cycle) auto-renewal turned OFF via Account Settings → Premium Subscriptions. Plan paid through Nov 18, 2028 — no refund pursued (past Wix's 14-day window; sunk cost accepted). Plan will simply expire on that date with no charge. Domain subscription left ACTIVE (renews 2026-12-14, separate yearly cycle). Wix DNS records intact (apex A → 75.2.60.5, www CNAME → stellular-valkyrie-159d1a.netlify.app). Live site verified still serving from Netlify post-change. Optional Wix content export skipped (live site on Wayback if ever needed).
- [x] **Phase 6 — Post-migration SEO** (complete 2026-05-02). Google Search Console property created for `https://alohacritterclub.org` (URL prefix), verified via HTML file (`/google33d50a466a0dcd76.html`, deployed via commit `38fcd87`; previous unused token `googlefe319da8d0fdb2ca.html` retained). Sitemap `sitemap-index.xml` submitted successfully. Indexing requested for all 4 pages: `/`, `/about/`, `/contact/`, `/events/`. Instagram (@alohacritterclub) and Facebook page bios updated to point to `https://alohacritterclub.org`. Indexing verification deferred to ~2 weeks out.
- [ ] **Phase 7 — Domain consolidation onto Netlify** (scheduled 2026-06-01). Move DNS authority + registrar from Wix to Netlify so domain, DNS, and hosting all live in one dashboard. Coordinated with lead engineer who started a Netlify DNS zone on 2026-05-06 (records: marketing-site apex/www correct; TXT verification for `app.*` correct; **missing A record `app.alohacritterclub.org → 199.36.158.100` for Firebase-hosted companion app — engineer to add before cutover**). Safe order on/after 2026-06-01: (1) confirm Netlify zone is complete with engineer; (2) swap nameservers at Wix from `ns2/3.wixdns.net` to `dns1/2.p02.nsone.net` (and dns3/4 if shown); (3) verify all three hostnames resolve; (4) initiate registrar transfer-away from Wix to Netlify (5–7 day ICANN window). Until 2026-06-01: **do not touch DNS records, nameservers, or initiate registrar transfer.**

Current phase: **Awaiting 2026-06-01.** Phases 0–6 complete; Phase 7 (DNS + registrar consolidation) on hold pending lead engineer's completion of the Netlify DNS zone.

**Verification window (active):** Indexing requested 2026-05-02. Expected timeline:
- 24–72hr: Google starts crawling submitted URLs
- 1–2 weeks: `site:alohacritterclub.org` returns results in Google (was zero pre-migration — this is the success metric)
- 2–4 weeks: branded searches like "aloha critter club" surface the site
- Check **Search Console → Indexing → Pages** report ~2026-05-16 to confirm 4/4 pages indexed; troubleshoot if not.

**Outstanding on live site** (polish, do anytime):
- YouTube promo video embedded on homepage ✓ (https://youtu.be/wOpa8_ZsdJk)
- Convert HEIC photos to JPG so they render in browsers
- Actually use photos in pages (hero image, team photos on About, etc.)
- Remove duplicate `logo without background copy 3.png` from `public/images/`
- Rename Netlify site from `stellular-valkyrie-159d1a` to `alohacritterclub` or similar (Site settings → Change site name)

## What's pending

*Note (2026-04-22): Tasks below were authored for the Wix site. Post-migration, the SEO copy (titles, meta, H1s, alt text) and donation copy will be executed on the new Astro/Netlify site through code, not Wix click paths. Backlink outreach still applies as-is.*


**SEO — setup (do first)**
- [ ] Verify Wix Dashboard → Settings → SEO → "Let search engines index your site" is ON
- [ ] Connect Google Search Console via Wix's one-click integration
- [ ] Submit sitemap: https://www.alohacritterclub.org/sitemap.xml
- [ ] Set up Google Business Profile under the Nonprofit category
- [ ] Set up Bing Webmaster Tools
- [ ] Pick one canonical domain (alohacritterclub.org vs www.alohacritterclub.org) and redirect the other

**SEO — paste-ready copy**
- [ ] Paste per-page titles, meta descriptions, and H1s from `seo-kit.md`
- [ ] Add alt text to all images (Venmo QR, logo, student photos, board photos)
- [ ] Inventory pages beyond Home / Who We Are / Events / Contact and add SEO metadata for those too

**SEO — ongoing**
- [ ] Backlinks: ask Hawaii News Now to link the 2021 article to the current site
- [ ] Backlinks: ask partner schools (Pahoa, Kea'au, Mountain View, Keaukaha) to link to the site from their club/community pages
- [ ] Backlinks: ask Aloha Ilio Rescue + other shelter partners
- [ ] Add website URL prominently to Facebook and Instagram bios
- [ ] Publish event recaps / student project stories to grow indexable content

**Donations**
- [x] Confirmed 2026-04-22: Venmo QR is a Charity Profile → tax receipts automatic, no migration needed
- [x] Homepage framed-ask copy chosen: **Option A (tiered, with $86/yr cost-to-serve anchor)** — saved to `homepage-copy.md`, includes Astro component sketch for the Netlify rebuild
- [x] Donor thank-you / tax-acknowledgment email template finalized — saved to `donation-acknowledgment.md`. IRS-compliant, EIN 86-1496578 baked in, Venmo handle `@alohacritterclub3` confirmed. Decision: use Gmail templates for manual send rather than automate (volume too low to justify Zapier).
- [ ] Paste Option A copy into Wix homepage (Home → section above Venmo QR → Add Section Above → paste → H2 headline, bulleted tiers)
- [ ] Add a desktop-clickable Donate button in the header
- [ ] Finalize donor acknowledgment template with EIN and save as Gmail template (Gmail → Settings → Advanced → Templates)
- [ ] Optional: add a recurring-gift path (Venmo Charity doesn't support monthly recurring — revisit Givebutter/Donorbox as a *supplement*, not replacement, if recurring becomes a priority)

**Information still needed from Kristin**
- Real URL slug for the Events page (the `/events` guess 404s, but the page works in the browser) — needed for migration content port
- Complete inventory of pages under the "More" expandable menu — needed for migration content port
- Whether to use 70 students / 5 schools (FY2025 actuals) or 84 students / 97% attendance (earlier figure) in public copy

## Files in this folder

**Project root (Astro app):**
- `CLAUDE.md` — this file; auto-loaded when Claude Code runs in this directory
- `package.json`, `astro.config.mjs`, `tsconfig.json`, `.gitignore` — Astro scaffold (minimal template, Astro 6.1.9, TypeScript strict)
- `src/pages/index.astro` — homepage (currently placeholder from scaffold)
- `public/` — static assets (favicons, images)
- `node_modules/` — dependencies (gitignored)

**Reference docs (`docs/`):**
- `docs/seo-kit.md` — paste-ready page titles, meta descriptions, H1s, alt text (originally for Wix; still valid for porting to Astro pages)
- `docs/homepage-copy.md` — homepage framed-ask (Option A) + Astro component sketch + header Donate button recommendation
- `docs/donation-acknowledgment.md` — IRS-compliant donor thank-you / tax receipt email (with EIN), Gmail template setup, automation notes

**Dev commands** (all run from this folder):
- `npm run dev` — local preview at http://localhost:4321
- `npm run build` — production build to `dist/`
- `npm run preview` — preview the production build

## Resuming this project

```
cd /Users/kristinspear/aloha-critter-club-website
claude
```

To continue the most recent session in this folder instead of a fresh one, add `--continue`.
