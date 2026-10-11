# SEO and GEO (AI answers) for WordPress pages

Status: merged 2026-10-11 from the dashboard `seo` skill (on-page, schema), `japan-web/seo-jp`, the WSL `seo-build` and `japanese-web/seo-jp`. Not yet verified against Google Search Central, Yoast and current GEO guidance (pass 2). **Conflicting length guidance between sources is marked ⚠ and must be settled in pass 2.**

**Procedure and tools live in `../../seo-audit-kit/`** (playbook, checklist, templates, Search Console and PageSpeed tools, the `/seo-audit` skill). This file is the knowledge the kit and every project share.

## Principles

- Google Search guidelines win over any other rule, including Yoast's traffic lights. Target all three: Google guidelines, a sensible Yoast score, GEO-ready structure.
- Search intent first: know (guide, FAQ), do/buy (service, product, contact) or go (brand, login). The page type must match. Ask for the main keyword if unclear; never guess a different topic.
- Never: keyword stuffing (text, headings, titles, alt), hidden text or links, doorway pages, schema for invisible content, invented reviews or ratings, mass-produced thin pages, changing an existing slug without a redirect, promising rankings.
- Published AI-drafted text is reviewed by a person.

## Title and meta description

| | English | Japanese |
|---|---|---|
| SEO title | about 50–60 characters | about 28–35 全角字 (Google cuts at ~600 px; full-width characters are wide) |
| Meta description | about 120–155 characters | ⚠ sources disagree: 60–80字 vs 80–120字. Until verified: write the answer and keyword in the first ~50字 (what phones show) and stay under ~120字 |
| H1 | one per page; may be longer and friendlier than the SEO title | same |

- Keyword near the start, written for a human, unique on the site; brand at the end if the template adds it (never twice). Keep the site's separator (Yoast `%%sep%%`; 「｜」 is common in Japan).
- Honest: the page must deliver what the title promises. Google may rewrite descriptions; a good one still lifts clicks.

## Headings and content

- One H1. H2 for main sections, H3 inside. Question-style headings match searches and AI answers: 「〜とは？」「〜の費用は？」 / "How much does it cost?".
- **Definition block:** answer the main question in the first 150 characters/words. ✅「通信制高校とは、毎日通学せずに自分のペースで学べる高校です。」 ❌「このページでは〜について説明します。」
- Cover what a searcher needs to decide, not a word count. Remove fluff. Thin indexed pages (under ~300 words) are a problem.
- **E-E-A-T:** who wrote or supervises the content, real examples, data with sources, visible last-updated date on time-sensitive pages, author box on articles.
- FAQ sections with real customer questions, answers 60–200字 / 60–120 words, visible on the page.
- Dates in titles (「2026年度版」) only when the page really is updated each year.

## Japanese specifics

- One idea, several spellings: 漢字 / ひらがな / カタカナ / English (「問い合わせ」「お問合せ」, 「ウェブ」「Web」). Use the form people search (Search Console data or ラッコキーワード / Keyword Planner) and the others naturally in the text.
- Strong local intent: 「地域名 + サービス」 in title and headings for local businesses. Keep Google Business Profile and Yahoo!プレイス current (a person does that).
- Google is the main engine; Yahoo! JAPAN uses Google's index, so Google covers both except local listings.
- Slugs in English/romaji (`/tsushinsei/`, `/campus/tokyo/`); Japanese slugs become long encoded URLs.
- Japanese queries tend to be longer and more specific than English ones.

## Links and images

- Internal links from related pages to important ones with descriptive anchors (「学費について詳しく見る」); every important page reachable in a few clicks.
- External links to trustworthy sources for facts; `rel="sponsored"` for paid links, `rel="ugc"` for user-added.
- Images: descriptive file names and alt text (not keyword lists), right size, WebP, width and height set, hero image not lazy-loaded (`../wp-performance.md`).

## GEO: writing for AI answers

What helps people helps AI overviews and chat answers: one clear paragraph under a question heading, specific dated facts with sources, lists and tables for comparisons, the author or organisation named, the page kept current. Self-contained answers (no "see above").

## Structured data (JSON-LD)

- **Yoast already outputs** Organization/WebSite, WebPage, Article, BreadcrumbList and more. Never add duplicate JSON-LD by hand; prefer Yoast settings. Check what is already there before adding anything.
- Worth adding when real: FAQPage (every Q&A visible word for word; rich results now mostly for authoritative sites, markup still aids understanding), LocalBusiness / EducationalOrganization (name, address, phone matching the page and Google Business Profile), Event (real dates, update or remove after), Product / Review (real prices and real reviews only). HowTo is low priority (no rich results any more).
- Rules: `<script type="application/ld+json">`, only visible content, ISO dates, absolute production URLs, `JSON_UNESCAPED_UNICODE` when printed from PHP, validate with Google's Rich Results Test (a person runs it).
- Adding schema to a theme is a code change: draft the JSON-LD, explain the need, get approval.

## Staging and duplicates

Staging is `noindex` on purpose (Yoast warns; that is correct). On production avoid two pages for the same keyword: merge or differentiate.

## Before publishing a new page (checklist)

Keyphrase and intent defined · title and description written · one H1 with the keyphrase · definition block · question headings · at least one internal link in and out · one external source for facts · images sized with alt · author and date visible · schema needs checked · Rich Results Test by a person.
