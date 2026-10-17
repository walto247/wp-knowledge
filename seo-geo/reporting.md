# SEO and analytics reports for clients (English and Japanese)

Status: **researched 2026-10-14**; sections "Diagnose before writing", "Client report, page by page", seasonality,
words for numbers, templates and frameworks added 2026-10-16 (Analytics and Search Console help, WCAG, Minto, Kaushik;
patterns and layouts are practice) (Google Search Central and Search Console / Analytics help read 2026-10-14; Japanese
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

- Agree **one primary goal** and its key number with the client before the first report (enquiries, bookings, sales or
  awareness), and show **target vs actual** once a target exists (practice).
- 1–3 numbers that define success for the client's goal; for lead sites: **conversions from search** (form completions,
  bookings). Rankings, impressions and CTR support them (practice).
- Keep out of the summary: domain rating, backlink counts, raw impressions, crawl lists (practice).
- Seasonal businesses (schools: 説明会 season, 出願) compare with the **same month last year** first; the previous month is
  secondary. If impressions fall while position and CTR hold, demand fell; if position or CTR moved, performance changed (practice).
- Status marks: ○ good · △ watch · × action needed, with a word and a legend at the top; they survive black-and-white
  printing (public-sector practice, e.g. 長野県 順調 / 概ね順調 / 努力を要する). Colour may be added but never alone
  (WCAG 1.4.1: red/green is the common colour-blindness pair and is lost in print); no emoji traffic lights in PDFs (they
  render differently).

## Bad news

- Report it early, never hide a drop, give the cause and the fix together (報連相; practice).
- Separate **確定した事実 / 可能性のある原因 / 要確認事項** (confirmed fact / possible cause / still to check). A drop at the
  time of a Google update does not prove the update caused it (practice).
- Before naming a Google update, check the **Search Status Dashboard** (status.search.google.com). 2026 so far: core updates in March and May; spam updates in March, June, August and September (24 Sep–8 Oct); none since. Wait about a week after an update ends before reading the data (fact as of 2026-10-17).
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
SEO data is mostly noise. Google: some changes show in hours, others take months (SEO Starter Guide, fact); judge a fix after a few weeks, not days
(practice). With a two-week rhythm, send a short work update mid-month (what was done, one quick check) and the full report
at the start of the month with a 20–30 minute review call (practice). Layered: weekly internal checks, monthly report, quarterly review of the strategy (practice).
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
- Dashboards: Looker Studio has official Search Console and GA4 connectors and a Google template combining both (fact);
  Search Console data refreshes every 12 hours, GA4 every 12 hours by default (`measurement.md`). Use the dashboard to find problems; the client gets the written report
  (PDF or slides) with the reading done for them. Share the dashboard only as an extra (practice).

## Diagnose before writing (checked 2026-10-16)

Read Search Console (before the click) and GA4 (after the click) together. These patterns are **practice**: no Google
benchmark exists, so compare with the site's own history, GA4's Benchmarking report and similar pages, not fixed numbers.
Every pattern is a hypothesis; check it before it goes in a report.

| What the data shows | Likely cause | What we do | Check before concluding |
|---|---|---|---|
| Page ranks around 11–20 with many impressions | close to page 1 ("striking distance", practice) | deepen the page, answer missing questions, internal links from strong pages | intent of the query matches the page |
| Good position, CTR clearly below the site's other pages at that position | title and description do not win the click | rewrite title and description (facts, price, benefit; a year only if the page and H1 really are updated) | Google may rewrite the title; check what it shows |
| Impressions up, clicks down, key events steady | AI Overviews or other SERP features answer simple questions | shift effort to commercial queries (費用, 料金, 依頼, 比較) | query mix, brand vs non-brand, rankings (`measurement.md`) |
| Many search clicks, low engagement rate on the landing page | page does not match the search, loads slowly, answer too far down | answer and price in the first screen, speed (`../wp-performance.md`) | engagement by device; Core Web Vitals field data |
| High engagement, almost no clicks to contact | no next step | CTA in the middle and at the end; phone bottom bar (`../design/japan.md`) | click events on CTAs exist |
| Many form views (form_start), few submissions | form friction | fewer fields, ※必須/※任意, postal-code fill, no email re-type | form_start → form_submit by device; test the form on a phone |
| Most visits on phones, most key events on PCs | **not automatically "broken mobile"**: people research on phones and send from office PCs; GA4 counts devices separately | test the phone flow by hand; fix what is really broken | key-event rate by landing page and device, hour and weekday, form drop-off by device |

## Client report, page by page (practice, checked 2026-10-16)

The **monthly client PDF** (4–6 pages, landscape 16:9 slides or PDF). The seven-part structure above stays the full
document for audits and quarterly reviews; in the monthly PDF the problem cards become pages 4–5, the task table becomes
the next-month table, the talk page stays separate for the presenter, and 30/60/90 days and definitions go to the appendix.
Pages are titled by result; the tool is only named as the data source:
1. **Cover:** 〇〇株式会社 様, 月次Webサイト運用・SEOレポート, period (2026年10月度), our company name.
2. **Summary:** 3–5 key numbers (usually 3) (key events, visits, search impressions or clicks) with previous month, same month last year
   and target; ○△× status; three lines: 今月の成果 / 見つかった課題 / 来月の対策.
3. **How people find the site** (source: Search Console): money keywords with position then and now; 3 striking-distance queries (positions 11–20)
   with the plan; 1–2 new questions people searched, with a content idea. Not a 50-row keyword table.
4. **What visitors do on the site** (source: GA4): top 5 landing pages: visits, engagement rate, key events, and a one-line diagnosis and fix.
5. **What we did (施策報告):** before/after screenshot; the problem in the data → the likely cause → what we changed →
   when we will check it. This page shows the work the client pays for.
6. **Next month:** priority / what / why (the number it should move) / who (us or the client, e.g. "client: send 2 project
   photos") / by when.
Definitions and how-to-check stay as an appendix page.

## Japanese seasonality (practice)

- Business sites dip in ゴールデンウィーク, お盆 and 年末年始; schools follow the 入試 calendar. Show **前年同月比** next to
  **前月比** so a holiday dip is not read as a crash.
- Holidays move: a month with more 休日 than last year is not comparable day for day. Note the number of business days,
  compare weekday-aligned periods or divide by business days, and mark the holidays on the chart. No public Japanese
  dataset measures the size of these dips; describe them, do not quote a percentage.

## Words for numbers (Japanese reports)

| GA4 / Search Console | In the report | Note |
|---|---|---|
| Impressions / Clicks / CTR / Average position | 表示回数 / クリック数 / クリック率 / 平均掲載順位 | position: "topmost position, averaged"; show with impressions |
| Active users / Sessions | ユーザー数（概算） / 訪問数（セッション） | users are devices, not people |
| Engagement rate | エンゲージメント率 | not 精読率 |
| Average engagement time | 平均エンゲージメント時間 | no "time on page" in GA4 |
| Key events | キーイベント（お問い合わせ・資料請求など） | not "conversion" (Google Ads term); name the action |

## Cover message templates (practice)

Japanese:
> 件名：【月次ご報告】Webサイト運用状況と来月の改善について（2026年10月度）
>
> 〇〇株式会社 〇〇様
>
> いつもお世話になっております。〔会社名〕の〔氏名〕です。
> 10月度のWebサイト運用レポート（PDF）をお送りいたします。今月の成果・見つかった課題・来月の対策の3点にまとめております。
>
> ■ 今月のポイント
> 1. 成果：お問い合わせは〇件（前月比＋〇％、前年同月比＋〇％）。「〇〇」の検索順位が〇位から〇位に上がりました。
> 2. 課題：「〇〇ページ」はよく見られていますが、スマートフォンからのお問い合わせボタンのクリックが少ない状態です。
> 3. 対策：スマートフォンのボタン配置を見直し、あと一歩で1ページ目（11〜20位）の3ページのタイトルを改善します。
>
> 実施した改善の画面（ビフォー・アフター）と来月の予定は5〜6ページにございます。〇日の定例会でご説明いたします。

English:
> Subject: [Company] website report and next steps — October 2026
>
> Hi [Name], attached is the October report, kept to what happened, what we found and what we will fix.
> - Result: [X] enquiries ([+Y]% vs last month, [+Z]% vs October last year); [keyword] moved from [A] to [B].
> - Found: [page] gets good search traffic, but few phone visitors reach the contact button.
> - Next: move the button up on phones and improve the titles of 3 pages ranking 11–20.
> Before/after screenshots and next month's plan are on pages 5–6. Let's go through it on [day].

Numbers in the message must match the PDF; never round in our favour; no ranking promises.

## Frameworks behind this (checked 2026-10-16)

- **SCQ(A)** (Barbara Minto, Pyramid Principle, McKinsey): situation → complication → question → answer; put the answer
  first in summaries. "SCR" (situation, complication, resolution) is a common consulting variant.
- **PDCA** (Shewhart and Deming; named Plan-Do-Check-Act in Japan): the month's report is the Check, next month's table the
  Act; Japanese clients know the term.
- **Kaushik's 10/90 rule** (2006): of every 100 spent on analytics, 10 on tools, 90 on people who analyse. Our version:
  the client pays for the reading, not for charts.
- Training: Google's **Analytics Academy on Skillshop** and its Google Analytics certification.
