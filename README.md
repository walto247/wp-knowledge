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
3. **Every file says how fresh it is.** The first lines carry `Status:` with the date it was
   merged and whether it has been verified against the official documentation. Pass 2
   (one session per topic) verifies each topic and records the date and the source pages.
4. **Account skills in `~/.claude/skills/` (flatsome-wp, swell-wp, seo-expert) are the one
   allowed duplicate**, because Claude Code loads them automatically. They are updated *from*
   this folder, never the other way round. Edit here first.
5. `seo-audit-kit/` stays a separate project: it is a method with tools and templates.
   `seo-geo/` here holds the knowledge and points to the kit for the procedure.
6. The site-assistant service runs in a container on the VPS and cannot read this PC. For it,
   this folder is a build input: the deploy copies the topics it needs (or checks this repo out
   next to the service). Decided 2026-10-11; not built yet.

## Topics

| Folder / file | What | Status |
|---|---|---|
| `design/general.md` | Page structure, hierarchy, spacing scale, wireframe patterns, components, avoiding the generic "AI look" | merged, unverified |
| `design/japan.md` | Japanese UX conventions, typography, forms, trust signals, mobile, colour, seasons | **typography verified 2026-10-11** (DADS, JLReq, JIS); UX/forms/audiences remain practice |
| `design/accessibility.md` | WCAG 2.2 AA and JIS X 8341-3 checklist, JIS revision status | **verified 2026-10-11** (WCAG 2.2, JIS 1.4.3 checklist, DADS) |
| `design/design-tokens.md` | DESIGN.md template and how tokens map to CSS, any theme | merged |
| `writing/japanese.md`, `writing/english.md` | Copy, tone by audience, CTAs, lengths | merged |
| `legal/japan.md` | 景品表示法, ステマ規制, 薬機法, 特定商取引法, 個人情報保護法, accessibility duty, copyright | merged, unverified (law changes; verify dates) |
| `seo-geo/README.md` | On-page SEO, Japanese SEO, GEO (AI answers), structured data; points to `seo-audit-kit` | merged, unverified |
| `marketing/japan.md` | Japanese CTAs and conversion conventions, trust, seasonal calendar, claims | merged (thin, to grow) |
| `flatsome/` | UX Builder, CSS and child theme, WooCommerce, posts | merged, unverified (version-specific facts) |
| `swell/` | Block editor rules, SWELL blocks, Customizer map | merged, **unverified: block prefix conflict, see file** |
| `block-themes/README.md` | theme.json-based themes (for `wp-master-theme`) | stub |
| `wp-plugins/` | One file per plugin: Yoast, WP Rocket, WPForms, Wordfence, UpdraftPlus, WP Mail SMTP, WPML, ACF | merged, unverified (versions) |
| `wp-maintenance.md`, `wp-security.md`, `wp-performance.md` | Health check, security review, Core Web Vitals | merged, unverified |

## Pass 2 plan (one session per topic, in this order)

1. ~~`design/japan.md` + `design/accessibility.md`~~ done 2026-10-11 (typography and accessibility; the Digital Agency policy page was unreachable, retry once).
2. `flatsome/` against the official Flatsome documentation and current changelog.
3. `swell/` against swell-theme.com documentation (Japanese).
4. `seo-geo/` against Google Search Central, Yoast, current GEO guidance; `legal/japan.md` against
   the Consumer Affairs Agency pages.
5. `wp-plugins/`, `wp-security.md`, `wp-performance.md` against each plugin's docs and the
   WordPress hardening guide.

Each verified file gets `Status: verified YYYY-MM-DD against <pages>` and keeps a short
"what changed" note at the bottom.
