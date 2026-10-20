# wp-knowledge — shared WordPress knowledge for every project

One folder of plain Markdown that every project in `CC-projects/` reads when it needs it:
theme know-how (Flatsome, SWELL, block themes), design rules (general and Japanese),
writing, Japanese law for websites, SEO/GEO, plugins, maintenance, security, performance.
No site-specific code (short reference snippets are allowed), no secrets, nothing specific to one client.

Repository: github.com/walto247/wp-knowledge (private). Created 2026-10-11 from the skills of the
archived `wp-agent-dashboard` project. Each folder has a `SOURCES.md` with the pages read and the dates.

## Rules

1. **This is the only copy.** When a fact changes, change it here. Do not paste these files into
   a project; a project's `CLAUDE.md` points to `CC-projects/1_GLOBAL_ASSETS/wp-knowledge/<topic>` and the reader opens
   the topic it needs.
2. **Client-specific facts never go here.** They belong to that client's project (its `CLAUDE.md`,
   `DESIGN.md`) or, for the site assistant, its site pack. Example: which accordion tag one site
   uses, one school's campus list, one shop's prices.
3. **Every change is logged in `CHANGELOG.md`** (what changed, and what existing sites should check). That file is the only notification channel: projects read it at session start; no messages between projects.
4. **Every file says how fresh it is.** The first lines carry `Status:` with the date it was
   merged and whether it has been verified against the official documentation. Pass 2
   (one session per topic) verifies each topic and records the date and the source pages.
5. **The account skills flatsome-wp, swell-wp and seo-expert (synced under `~/.claude/skills/synced/`) are the one
   allowed duplicate**, because Claude Code loads them automatically. They are updated *from*
   this folder, never the other way round. Edit here first.
6. `seo-audit-kit/` stays a separate project: it is a method with tools and templates.
   `seo-geo/` here holds the knowledge and points to the kit for the procedure.
7. Tools that cannot read this PC (for example a service on a server) get the topics they need copied at deploy time.

## Topics

| Folder / file | What | Status |
|---|---|---|
| `design/general.md` | Page structure, hierarchy, spacing scale, wireframe patterns, components, avoiding the generic "AI look", screen sizes and breakpoints, spacing rhythm, English typography, navigation, surfaces, motion | merged, unverified; **screen sizes, spacing, typography, navigation, surfaces and motion researched 2026-10-15** (Bootstrap, Tailwind, StatCounter, DADS, WCAG, Material, NN/g) |
| `design/japan.md` | Japanese UX conventions, typography, forms, trust signals, mobile, colour, seasons | **typography verified 2026-10-11** (DADS, JLReq, JIS); navigation and forms checked 2026-10-15 (DADS components, WCAG 2.2); UX conventions and audiences remain practice |
| `design/accessibility.md` | WCAG 2.2 AA and JIS X 8341-3 checklist, JIS revision status | **verified 2026-10-11** (WCAG 2.2, JIS 1.4.3 checklist, DADS) |
| `design/design-tokens.md` | DESIGN.md template and how tokens map to CSS, any theme | merged |
| `writing/japanese.md`, `writing/english.md` | Copy, tone by audience, CTAs, lengths | merged |
| `legal/japan.md` | 景品表示法, ステマ規制, 薬機法, 特定商取引法, 個人情報保護法, accessibility duty, copyright | **景表法 parts verified 2026-10-11** (ステマ, No.1, 2024 amendment); rest practice |
| `marketing/japan.md` | Japanese CTAs and conversion conventions, trust, seasonal calendar, claims, what Dentsu and Hakuhodo publish | merged; agency section checked 2026-10-11 |
| `marketing/youtube.md` | YouTube: what the system optimises, myths, packaging, retention, Shorts, captions, policies, Japan law and music, embeds and video indexing, report KPIs | **researched 2026-10-17** (YouTube Help, Search Central, 総務省, 消費者庁, JASRAC) |
| `marketing/sns.md` | Instagram, TikTok, X, LINE, Facebook: Japan usage by age, discovery per platform, myths, LINE pricing, UTM and GA4, embeds, SNS law, report KPIs | **researched 2026-10-17** (platform docs, 総務省, 消費者庁, 厚労省) |
| `marketing/landing-pages.md` | Landing pages, global and Japanese: one goal, first view, phone-first, 新PASONA and AIDA, ten-block wireframe, CTA and form, law and ad platforms | **checked 2026-10-16** (NN/g, Unbounce, Baymard, Google/Meta/LINE ad policies, 消費者庁, 厚労省); layouts are practice |
| `seo-geo/README.md` | On-page SEO, Japanese SEO, GEO (AI answers), structured data; points to `seo-audit-kit` | **verified 2026-10-11** (Google Search Central, Yoast); Japanese lengths are practice |
| `seo-geo/reporting.md` | Client SEO / analytics reports (English and Japanese): structure, key numbers, bad news, writing for non-technical readers, talk script, cadence, how to check; diagnosis table, monthly client PDF page by page, Japanese seasonality and metric labels, cover message templates, frameworks | **researched 2026-10-14, extended 2026-10-16** (Google + government sources; agency parts are practice) |
| `seo-geo/measurement.md` | Search Console and GA4 measurement (key events, cross-domain, referrals, hostname filter, UTM rule), moving part of a site to another domain, CWV in reports; GA4 metric definitions and names, Search Console inside GA4, Looker Studio refresh, AI Overviews evidence | **researched 2026-10-14, extended 2026-10-16** (Google help and Search Central, Pew) |
| `seo-geo/clarity.md` | Microsoft Clarity: when it may be used (Microsoft: not for sites aimed at minors; terms: no health, finance or government content), limits, WordPress install, masking and consent, Japan law, monthly routine, reporting | **researched 2026-10-17** (Microsoft Learn, Clarity terms, PPC, 総務省) |
| `print/` (README, production, design, html-to-pdf, tri-fold, law) | Flyers (チラシ), leaflets and pamphlets: JIS sizes, bleed, fold panels, CMYK and black, PDF/X, paper, QR; type sizes and layout; front/back blueprint; HTML/CSS to PDF routes; print law (総額表示, clinics, real estate, maps, posting) | **verified 2026-10-20** (vendor data guides, Japan Color, W3C, Vivliostyle, Prince, 国税庁, 消費者庁, 厚労省, 不動産公取協) |
| `ecommerce/japan-checkout.md` | Japanese shops: 消費税 and 総額表示, インボイス, payment methods and 3-D Secure, Shopify/WooCommerce options, checkout fields, Yamato/Sagawa slots, 置き配 | **verified 2026-10-19** (国税庁, METI, platforms, carriers) |
| `ecommerce/cross-border.md` | Selling abroad: DAP/DDP, EU €3 duty and IOSS, UK £135, US de minimis suspension, Australia GST, Japan Post services and US rules, 輸出免税, currencies | **verified 2026-10-19** (EU, HMRC, CBP, ATO, Japan Post, 国税庁) |
| `flatsome/` | UX Builder, CSS and child theme, WooCommerce, posts | **verified 2026-10-11** (theme 3.20.11 files, official hooks and docs, live sites); `posts.md` and `woocommerce.md` still unverified |
| `swell/` | Block editor rules, SWELL blocks, Customizer map | **verified 2026-10-11** (swell-theme.com: 2.19, blocks, plugins; live site: CSS variables); Customizer paths checked against the manual 2026-10-17 |
| `block-themes/README.md` | theme.json-based themes: files, theme.json v3 keys, presets, layout, variations, WP 7.1 responsive styles, default themes | **generic parts checked 2026-10-17** (schema, Theme Handbook); master-theme decisions stay in `wp-master-theme/docs/` |
| `wp-plugins/` | One file per plugin: Yoast, WP Rocket, WPForms, Wordfence, UpdraftPlus, WP Mail SMTP, WPML, ACF; minimum safe versions | **checked 2026-10-11** where vendors document it; versions and advisories checked 2026-10-17 |
| `wp-maintenance.md`, `wp-security.md`, `wp-performance.md` | Health check, security review with the hardening baseline and PHP/WordPress versions, Core Web Vitals | **verified 2026-10-11**, versions re-checked 2026-10-17 (hardening guide, php.net, wordpress.org, web.dev); routines are practice |
| `infrastructure/shared-hosting.md` | Hostinger (hPanel) and cPanel for WordPress: SSH, document roots, WP-CLI, three caches, PHP, SSL fixes, cron, backups, staging | **verified 2026-10-19** (Hostinger, cPanel, LiteSpeed, WP-CLI docs) |
| `infrastructure/vps-hardening.md` | Generic VPS hardening (Ubuntu/Debian): SSH drop-ins, UFW and Docker, fail2ban, updates, time, backups, batch WP-CLI updates | **verified 2026-10-19** (Ubuntu, Debian, Docker, fail2ban, WP-CLI); n8n VPS specifics stay in `n8n-server-ops` |
| `database/wp-database.md` | Database upkeep: export first, prefix, autoloaded options (6.6), transients, revisions, optimize/repair, WooCommerce HPOS | **verified 2026-10-19** (WP-CLI, WordPress, WooCommerce docs) |
| `agency-sop/file-intake.md` | How agents take in client files (spreadsheets, documents, slides, PDFs, images, archives, audio/video): `tmp/intake/` paths, parsing, visual review page | added 2026-10-19 by the owner's orchestrator chat (procedure, not verified knowledge) |
| `CHANGELOG.md` | Dated entries: what changed in the guidance + a checklist for existing sites. **Every project reads the top entry at session start.** | started 2026-10-11 |

## Open items

- `legal/japan.md`: 薬機法, 定期購入 details, 個人情報保護法 (利用目的, 第三者提供); the 令和8年 amendment's guidelines when published.
- One retry of the digital.go.jp design-system policy page.
- `flatsome/posts.md`, `flatsome/woocommerce.md`, `design/general.md` (older parts), `writing/`: not yet verified.
- `marketing/japan.md`: palettes and type by industry.
- Re-check version tables every quarter. Monthly scheduled source check (CLAUDE.md job 3): pending the owner's decision (2026-10-21); until then on request.
