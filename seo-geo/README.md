# SEO and GEO (AI answers) for WordPress pages

Status: **verified 2026-10-11** against Google Search Central (AI features and your website; title links; snippets and meta descriptions; creating helpful, reliable, people-first content; structured data general policies; FAQ structured data change log; the June 2025 "simplifying search results" post) and Yoast (meta description and title articles). Japanese-specific lengths are practice, not a Google rule, and are marked as such. URLs and read dates: `SOURCES.md`.

**Procedure and tools live in `../../seo-audit-kit/`** (playbook, checklist, templates, Search Console and PageSpeed tools, the `/seo-audit` skill). This file is the knowledge the kit and every project share.

## Principles (Google)

- Google's guidelines win over any plugin score, including Yoast's traffic lights.
- **People-first content.** Google's own test questions: does the page add original information, research or analysis; does it go beyond the obvious; is it produced well, not sloppy or mass-produced; does it give reasons to trust it (sourcing, author information); is it free of easily verified factual errors; would someone coming to the site directly find it useful? Warning signs: content made mainly to attract search visits, many topics in the hope some rank, mass automation, date changes without real updates.
- **E-E-A-T** (experience, expertise, authoritativeness, trust): "trust is most important". Not a ranking factor itself, but what the systems look for; weighted more on health, money, safety topics (YMYL). Show **Who** (real author, byline, link to author information; never fabricated profiles), **How** (how the content was made, including AI use where readers would ask), **Why** (made to help people, not to rank).
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

- One H1, visibly the most prominent heading. H2 for sections, H3 inside. Question headings match searches and AI answers (「〜とは？」「〜の費用は？」 / "How much does it cost?").
- **Definition block:** answer the main question in the first 150 characters/words. ✅「通信制高校とは、毎日通学せずに自分のペースで学べる高校です。」 ❌「このページでは〜について説明します。」
- Cover what a searcher needs to decide, not a word count. Thin pages are a problem; padding is a worse one.
- Author box and a real last-updated date on time-sensitive pages. FAQ sections with real customer questions, visible on the page.
- Dates in titles (「2026年度版」) only when the page really is updated each year.

## Japanese specifics (practice)

- One idea, several spellings: 漢字 / ひらがな / カタカナ / English (「問い合わせ」「お問合せ」, 「ウェブ」「Web」). Use the form people search (Search Console, ラッコキーワード, Keyword Planner) and the others naturally.
- Strong local intent: 「地域名 + サービス」 in title and headings for local businesses. Keep Google Business Profile and Yahoo!プレイス current.
- Google is the main engine; Yahoo! JAPAN uses Google's index, so Google covers both except local listings.
- Slugs in English/romaji (`/tsushinsei/`, `/campus/tokyo/`); Japanese slugs become long encoded URLs.

## Links and images

- Internal links from related pages to important ones with descriptive anchors; every important page reachable in a few clicks.
- External links to trustworthy sources for facts; `rel="sponsored"` for paid links, `rel="ugc"` for user-added.
- Images: descriptive file names and alt text, right size, WebP, width and height set, hero not lazy-loaded (`../wp-performance.md`).

## Structured data (JSON-LD)

Google's policies: mark up only **content visible on the page**; markup must be a true representation of the page; no fake reviews or unrelated items; keep time-sensitive data current; image URLs crawlable; include every required property; put the markup on the page it describes (and on duplicates, not only the canonical); JSON-LD recommended; never block those pages. A structured-data manual action removes rich-result eligibility but does not change ranking.

What still earns a rich result and what does not (2026-10):
- **Gone: FAQ rich results** (stopped 2026-05-07; documentation removed 2026-06-15). **HowTo** gone since 2023. Removed in June 2025: Book actions, Course info, Claim review, Estimated salary, Learning video, Special announcement, Vehicle listing. Existing markup does no harm and needs no removal, but it earns nothing in Google's results.
- Worth keeping, when real: Organization / LocalBusiness / EducationalOrganization (name, address, phone matching the page and Business Profile), Article (author, dates), BreadcrumbList, Product / Review / Offer for shops (real prices and reviews only), Event (real dates; update or remove after), VideoObject, JobPosting.
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
