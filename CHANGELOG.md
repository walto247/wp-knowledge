# Changelog — what changed in the shared knowledge, and what to check on existing sites

Newest first. Every project reads the **top entry** at the start of a session (rule in `CC-projects/CLAUDE.md`).
An entry has two parts: what changed in the files, and a **checklist for existing sites** (check and report; change only with the owner's OK and each project's own rules).

## 2026-10-16 — Client reports: GA4 and Search Console terms, diagnosis table, page-by-page report

Files changed: `seo-geo/measurement.md` (average position, new sections "GA4 numbers and their names", "Search Console inside GA4, and Looker Studio", "AI Overviews and clicks"), `seo-geo/reporting.md` (target vs actual, status marks, cadence, dashboards, new sections "Diagnose before writing", "Client report, page by page", seasonality, words for numbers, cover message templates, frameworks), `seo-geo/SOURCES.md`.
Checked three pasted articles on GA4 + Search Console reporting against Analytics, Search Console and Looker Studio help, Search Central, Pew Research, WCAG and the original framework sources; corrected claims listed in `seo-geo/SOURCES.md`.

What changed in the guidance:
- Search queries cannot be joined with GA4 key events; report search → key events per landing page.
- Users are devices, not people (ユーザー数（概算）); no "time on page" (average engagement time); 精読率 is not engagement rate; average position is topmost and impression-weighted.
- Looker Studio is not real time (Search Console 12 h; GA4 12 h by default) and stays our working tool; the client gets a 4–6 page written report with a "what we did" before/after page and a next-month table that names who acts (us or the client).
- Diagnosis patterns with "check before concluding" (e.g. mobile visits but PC enquiries is not automatically broken mobile; AI Overviews is a hypothesis).
- Status marks ○△× with words, colour never alone, no emoji; Japanese holidays: business-day-aware comparisons.

### Checklist for existing reports (run at the next report of each project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| A "conversion rate per keyword" or similar query-level GA4 figure | Google's data cannot produce it | report, figure, where it came from |
| "Users" presented as people; "time on page"; 精読率 used for engagement rate | wrong terms | report, wording |
| Status shown by colour or emoji only | WCAG 1.4.1; lost in print | report pages |
| Monthly client report without a page showing the work done (before/after) or who acts next month | the client cannot see the value or their own tasks | report |
| GA4 Search Console reports not published, or Search Console not linked | the landing-page view is missing | property |
| Engaged-session timer not 10 s and no method note in the report | months stop being comparable | property setting, date changed |

## 2026-10-15 (evening) — sideways rows are allowed (owner)

Files changed: `design/general.md` (phone-first line). "No sideways scrolling" means the page itself; a deliberate sideways row of cards inside a section (works, news, programs) is fine and expected on phones: scroll-snap, swipe, mouse drag or arrows on PC, the next card peeking in. Automated checks flag only the page width, not inner scrollers.

### Checklist for existing sites
None (a clarification; nothing to check).

## 2026-10-15 — Google rules: spam policies, ranking myths, crawling and indexing

Files changed: `seo-geo/README.md` (E-E-A-T and raters, Yahoo! JAPAN status, URL rule as house rule, new sections "Spam policies by name", "Ranking systems", "Crawling and indexing for WordPress"), `seo-geo/SOURCES.md`.
Checked a pasted article on Google's guidelines against Google Search Central, the ranking-systems guide, the Quality Rater Guidelines (2025-09-11), OpenAI and Perplexity crawler docs and WordPress core; rejected claims listed in `seo-geo/SOURCES.md`.

What changed in the guidance:
- Spam policies named one by one for reports (scaled content, doorway pages per city, expired domains, site reputation abuse, link spam incl. keyword anchors in press releases). Separately, a structured-data guideline: no self-serving review stars.
- Ranking: helpful content system retired into core (2024-03); NavBoost, information gain, dwell-time thresholds and "#1 signal" are not Google-documented; date changes without real updates are a warning sign.
- Crawling and indexing: robots.txt is not for hiding pages; never block `/wp-content/`; AI crawler names and what each does; sitemap and `lastmod` rules; self canonicals; the WordPress "discourage search engines" box must be off on live sites; `sponsored` / `ugc`, never `nofollow` on internal links.
- Slugs in romaji stay our house rule; Google allows Japanese URLs.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| 設定 → 表示設定 「検索エンジンがサイトをインデックスしないようにする」 ticked on a live site | every page is `noindex` | site, setting |
| robots.txt blocks `/wp-content/`, `/wp-includes/`, CSS or JS, or blocks pages that carry `noindex` | Google cannot render, or cannot see the noindex | robots.txt lines |
| AI crawlers blocked (`OAI-SearchBot`, `PerplexityBot`) or allowed without the owner knowing | visibility in AI search is the owner's choice | robots.txt lines, CDN/WAF bot rules |
| Sitemap lists redirects, 404s or noindex pages; `lastmod` on posts changes daily without edits (missing `lastmod` on term or author entries is normal) | Google stops trusting the sitemap | sitemap URL, examples |
| Pages without a self canonical, or a language version canonical to another language | duplicates, lost language versions | page, canonical printed |
| Paid, sponsored or affiliate links without `rel="sponsored"`/`nofollow`; `nofollow` on internal links | link spam policy; wasted internal links | page, link |
| Star ratings (AggregateRating) for the business's own reviews or widgets | self-serving reviews are not eligible (review-snippet guideline) | page, markup source |
| City or station landing pages with near-identical text | doorway abuse | URLs, how similar |
| Full-screen pop-up on load (other than a small, legally required notice) | may hurt search performance | page, trigger |

## 2026-10-15 — Page structure, SEO/GEO extras, social previews and icons, 特商法 and 外部送信

Files changed: `design/general.md` (new section "Content blocks and page order"), `design/japan.md` (top page order, English display headings), `seo-geo/README.md` (headings, images of text, Organization properties, new sections "GEO beyond Google", "Multilingual sites", "Social previews, icons, 404 and thank-you pages"), `wp-performance.md` (Japanese font slices, image size targets), `legal/japan.md` (特商法 表記 details, 最終確認画面, 外部送信, cookie consent), the three `SOURCES.md`, `README.md`.
Checked a pasted article against Google Search Central, WCAG 2.2, NN/g, Facebook/X/Apple docs, WordPress core, the KDD 2024 GEO paper, 消費者庁 and 総務省; rejected claims listed in the `SOURCES.md` files.

What changed in the guidance:
- Pages: section intro (eyebrow → H2 → lead), cards for three or more points, descriptive link text instead of "Learn more", zigzag only for 2–3 informational rows, HTML in reading order, no auto-advancing hero sliders, a home-page order (Japanese version with お知らせ under the hero, 実績 with industry tags, ご利用の流れ).
- SEO/GEO: one H1 is clarity, not a Google rule; no special AI markup; statistics, quotations and sources help on answer engines (research); Organization with `taxID` = 法人番号; text in images repeated in `alt`.
- Multilingual: one URL per language, `hreflang` + `x-default`, never redirect by IP or browser language.
- Polish: og:image 1200 × 630 JPEG/PNG with alt; WordPress Site Icon 512 (gives the 180 Apple icon); PNG favicon for Google; 404 returns status 404; thank-you page with next steps.
- Law: 特商法 表記 for goods and paid services, 返品特約 never omitted, omission rule 「請求があれば遅滞なく」; 外部送信 is a notice duty for media, malls and services (not company sites); cookie consent when a site targets EU/UK visitors.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Rows of "詳しくはこちら" / "Learn more" links | WCAG 2.4.4; unclear for everyone | page, how many |
| Auto-advancing hero slider without a pause button | WCAG 2.2.2; later slides go unseen | page |
| Missing `og:image`, or none set site-wide (WebP share images: see the WebP entry below) | blank previews in LINE, X, Slack | page, current image |
| Site Icon not set, or no 180 px Apple touch icon | blank icons in tabs, search results, home screens | what is printed in `<head>` |
| Missing URLs that return status 200 instead of 404 | soft 404 | test URL, status |
| Language versions that redirect automatically, or no `hreflang` | Google may only see one language | which versions |
| Shops and paid services: 特商法 表記 without 返品特約, or 最終確認画面 incomplete | 特商法 11条, 12条の6 | page, missing items |
| Tracking or chat scripts not listed in the privacy policy (外部送信 table) | duty for sites in scope of 外部送信規律 (media, malls, apps, services); good practice for company and own-goods sites | scripts found, policy section, whether the site is in scope |

## 2026-10-15 — Navigation, colour and surfaces, motion, Japanese forms

Files changed: `design/general.md` (new section "Navigation, surfaces and motion", card spec), `design/japan.md` (navigation, forms, new subsection "Surfaces, photos and trust pages"), `design/SOURCES.md`, `README.md`.
Checked a pasted "premium website" article against WCAG 2.2, DADS, Material 3, NN/g, MDN, web.dev and the 消費者庁 guideline; rejected and softened claims listed in `design/SOURCES.md`.

What changed in the guidance:
- Navigation: menus open on click/tap/focus, never hover alone; menu button with a visible メニュー label; breadcrumbs between header and title; sticky header with `scroll-padding-top`; bottom bar with safe-area padding; a conversion band before the footer (Japan, practice).
- Colour and surfaces: captions no lighter than #767676 (#888 fails); input borders 3:1; one elevation scale, one radius scale, one accent; pure black text is acceptable (DADS).
- Images: one `aspect-ratio` per row with `object-fit: cover`; text over photos 4.5:1.
- Motion: ease-out curves, 150–250 ms for small changes, up to 400 ms for transitions, scroll reveals at most about 600 ms, `prefers-reduced-motion`, never hide the hero or LCP element at opacity 0.
- Japanese forms: no second email field (our default; WCAG 3.3.7 argues against it); `autocomplete` on personal fields; ※必須 / ※任意; 最終確認画面 is a legal duty only for online sales contracts.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Normal-size grey text lighter than #767676 on white (captions, dates, notes, placeholders used as labels) | fails WCAG 1.4.3 (4.5:1; large text needs 3:1) | colour, where |
| Input borders lighter than about #949494, unless the field background itself contrasts 3:1 with the page | fails WCAG 1.4.11 (3:1) | form, colour |
| Menus or sub-menus that open only on hover | keyboard and touch users cannot open them reliably (DADS; WCAG 2.1.1 / 2.4.7 / 1.4.13 depending on the build) | menu, page |
| A focused field or anchor entirely hidden under the sticky header or bottom bar | WCAG 2.4.11 (fix: `scroll-padding-top` / `-bottom`) | page, element |
| A "メールアドレス（確認）" second field | WCAG 3.3.7 argues against re-typing; our default is to drop it and show the address on the 確認 screen | form |
| Personal fields without `autocomplete` | WCAG 1.3.5 | form, fields |
| Hero, H1 or main image hidden by a scroll-reveal animation (opacity 0 at load) | delays or breaks LCP; invisible if JS fails | page, element, library |
| Scroll or click animations without a `prefers-reduced-motion` rule; sliders or tickers that cannot be paused | WCAG 2.3.3 (AAA) for the first; 2.2.2 (AA) for the second | where |
| Shops: a 最終確認画面 that does not show quantity, price and shipping, payment, delivery, application deadline (if any) and cancellation terms | 特定商取引法 第12条の6 | page, what is missing |

## 2026-10-15 — Typography: Japanese brand options, English rules, spacing rhythm

Files changed: `design/japan.md` (new subsection "Brand and premium typography"), `design/general.md` (spacing rhythm table, new section "English typography"), `design/design-tokens.md` (body line height 1.75), `design/SOURCES.md`, `README.md`.
Checked a pasted "premium typography" article against DADS, JLReq, WCAG 2.2, MDN/caniuse; its Japanese spacing, line-height and caption numbers were rejected (list in `design/SOURCES.md`). The verified Japanese values from 2026-10-11 are unchanged.

What changed in the guidance:
- Japanese: letter spacing above DADS only for short display lines and eyebrows (≤ 0.05 em); weight 500 allowed as a brand option (Meiryo has none); captions never under 14 px; body left-aligned, not justified; `palt` on headings only; automatic Japanese–Latin spacing and bracket trimming in Chrome/Safari (no typed spaces); `word-break: auto-phrase` + `text-wrap: balance` for headings; Latin font first in `font-family` with `unicode-range` / `size-adjust`; English eyebrow is never a heading tag.
- English: body line height 1.5–1.6, headings 1.1–1.25, slight negative tracking only on large display text, +0.05 em on all-caps labels, 45–75 characters per line, left-aligned.
- Spacing rhythm table: a heading is closer to its own text than to the block above (3 × on desktop, 2–2.5 × on phones); spacing scale extended with 40 / 80 / 128.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Japanese text under 14 px (captions, notes, footers) | DADS floor | where, size |
| Japanese body letter spacing above 0.05 em | no standard supports it; DADS uses 0.02 em | CSS rule, value |
| Japanese body line height above 2.0 | beyond JLReq's usual range; harder to read | CSS rule, value |
| Justified body text (`text-align: justify`) | WCAG 1.4.8; uneven gaps with Latin words | pages |
| English eyebrow labels (`ABOUT US`) coded as `<h2>`/`<h3>` | breaks the heading outline for screen readers | template, tag used |
| `palt` on body text | body should stay ベタ組み | CSS rule |

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
