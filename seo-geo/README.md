# SEO and GEO (AI answers) for WordPress pages

Status: **verified 2026-10-11** against Google Search Central (AI features and your website; title links; snippets and meta descriptions; creating helpful, reliable, people-first content; structured data general policies; FAQ structured data change log; the June 2025 "simplifying search results" post) and Yoast (meta description and title articles). Sections "Spam policies by name", "Ranking systems" and "Crawling and indexing for WordPress" checked 2026-10-15 (Google Search Central, ranking-systems guide, Quality Rater Guidelines 2025-09-11, OpenAI and Perplexity crawler docs, WordPress core). Sections "GEO beyond Google", "Multilingual sites" and "Social previews, icons, 404 and thank-you pages" checked 2026-10-15 (Google Search Central, Facebook, X, Apple, WordPress core, KDD 2024 paper). Japanese-specific lengths are practice, not a Google rule, and are marked as such. URLs and read dates: `SOURCES.md`.

**Procedure and tools live in `../../seo-audit-kit/`** (playbook, checklist, templates, Search Console and PageSpeed tools, the `/seo-audit` skill). This file is the knowledge the kit and every project share.

## Principles (Google)

- Google's guidelines win over any plugin score, including Yoast's traffic lights.
- **People-first content.** Google's own test questions: does the page add original information, research or analysis; does it go beyond the obvious; is it produced well, not sloppy or mass-produced; does it give reasons to trust it (sourcing, author information); is it free of easily verified factual errors; would someone coming to the site directly find it useful? Warning signs: content made mainly to attract search visits, many topics in the hope some rank, mass automation, date changes without real updates.
- **E-E-A-T** (experience, expertise, authoritativeness, trust): "trust is most important". Not a ranking factor itself, but what the systems look for (Google: quality raters "have no control over how pages rank"; their data is not used directly in ranking); weighted more on health, money, safety topics (YMYL). Show **Who** (real author, byline, link to author information; never fabricated profiles), **How** (how the content was made, including AI use where readers would ask), **Why** (made to help people, not to rank).
- **AI-drafted text** is allowed; it is judged by effort, originality and accuracy. "Generative AI to produce large amounts of text without manual oversight" is spam. Every published AI draft is reviewed by a person; disclose automation where it matters.
- Search intent first: know (guide, FAQ), do/buy (service, product, contact) or go (brand). The page type must match. Ask for the main keyword if unclear.
- Never: keyword stuffing (text, headings, titles, alt), hidden text or links, doorway pages, schema for invisible content, invented reviews, mass thin pages, changing an existing slug without a redirect, promising rankings.

## AI Overviews and AI Mode (GEO)

Google's statement: **"There are no additional requirements to appear in AI Overviews or AI Mode, nor other special optimizations necessary."** No AI text files, no new markup, no special schema. What helps is what already helps Search: crawlable (robots.txt and CDN), good internal links, good page experience, **important content as text** (not images or JavaScript-only), images and video that support the text, structured data that matches the visible page, current Business Profile and Merchant Center data. AI traffic is counted as normal web search in Search Console. Controls: `nosnippet`, `data-nosnippet`, `max-snippet`, `noindex`; Google-Extended for training.

What this means in writing: a clear, self-contained answer under a question heading in the first paragraph; specific dated facts with sources; lists and tables for comparisons; the author or organisation named; the page kept current. Nothing in a tab, accordion or "read more" that needs a click to exist in the HTML.

## Title and meta description

| | Google's rule | Yoast's check | Our practice |
|---|---|---|---|
| Title | **No length limit**; truncated to fit the device width. Describe the page, no boilerplate, no keyword repetition, brand once (home page may be fuller), language matches the page, one clearly dominant H1 | pixel-width check (orange when too wide); site name and separator excluded from the check | English about 50–60 characters; Japanese about 28–35 全角字 (wider glyphs); keyword first, brand last with the site's separator (「｜」 common in Japan) |
| Meta description | **"There's no limit on how long a meta description can be"**; unique per page, specific, with concrete facts (date, price, author); not a keyword list; Google often writes its own from the page | flags under 120 or over 156 characters | English 120–155 characters; Japanese: put the answer and keyword in the first ~50字 (what phones show), stay under ~120字 (practice; Yoast's 156 counts Japanese characters one by one and is too long for display) |

Google rewrites titles that are half empty, outdated, inaccurate, boilerplate across pages, unclear (several equally prominent headings), in the wrong language, or that repeat the site name. Fix the cause rather than fighting the rewrite.

## Headings and content

- One H1, visibly the most prominent heading. H2 for sections, H3 inside, no skipped levels. This is accessibility and clarity, not a Google rule (Google: heading order does not affect Search; it uses the main heading and other headings as sources for the title link). Question headings match searches and AI answers (「〜とは？」「〜の費用は？」 / "How much does it cost?").
- **Definition block:** answer the main question in the first 150 characters/words. ✅「通信制高校とは、毎日通学せずに自分のペースで学べる高校です。」 ❌「このページでは〜について説明します。」
- Cover what a searcher needs to decide, not a word count. Thin pages are a problem; padding is a worse one.
- Author box and a real last-updated date on time-sensitive pages. FAQ sections with real customer questions, visible on the page.
- Dates in titles (「2026年度版」) only when the page really is updated each year.

## Japanese specifics (practice)

- One idea, several spellings: 漢字 / ひらがな / カタカナ / English (「問い合わせ」「お問合せ」, 「ウェブ」「Web」). Use the form people search (Search Console, ラッコキーワード, Keyword Planner) and the others naturally.
- Strong local intent: 「地域名 + サービス」 in title and headings for local businesses. Keep Google Business Profile and Yahoo!プレイス current.
- Google is the main engine; Yahoo! JAPAN has used Google's search engine since 2010, so Google covers both except local listings (the contract was due for renewal in 2025; no public statement on the outcome found 2026-10-15, re-check).
- Slugs in English/romaji (`/tsushinsei/`, `/campus/tokyo/`), lowercase, words joined by hyphens (not underscores); Japanese slugs become long encoded URLs when shared in LINE or email. This is our house rule: Google itself allows Japanese words in URLs (UTF-8, percent-encoded) and even suggests the audience's language, so an existing Japanese-slug site is not wrong.
- A post slug says what the post is about: short English/romaji keywords taken from its title (`/security/news/yakiniku-king-app-unauthorized-access-2026-10-08/`), never only a series name + a date (`/security-news-2026-10-08/`). A date may be added at the end for repeating posts (weekly reports) to keep slugs unique. Automated posts: build the slug from the same facts as the title. Changing a published slug: WordPress keeps the old one for posts (`_wp_old_slug`) and redirects; pages and categories need a 301.

## Links and images

- Internal links from related pages to important ones with descriptive anchors; every important page reachable in a few clicks.
- External links to trustworthy sources for facts; `rel="sponsored"` for paid links, `rel="ugc"` for user-added.
- Images: descriptive file names and alt text, right size, WebP, width and height set, hero not lazy-loaded (`../wp-performance.md`).
- Text belongs in HTML, not in images (WCAG 1.4.5). When a banner has text baked in, its `alt` repeats that text (WCAG 1.1.1); the page is still indexed without it, but that text is lost to search and screen readers.

## Structured data (JSON-LD)

Google's policies: mark up only **content visible on the page**; markup must be a true representation of the page; no fake reviews or unrelated items; keep time-sensitive data current; image URLs crawlable; include every required property; put the markup on the page it describes (and on duplicates, not only the canonical); JSON-LD recommended; never block those pages. A structured-data manual action removes rich-result eligibility but does not change ranking.

What still earns a rich result and what does not (2026-10):
- **Gone: FAQ rich results** (stopped 2026-05-07; documentation removed 2026-06-15). **HowTo** gone since 2023. Removed in June 2025: Book actions, Course info, Claim review, Estimated salary, Learning video, Special announcement, Vehicle listing. Existing markup does no harm and needs no removal, but it earns nothing in Google's results.
- **No self-serving review stars:** reviews a business controls about itself (Organization or LocalBusiness, including embedded Google or Facebook review widgets) are not eligible for star ratings (review-snippet guidelines).
- Worth keeping, when real: Organization / LocalBusiness / EducationalOrganization (name, address, phone matching the page and Business Profile; Google's Organization properties include `legalName`, `address`, `foundingDate`, `numberOfEmployees`, `logo`, `sameAs` and `taxID`, where a Japanese company puts its 13-digit 法人番号; `founder` is not in Google's list. Google says this helps it understand the organisation's details; it claims no ranking or E-E-A-T boost), Article (author, dates), BreadcrumbList, Product / Review / Offer for shops (real prices and reviews only), Event (real dates; update or remove after), VideoObject, JobPosting.
- **Yoast already prints** Organization/WebSite, WebPage, Article, BreadcrumbList and more. Never add duplicate JSON-LD by hand; prefer Yoast's settings. Check what is there first.
- Rules of the house: ISO dates, absolute production URLs, `JSON_UNESCAPED_UNICODE` when printed from PHP, validate with the Rich Results Test (a person runs it). Adding schema to a theme is a code change: draft, explain, approve.

## Staging and duplicates

Staging is `noindex` on purpose (Yoast warns; correct). On production avoid two pages for the same keyword: merge or differentiate.

## Before publishing a new page

Keyphrase and intent defined · title and description written to the table above · one H1 with the keyphrase · definition block · question headings · at least one internal link in and out · a source for facts · images sized with alt · author and date visible · schema needs checked · Rich Results Test by a person.

## What changed in pass 2 (2026-10-11)

- Google states no length limits for title or description; Japanese lengths kept as practice and the ⚠ conflict closed (first 50字 matter, under ~120字).
- AI Overviews / AI Mode guidance added from Google: no special markup or files; text content and normal SEO.
- FAQ rich results removed (May 2026) and the June 2025 removals listed; HowTo confirmed gone.
- Helpful-content self-assessment, E-E-A-T with "trust is most important", Who/How/Why and the AI-content rule added.
- Structured data policies quoted from Google.

## GEO beyond Google (checked 2026-10-15)

- Google: no special markup or optimisation for AI features. Claims such as "AI engines read the first 40 words after an H2" or "JSON-LD / FAQPage is critical for GEO" have no source.
- Research on other answer engines (Aggarwal et al., KDD 2024, tested on Perplexity and a benchmark): adding **statistics, quotations and cited sources** raised visibility by up to about 40 %, with results varying by topic. Tables and lists were not tested; they help readers, which is reason enough.

## Multilingual sites (checked 2026-10-15)

- One URL per language (`/ja/`, `/en/`), each page linking its versions with `hreflang` (`ja`, `en`, plus `x-default` for the fallback, usually the language picker or main version). Language codes ISO 639-1, regions ISO 3166-1 (`en-US`).
- **Never redirect automatically by IP address or browser language**: Googlebot usually crawls from the USA and would only see the English version. Show a visible language switcher (EN / JP) in the header instead.
- WPML or Polylang print `hreflang` themselves; check, do not add by hand (`../wp-plugins/wpml.md`).

## Social previews, icons, 404 and thank-you pages (checked 2026-10-15)

- **og:image** 1200 × 630 (Facebook's recommendation, ratio 1.91:1; X crops to 2:1, LINE and Slack use the same tag). **JPEG or PNG, not WebP** (some apps fail on WebP), under 5 MB (X's limit; Facebook allows 8 MB), with `og:image:width`, `og:image:height`, `og:image:alt` and `twitter:card` = `summary_large_image`. Keep important text away from the edges. The Open Graph protocol itself sets no size. Yoast / SEO SIMPLE PACK print these tags; set a default image site-wide.
- **Icons:** WordPress **Site Icon** (upload at least 512 × 512; WordPress 6.5+: 設定 → 一般 → サイトアイコン, classic themes also Customizer → サイト基本情報) creates 32, 64, 180 (Apple touch icon), 192 and 270 px versions; that covers phones and tabs. Google's search favicon: square, larger than 48 × 48 recommended, PNG/ICO/GIF/JPEG (**SVG is not in Google's list**). An extra SVG favicon for sharp tabs and dark mode is optional (Safari only from 26).
- **404 page:** on-brand, with search and links home and to the main sections, and it **must return HTTP 404** (WordPress's `404.php` does). A normal-looking page with status 200 for missing URLs is a "soft 404".
- **Thank-you page** after a form: what happens next and when (「2営業日以内にご連絡します」), a link back; `noindex` (practice; Google does not require it). The GA4 key event is the form's `form_submit`, not this page view (`measurement.md`); count thank-you page views only when the form sends no event.

## Spam policies by name (checked 2026-10-15)

Google Search Essentials (formerly the Webmaster Guidelines) has three parts: technical requirements, **spam policies**, key best practices. The spam policies, in the words a report should use:
- **Scaled content abuse:** many pages made mainly to rank, with or without AI, that add no value. Volume itself is not the test; value per page is.
- **Doorway abuse:** near-identical pages per city or station (「渋谷 ホームページ制作」「新宿 ホームページ制作」) that funnel to one page. Local pages are fine when each has its own real content (address, staff, cases, access).
- **Expired domain abuse:** buying an old domain to use its links or reputation. Buying a domain for a real business is fine.
- **Site reputation abuse:** third-party pages published on a strong site mainly to borrow its ranking (coupon, payday or affiliate sections on a news or university site). Since November 2024 the host's involvement or oversight is no excuse. Editorial columns, syndication and press wires are not abuse.
- **Link spam:** buying or selling links that pass credit, excessive link exchanges, networks of sites made to link, automated comment links, and **keyword-rich anchors in guest posts and press releases** (PR TIMES included). A normal editorial guest post with a plain link is fine.
- **Cloaking, hidden text and links, sneaky redirects, keyword stuffing, scraped or spun content, thin affiliate pages, user-generated spam.**
- Not spam: tabs and accordions whose text is in the HTML (Google indexes it; text loaded only on click is not indexed); AI-assisted text a person edits; small, easy-to-close banners. Large pop-ups that block the page "may lead to poor search performance"; legally required interstitials (an age gate where the law demands it, legal notices) are exempt; a cookie banner is safe when it is small and easy to close.

## Ranking systems: what Google documents, and common myths (checked 2026-10-15)

- Google's ranking-systems guide lists current systems (RankBrain, BERT, neural matching, passage ranking, freshness, reviews, reliable information, spam detection, site diversity…). The **helpful content system was retired in March 2024** and became part of the core systems; its questions (people-first content, above) still apply.
- **Not documented by Google, do not present as fact:** NavBoost (known only from the 2023 US antitrust trial, where Google said aggregated click data is one signal, and from leaked internal documents in 2024; never from Google's own guidance); an "information gain" score (a 2018 patent for assistants, never confirmed for web ranking); dwell-time or pogo-sticking thresholds ("back within 5 seconds"); a "#1 signal"; "topical authority" as a site score (Google's topic-authority system is for news only).
- What holds without myths: match the format searchers expect (look at the current results first), add something the other results lack (data, prices, local facts, first-hand photos), answer early, load fast.
- **Freshness** matters only for queries that need it. Update a page when the facts change; changing the date without real changes is a warning sign in Google's own checklist. Visible date and `dateModified` must match a real update. No fixed interval.
- **HTTPS** is a lightweight ranking signal and the canonical Google prefers; required in practice because browsers warn on HTTP.
- **Quality Rater Guidelines** (edition of 2025-09-11): YMYL = health or safety, financial security, government, civics and society (elections added 2025), and other topics that can cause harm. YMYL pages need more trust, not a fixed checklist: real author or supervisor (監修者) with credentials, sources, company details. A 監修 byline helps trust; no "ranking boost" is documented.

## Crawling and indexing for WordPress (checked 2026-10-15)

- **robots.txt** manages crawling, **not** what appears in search. WordPress's default (virtual) file: `Disallow: /wp-admin/`, `Allow: /wp-admin/admin-ajax.php`, plus a sitemap line (core's since 5.5, or Yoast's); keep it. Blocking cart, checkout and `?s=` search results is optional crawl hygiene. **Never block `/wp-content/` or `/wp-includes/`** (CSS, JS, images): Google renders pages like Chrome.
- To keep a page out of results use **`noindex`**, and do not block that page in robots.txt (Google must crawl it to see the noindex). Candidates: thank-you pages, login, internal search, empty archives, staging.
- **AI crawlers** (robots.txt user agents): `OAI-SearchBot` (ChatGPT search; allow for visibility), `GPTBot` (OpenAI training), `PerplexityBot` (Perplexity search; allow), `Google-Extended` (Gemini training and grounding; **no effect on Google Search**). User-triggered fetchers (`ChatGPT-User`, `Perplexity-User`) may ignore robots.txt. Blocking training bots is the owner's policy choice.
- **XML sitemap:** the URLs you want in search results (Google); in practice only canonical, indexable 200 URLs, no redirects, 404s or noindex pages (Search Console flags them). Google uses `lastmod` only if it is consistently accurate (real content changes, not a footer year); it ignores `priority` and `changefreq`. Yoast builds its own sitemap and turns the core one off; SEO SIMPLE PACK has no sitemap, so SWELL sites use WordPress's core `wp-sitemap.xml`. Since WordPress 6.5 the core sitemap prints `lastmod` for posts and pages (none for term and author archives, which is not a fault).
- **Canonical:** every page has a canonical to itself (absolute, HTTPS, one host); URLs with `utm_` or `gclid` point to the clean URL; http/https and www/non-www variants 301 to one. With `hreflang`, each language page is canonical to itself, never to another language.
- **Go-live check:** WordPress **設定 → 表示設定 → 「検索エンジンがサイトをインデックスしないようにする」** must be **unticked** on the live site (when ticked, WordPress prints `noindex` on every page). Also check the SEO plugin's noindex settings and that Search Console shows pages getting indexed.
- **Outbound links:** `rel="sponsored"` for ads, paid placements and affiliate links (`nofollow` also accepted); `rel="ugc"` for comments; nothing on normal editorial links; **never `nofollow` on internal links**.
