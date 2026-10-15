# Changelog — what changed in the shared knowledge, and what to check on existing sites

Newest first. Every project reads the **top entry** at the start of a session (rule in `CC-projects/CLAUDE.md`).
An entry has two parts: what changed in the files, and a **checklist for existing sites** (check and report; change only with the owner's OK and each project's own rules).

## 2026-10-15 — Screen sizes, breakpoints and content widths

Files changed: `design/general.md` (new section "Screen sizes, breakpoints and widths"), `design/japan.md` (new section "Screen sizes in Japan", line-length row), `flatsome/posts.md` (article width), `design/SOURCES.md`, `README.md`.
Checked a pasted agency article against Bootstrap/Tailwind docs, StatCounter Japan (Sept 2026), DADS レイアウト, JLReq; several claims corrected (see `design/SOURCES.md`).

What changed in the guidance:
- Design at 390 (phone) and 1440 (desktop); no separate tablet design. Test phones at 360 / 390 / 430 (Japan also 375 / 414), desktops at 1280 / 1366 / 1536 / 1920.
- One breakpoint at 768 (DADS and Japanese practice); add 1024 only for 3–4 column grids. Theme breakpoints (Flatsome 549 / 849) stay as they are.
- Content container 1120 + side padding, never over 1200; side padding 16 on phones, 32 from 768.
- Japanese article body `max-width: 41em` (≈ 40 characters, ≈ 656 px at 16 px); was 780 px in the Flatsome post CSS (≈ 48 characters); that rule is now scoped to single posts.
- Raster images at 2× the slot; 3× not needed.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Content container wider than 1200 px | edges touch on 1280–1536 laptops (native 1366, or 1920 screens at 125–150 %) | container width, pages |
| Japanese article body wider than 45 characters per line (> ~730 px at 16 px) | JLReq: at most about 40 characters (40 is the target, 45 the tolerance) | measured width and characters per line |
| Layout at 360 px and 1280 px; Flatsome `.entry-content` width rules that also hit pages or tab panels | smallest common phone, scaled Windows laptop | sideways scroll, overlap, cut-off menus |
| Banners with text baked in, or images narrower than 2× their slot | blurry on phones; text not readable by search or screen readers | page, image, file width vs slot |

## 2026-10-14 — SEO / analytics reporting and measurement (two new topics)

Files changed: new `seo-geo/reporting.md`, new `seo-geo/measurement.md`, `seo-geo/SOURCES.md`, `README.md`, `writing/japanese.md` (pointer).
Researched from an SEO project session; Google and government points read 2026-10-14; agency points marked as practice.

What changed in the guidance:
- Reports say **what is wrong → how to fix → how to check**; summary first (written last), 3–5 key numbers compared with the
  previous month **and the same month last year**, ○△× status with a legend, problem cards, task table by team, 30/60/90 days,
  a fixed "definitions and how to check" page; a talk page and expected questions when someone presents for us.
- Bad news: confirmed fact / possible cause / still to check, with the fix; no ranking promises (Google: no one can guarantee #1).
- Japanese writing for reports follows 公用文作成の考え方 (2022) and the やさしい日本語 guideline, step 1.
- Measurement: never `utm_` on links between your own domains (it overwrites the real source); use cross-domain measurement
  and a plain parameter + hidden form field; hostname filter when a property gets another domain's hits.
- Moving part of a site: one-to-one 301s, keep at least 1 year, Change of Address is for whole domains only; a 301 to a
  thinner page still loses the ranking.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Links between our own domains carry `utm_` parameters | they overwrite the visitor's real source in GA4 | which links, which domains |
| A GA4 property receives hits from another hostname | totals are mixed | hostnames and their share of sessions |
| Sessions that start on thank-you pages | the form flow breaks the session (other domain, booking system) | share of key events |
| A section moved to another domain with 302s or to thinner pages | rankings are lost | URLs, redirect type, target page |
| Client reports without "how to fix" and "how to check" | data alone does not lead to action | which reports |

## 2026-10-12 — WebP by default (native WordPress)

Files changed: `wp-performance.md` (Images).

What changed in the guidance:
- Every site we build uses WordPress's native WebP output for JPEG uploads (filter `image_editor_output_format`, quality 82); originals kept; PNG/SVG/GIF and site icons unchanged; share images stay JPEG. Existing images are converted with `wp media regenerate`. Rolled out first on wp-anshin-com (staging): a list card went from the 356 KB original to a 13 KB WebP.
- `sizes` must match the image slot (cards asking for `100vw` download the original).

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Images served as JPEG/PNG photos (page source `src`/`srcset`) | WebP is ~30–90 % smaller; native in WordPress since 5.8 | how many, which theme/builder, whether a plugin (EWWW, ShortPixel, WP Rocket) already converts |
| Cards/thumbnails loading the full-size original (`sizes="100vw"` on small slots) | wasted MBs on phones | page, element, file size loaded |
| og:image in WebP | Facebook/LINE previews may fail | page and URL |

## 2026-10-12 — Post slugs carry the title's keywords

Files changed: `seo-geo/README.md` (Japanese specifics).

What changed in the guidance:
- A post slug must describe the post with keywords from its title (English/romaji), not just a series name + date; a date may be appended for repeating posts. Automated posts build the slug from the same facts as the title. Found on wp-anshin-com, whose automated security posts used `security-news-YYYY-MM-DD`.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Post slugs that are only a series name, a number or a date (`news-2026-10-01`, `?p=123`, `post-5`) | the slug is a small relevance and click signal and tells readers what the page is | count, examples, whether old slugs would redirect |
| Automated or imported posts (n8n, RSS, AI drafts) | slugs are often generated from dates or IDs | which workflow, how the slug is built |

## 2026-10-11 — Folder created; pass 1 (merge) and pass 2 (verification) done

Files changed: all. Sources and dates in each topic's `SOURCES.md`; status line at the top of every file.

What changed in the guidance:
- Japanese typography now follows DADS: body and UI text 16 px, floor 14 px (never below), line height 1.7–1.75 body / 1.4 headings, letter spacing 0.02 em (0 at 45 px+), size scale 16–45 px, Noto Sans JP as reference font, no italics, links underlined, ruby 50 %. 禁則処理 and Latin-in-Japanese rules from JLReq.
- Accessibility: WCAG 2.2 is the target (JIS X 8341-3 still equals WCAG 2.0; revision pending). Six new criteria: target size 24 px, focus not obscured, dragging alternatives, redundant entry, consistent help, accessible login. Japanese large text = 22 pt regular / 18 pt bold before 3:1 contrast is allowed.
- Flatsome (3.20.11 files): button colour is `color=`, shape is `style=`; `[accordion-item]` with hyphen; `[testimonial image= company=]`; no `.m-8` utility scale; visibility values are the four `hide/show-for-small/medium`; breakpoints 549 / 849 px; four filters from old notes do not exist.
- SWELL (2.19): official block list; slugs `loos/`; CSS variables verified, no `--color_accent`; official plugin list (Contact Form 7 not incompatible; SEO SIMPLE PACK is the house SEO plugin).
- SEO/GEO: Google sets no length limit on titles or descriptions; no special markup for AI Overviews / AI Mode; FAQ rich results ended 2026-05-07, HowTo in 2023, seven more types in June 2025; helpful-content and E-E-A-T rules recorded.
- Law: stealth-marketing designation details (2023-10-01), No.1-claim conditions (2024 report), 2024-10-01 amendment with direct fines.
- Security and performance: WordPress hardening baseline; PHP 8.2 security support ends 2026-12-31; Core Web Vitals thresholds and the 75th-percentile rule; WP Rocket exclusion field.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| PHP version | 8.1 or lower is end of life; 8.2 loses security fixes on 2026-12-31; WordPress recommends 8.4/8.5 | version, host, whether staging exists to test an upgrade |
| Text under 14 px, Japanese body line height under 1.5 | DADS floor; readability | where (template, CSS rule), how many places |
| Sticky header or bar that covers a focused form field | WCAG 2.2 focus not obscured | pages with sticky elements and forms |
| Controls that need dragging (sliders, carousels without arrows) | WCAG 2.2 dragging movements | element and page |
| Icon buttons or links smaller than 24 × 24 px with no spacing | WCAG 2.2 target size | element and page |
| Links shown by colour only | DADS: underline links | main content area |
| FAQ / HowTo schema present | no longer earns rich results; harmless | note only, no action |
| Titles / meta descriptions | no Google limit; no action unless truncated badly on phones | note only |
| Flatsome sites: buttons written as `style="primary"` in content | `color=` is the real attribute; Flatsome tolerates the old one, but new content should use the right form | note only |
| 「No.1」「最高」「限定」「今だけ」 claims, paid posts without 「PR」 | 景品表示法, ステマ規制 | page and wording |
| Backups stored only on the server | hardening guide: off-server copy | where backups go |

Priority: the live www.wp-anshin.com and the SKYUS staging first; then the SPINGLE sites and clark.ed.jp.

## How to add an entry

1. Change the topic file(s); update their `Status:` line and `SOURCES.md`.
2. Add an entry here: date, what changed, and a checklist row for anything that affects existing sites. Leave the checklist out when nothing does.
3. Commit and push. Nothing else is needed: every project reads this file at its next session.
