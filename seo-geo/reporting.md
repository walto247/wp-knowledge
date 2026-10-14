# SEO and analytics reports for clients (English and Japanese)

Status: **researched 2026-10-14** (Google Search Central and Search Console / Analytics help read 2026-10-14; Japanese
government writing guides read in full; agency practice from their own how-to articles). Google and government points are
fact; agency points are practice (marked). Sources: `SOURCES.md` (section "Reporting"). Measurement details: `measurement.md`.

## The rule

A report says **what is wrong, how to fix it, and how to check it**: not only data. Simple beats complete. If a number
does not lead to a decision, leave it out (practice).

## Structure (one layered document)

1. **Summary, one page, written last.** The situation in 3–5 lines; 3–5 key numbers with the previous month **and the same
   month last year**; a status mark per number; the one or two main problems; the next step. Decision-makers often read
   only this page (practice).
2. **Talk page for the person who presents** (if the reader of the report is not the client): what to say in which order,
   what to ask the client for, expected questions with short answers, phrases to avoid.
3. **Problem cards**, one per problem: what is wrong (1 sentence) → evidence (1–3 numbers) → what to do (steps 1-2-3) →
   who → how to check → goal and date.
4. **Task table by team:** task / priority / team / when / material (施策・優先度・担当・期限). Developers get tickets with
   page, URLs, fix, the number it should move, effort (practice).
5. **30 / 60 / 90 days**, and when each number is checked again.
6. **Definitions and how to check:** periods, sources, filters, screen paths, a short glossary. The same every month, so
   months compare (practice).
7. Appendices: technical reports, change sheets, drafts.

Organise by business result, not by tool (no "Search Console section" and "GA4 section") (practice).

## Key numbers

- 1–3 numbers that define success for the client's goal; for lead sites: **conversions from search** (form completions,
  bookings). Rankings, impressions and CTR support them (practice).
- Keep out of the summary: domain rating, backlink counts, raw impressions, crawl lists (practice).
- Seasonal businesses (schools: 説明会 season, 出願) compare with the **same month last year** first; the previous month is
  secondary. If impressions fall while position and CTR hold, demand fell; if position or CTR moved, performance changed (practice).
- Status marks: ○ good · △ watch · × action needed, with a word and a legend at the top; they survive black-and-white
  printing (public-sector practice, e.g. 長野県 順調 / 概ね順調 / 努力を要する).

## Bad news

- Report it early, never hide a drop, give the cause and the fix together (報連相; practice).
- Separate **確定した事実 / 可能性のある原因 / 要確認事項** (confirmed fact / possible cause / still to check). A drop at the
  time of a Google update does not prove the update caused it (practice).
- Google's own list of causes for traffic drops gives neutral, no-blame wording: algorithm updates, technical issues,
  security, spam or manual actions, seasonality and changing interest, site moves (a few weeks to settle), reporting glitches (fact).
- Never promise rankings: "No one can guarantee a #1 ranking on Google" (fact). Do not quote "4 months to a year" as Google's
  words; it is not on the current page.
- Do not blame AI Overviews without data (practice).

## Writing for non-technical readers (Japanese)

Government guidance (fact):
- 文化審議会「公用文作成の考え方」(2022): 一文を短く, 一文の論点は一つ, 箇条書き for three or more items, 結論は早めに,
  専門用語・外来語をむやみに用いない (言い換えるか説明を付ける), 図表 with clear titles, understandable at 義務教育 level.
- 「在留支援のためのやさしい日本語ガイドライン」(2020), step 1 (for Japanese readers): sort the information, short
  sentences, 箇条書き, no 回りくどい言い方, カタカナ語 as little as possible; step 3: have someone check it is understood.
  Its step 2 (丁寧語 only) is for foreign readers; client reports keep normal ビジネス敬語.

Practice:
- One message per page or chart, with one sentence saying what it means and whether it is good or bad.
- Explain each technical word on first use or in a glossary; no raw tool screenshots without arrows and a caption.
- Translate numbers into business effect (visits, enquiries), with the period stated.
- For English reports the same rules apply: plain words, short sentences, conclusion first.

## Talk script and expected questions (presenter)

- トークスクリプト in 台本形式: a fixed order of points, rehearsed aloud, matching the pages (practice).
- 想定問答: question / short answer (conclusion → reason) / where the data is / fallback 「確認して後日回答します」 (no source; workable format).
- Phrases to avoid: blame, technical words, "No.1", guaranteed results.

## Cadence

Monthly is standard; every two weeks for the first 1–3 months is common; consistency matters more than frequency; weekly
SEO data is mostly noise. Layered: weekly internal checks, monthly report, quarterly review of the strategy (practice).
定例会 order (workable): 前回宿題 → サマリー → 進捗 → 課題 → 次月施策 → お願い事項・決定事項.

## How a client (or the team) checks numbers

- Search Console → Performance (検索パフォーマンス): Queries / Pages; filter with "+ New" (＋ 新規); Date → Compare
  (前年同期と比較 / previous period). Data is 2–3 days late; the newest days are preliminary (dotted line). Filtering by query
  drops anonymised queries, so totals and brand shares are approximate (fact).
- For drops: "Last 16 months", then compare the last 3 months with the previous period and year over year; sort pages by
  click difference; check Google Trends for a market-wide fall (fact).
- Search Console Insights (in Search Console since 2025): trending pages and queries, branded vs non-branded (AI-classified,
  can mislabel) (fact).
- GA4: Reports → Engagement → Landing page, compared with Organic Search; key events per page (fact).
- PageSpeed Insights: the real-visitor section (field data) first; lab numbers only to find causes (fact, see `../wp-performance.md`).
- Dashboards: Looker Studio has official Search Console and GA4 connectors and a Google template combining both (fact).
