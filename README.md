# wp-knowledge — shared WordPress knowledge for every project

One folder of plain Markdown that every project in `CC-projects/` reads when it needs it:
theme know-how (Flatsome, SWELL, block themes), design rules (general and Japanese),
writing, Japanese law for websites, SEO/GEO, plugins, maintenance, security, performance.
No code, no secrets, nothing specific to one client.

Repository: github.com/walto247/wp-knowledge (private). Created 2026-10-11 from the nine
skills of the archived `wp-agent-dashboard` project (which merged the account skills and the
older WSL skills in September 2026), de-duplicated and stripped of tool- and client-specific text.

## Rules

1. **This is the only copy.** When a fact changes, change it here. Do not paste these files into
   a project; a project's `CLAUDE.md` says "read `../wp-knowledge/<topic>`" and the reader opens
   the topic it needs.
2. **Client-specific facts never go here.** They belong to that client's project (its `CLAUDE.md`,
   `DESIGN.md`) or, for the site assistant, its site pack. Example: which accordion tag one site
   uses, one school's campus list, one shop's prices.
3. **Every change is logged in `CHANGELOG.md`** (what changed, and what existing sites should check). That file is the only notification channel: projects read it at session start; no messages between projects.
4. **Every file says how fresh it is.** The first lines carry `Status:` with the date it was
   merged and whether it has been verified against the official documentation. Pass 2
   (one session per topic) verifies each topic and records the date and the source pages.
5. **Account skills in `~/.claude/skills/` (flatsome-wp, swell-wp, seo-expert) are the one
   allowed duplicate**, because Claude Code loads them automatically. They are updated *from*
   this folder, never the other way round. Edit here first.
6. `seo-audit-kit/` stays a separate project: it is a method with tools and templates.
   `seo-geo/` here holds the knowledge and points to the kit for the procedure.
7. The site-assistant service runs in a container on the VPS and cannot read this PC. For it,
   this folder is a build input: the deploy copies the topics it needs (or checks this repo out
   next to the service). Decided 2026-10-11; not built yet.

## Topics

| Folder / file | What | Status |
|---|---|---|
| `design/general.md` | Page structure, hierarchy, spacing scale, wireframe patterns, components, avoiding the generic "AI look", screen sizes and breakpoints, spacing rhythm, English typography, navigation, surfaces, motion | merged, unverified; **screen sizes, spacing, typography, navigation, surfaces and motion researched 2026-10-15** (Bootstrap, Tailwind, StatCounter, DADS, WCAG, Material, NN/g) |
| `design/japan.md` | Japanese UX conventions, typography, forms, trust signals, mobile, colour, seasons | **typography verified 2026-10-11** (DADS, JLReq, JIS); navigation and forms checked 2026-10-15 (DADS components, WCAG 2.2); UX conventions and audiences remain practice |
| `design/accessibility.md` | WCAG 2.2 AA and JIS X 8341-3 checklist, JIS revision status | **verified 2026-10-11** (WCAG 2.2, JIS 1.4.3 checklist, DADS) |
| `design/design-tokens.md` | DESIGN.md template and how tokens map to CSS, any theme | merged |
| `writing/japanese.md`, `writing/english.md` | Copy, tone by audience, CTAs, lengths | merged |
| `legal/japan.md` | 景品表示法, ステマ規制, 薬機法, 特定商取引法, 個人情報保護法, accessibility duty, copyright | **景表法 parts verified 2026-10-11** (ステマ, No.1, 2024 amendment); rest practice |
| `seo-geo/README.md` | On-page SEO, Japanese SEO, GEO (AI answers), structured data; points to `seo-audit-kit` | **verified 2026-10-11** (Google Search Central, Yoast); Japanese lengths are practice |
| `seo-geo/reporting.md` | Client SEO / analytics reports (English and Japanese): structure, key numbers, bad news, writing for non-technical readers, talk script, cadence, how to check; diagnosis table, monthly client PDF page by page, Japanese seasonality and metric labels, cover message templates, frameworks | **researched 2026-10-14, extended 2026-10-16** (Google + government sources; agency parts are practice) |
| `seo-geo/measurement.md` | Search Console and GA4 measurement (key events, cross-domain, referrals, hostname filter, UTM rule), moving part of a site to another domain, CWV in reports; GA4 metric definitions and names, Search Console inside GA4, Looker Studio refresh, AI Overviews evidence | **researched 2026-10-14, extended 2026-10-16** (Google help and Search Central, Pew) |
| `marketing/japan.md` | Japanese CTAs and conversion conventions, trust, seasonal calendar, claims, what Dentsu and Hakuhodo publish | merged; agency section checked 2026-10-11 |
| `marketing/landing-pages.md` | Landing pages, global and Japanese: one goal, first view, phone-first, 新PASONA and AIDA, ten-block wireframe, CTA and form, law and ad platforms | **checked 2026-10-16** (NN/g, Unbounce, Baymard, Google/Meta/LINE ad policies, 消費者庁, 厚労省); layouts are practice |
| `flatsome/` | UX Builder, CSS and child theme, WooCommerce, posts | **verified 2026-10-11** (theme 3.20.11 files, official hooks and docs, live sites) |
| `swell/` | Block editor rules, SWELL blocks, Customizer map | **verified 2026-10-11** (swell-theme.com: 2.19, blocks, plugins; live site: CSS variables); Customizer paths not re-checked |
| `block-themes/README.md` | theme.json-based themes (for `wp-master-theme`) | stub |
| `wp-plugins/` | One file per plugin: Yoast, WP Rocket, WPForms, Wordfence, UpdraftPlus, WP Mail SMTP, WPML, ACF | **checked 2026-10-11** where vendors document it; Wordfence and ACF are practice |
| `CHANGELOG.md` | Dated entries: what changed in the guidance + a checklist for existing sites. **Every project reads the top entry at session start.** | started 2026-10-11 |
| `wp-maintenance.md`, `wp-security.md`, `wp-performance.md` | Health check, security review with the hardening baseline and PHP/WordPress versions, Core Web Vitals | **verified 2026-10-11** (hardening guide, php.net, web.dev); routines are practice |

## Pass 2 plan (one session per topic, in this order)

1. ~~`design/japan.md` + `design/accessibility.md`~~ done 2026-10-11 (typography and accessibility; the Digital Agency policy page was unreachable, retry once).
2. ~~`flatsome/`~~ done 2026-10-11 (theme files read on SKYUS staging).
3. ~~`swell/`~~ done 2026-10-11.
4. ~~`seo-geo/`~~ done 2026-10-11; `legal/japan.md` 景表法 parts done, the rest (薬機法, 特商法, 個人情報) still to verify; 消費者庁 site was unreachable.
5. ~~`wp-plugins/`, `wp-security.md`, `wp-performance.md`~~ done 2026-10-11.

Pass 2 is complete except: `legal/japan.md` 薬機法 / 定期購入 details / 個人情報 sections (特商法 表記 and 外部送信 checked 2026-10-15), `block-themes/` (stub), `swell/customizer.md` panel paths, and one retry of the two unreachable pages (digital.go.jp policy page, caa.go.jp stealth-marketing page). Next: pass 3 when a topic changes (new theme version, new law, new Google guidance); re-check version tables every quarter.

Each verified file gets `Status: verified YYYY-MM-DD against <pages>` and keeps a short
"what changed" note at the bottom.
