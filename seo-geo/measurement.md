# Measurement: Search Console, GA4, site moves

Status: **researched 2026-10-14** from Google Search Central and Search Console / Analytics / Looker Studio help (read
2026-10-14; most help pages show no update date). Points marked "inference" are our reading where no page says it outright.
Sources: `SOURCES.md` (section "Measurement"). How to write the report: `reporting.md`.
Sections "GA4 numbers and their names", "Search Console inside GA4, and Looker Studio" and "AI Overviews and clicks" checked 2026-10-16 (Analytics, Search Console and Looker Studio help, Search Central, Pew Research, WACA).
To re-check against the full help pages (the fetched pages were truncated): the "few dozen users" anonymisation wording,
the 1,000 / 50,000 row limits, the 30 key-event limit, the Insights branded classification.

## Search Console numbers

- Clicks, impressions, CTR (clicks ÷ impressions); average position = the **topmost** position of any link to the site (or page) in a result, averaged over the impressions it got (positions 2 and 3 → 2.5); it is not an average over a keyword list, and it changes with the view (by property or by page) (fact). A better average can also come from losing low-ranked impressions: always show it next to impressions (practice).
- Data normally 2–3 days late; newest days preliminary (fact).
- Queries used by fewer than a few dozen people over 2–3 months are anonymised: hidden from tables, counted in chart
  totals, so table rows add up to less (fact). UI export 1,000 rows; API and Looker Studio up to 50,000 rows per day (fact).
- Search Console and GA4 never match exactly (time zone, canonical URLs, click counting): compare trends, use the same
  country and device filters (fact).
- AI features: an AI Overview counts as one position shared by its links; clicks on its links count; AI Mode follow-ups are
  new queries; both are inside search type "Web", with no own filter (fact).

## GA4

- **Key events** = the important actions (formerly "conversions"; "conversion" is now the Google Ads term); up to 30 per
  standard property; do not mark page_view as a key event; new key events show within 24 h (fact).
- Landing page report: Reports → Engagement → Landing page; dimensions are session-scoped (fact).
- **Cross-domain measurement** (two of your own domains, e.g. a partner site that uses your forms): the same G- tag and web
  data stream on all pages of both domains; Admin → Data streams → Configure tag settings → Configure your domains; it adds
  `_gl` to links and form submits; without it one visitor counts as 2 users and 2 sessions; it can fail when JavaScript
  navigates instead of a click (fact).
- **Unwanted referrals:** up to 50 domains per stream (payment pages, email flows); domains in the cross-domain list are not
  referrals; do not set ignore_referrer on every page (fact).
- **Hostname data filter:** include or exclude hostnames when a property receives hits from another domain; Testing state
  first, 24–36 h, permanent for new data. Internal-traffic filter: IP rule + Exclude filter, Testing first, max 10 filters (fact).
- Data retention (2 or 14 months) limits explorations and funnels only, not standard reports (fact).
- Forms: enhanced measurement sends form_start / form_submit with form_name; one specific form = a custom event from
  form_submit filtered on form_name, marked as a key event (fact, read at summary level).
- **Do not put `utm_` on links between your own domains:** GA4 takes the session source from UTM parameters, so internal
  UTMs overwrite the visitor's real source (fact for the behaviour; no Google page states the rule outright: inference).
  To label where a lead came from, use a plain parameter (`?entry=partner`) + a hidden form field + an event parameter.
- Warning sign: many sessions that **start on a thank-you page** mean the form flow breaks the session (another domain,
  redirect, booking system): check cross-domain and unwanted-referral settings (practice).

## Moving part of a site to another domain

- Permanent redirects (301 or 308), **one-to-one** old URL → matching new URL; never many URLs to one unrelated page (soft
  404); avoid chains (≤ 3 hops ideal, < 5) (fact).
- Keep redirects **at least 1 year** (indefinitely for visitors); update own links and important external links; keep both
  Search Console properties verified; submit the new sitemap, remove the old (fact). The Change of Address page says at least
  180 days and the old domain for at least a year: the 1-year rule is the safer one.
- Expect fluctuation; a medium site takes a few weeks or more (fact).
- **Change of Address tool: whole domains only**, not path-level properties; a section moved to another domain relies on
  redirects and sitemaps (fact for the tool; the section case is inference).
- Merged pages: redirect to the page that now holds the combined content; content not kept returns 404/410 (fact).
- Practice: if the moved content was what ranked, the target page must match it in topic and depth; a correct 301 to a
  thinner or different page still loses the ranking. A 302 (temporary) keeps the old URL in Google.

## Core Web Vitals in reports

Field data (CrUX, 75th percentile, mobile and desktop separately) is authoritative; Lighthouse lab data is for debugging
and cannot measure INP (TBT instead); a Search Console CWV group takes the status of its worst metric (fact). Thresholds and
fixes: `../wp-performance.md`.

## GA4 numbers and their names (checked 2026-10-16)

- **Engaged session:** lasts longer than 10 seconds, **or** has a key event, **or** has 2+ page views. The 10 s timer can be changed per web stream (Admin → Data streams → Configure tag settings → Show all → Adjust session timeout → Adjust timer for engaged sessions); write the setting in the report's method note and do not change it mid-year (fact; method note practice).
- **Engagement rate** = engaged sessions ÷ sessions; GA4's **bounce rate** is its inverse (not-engaged sessions), not Universal Analytics' bounce rate (fact).
- **Users are browsers or devices, not people:** counted by User-ID if the site sends one, otherwise by the `_ga` cookie, plus modelling. The same person on phone and PC = 2 users; cleared cookies = a new user. Standard reports show **Active users** (fact). Label in Japanese reports: ユーザー数（概算）.
- **There is no "time on page" in GA4.** Use **average engagement time** (per active user or per session; only time the page was in the foreground) (fact).
- **精読率** is not engagement rate: in Japanese analytics it means how many page views reached the end of the page (WACA glossary). If a report needs it, use the `scroll` event (90 % depth, enhanced measurement) ÷ page views and call it 精読率（90%スクロール）; call engagement rate エンゲージメント率 as GA4's Japanese UI does (fact; formula practice).
- **Benchmarks:** GA4's own opt-in Benchmarking report first; external CTR or engagement curves (Backlinko, Advanced Web Ranking, Databox) are secondary and vary by industry, brand and intent (fact for the report; practice for the ranking).

## Search Console inside GA4, and Looker Studio (checked 2026-10-16)

- Link in GA4: Admin → Product links → **Search Console links** (GA4 Editor + verified Search Console owner; one web stream ↔ one Search Console property; a link cannot be edited, only deleted and recreated). Two reports appear in the Library and must be **published** to show in the menu: **Google organic search queries** and **Google organic search traffic** (fact).
- **Queries cannot be joined with GA4 sessions or key events.** Search Console metrics combine only with Search Console dimensions plus GA4 landing page, device and country. "Conversion rate per search query" is therefore not available from Google's data; the honest level is **per landing page**: which landing pages get search clicks and which of them produce key events (fact). Search Console data in GA4 is 48 h late and covers at most 16 months.
- **Looker Studio** is not real time: the Search Console connector refreshes every **12 hours** (fixed), the GA4 connector every 12 hours by default (1 or 4 hours selectable); "Refresh data" forces an update. PDF download and **scheduled email delivery** (PDF with a link) are built in (fact).

## AI Overviews and clicks (checked 2026-10-16)

- AI Overview and AI Mode traffic sits inside search type "Web" with no own filter (see "Search Console numbers" above). Google says clicks from AI results are "higher quality" and total organic clicks are stable, without publishing data (fact: what Google says).
- Independent research: Pew Research (US, 900 adults, March 2025): people clicked a result in **8 %** of visits when an AI summary appeared vs **15 %** without; links inside the summary got 1 % (fact for the study). Ahrefs and Seer measured lower CTR on queries with AI Overviews (secondary, observational).
- So "impressions up, clicks down, key events steady" **fits** AI Overviews but is a **hypothesis to test**: compare informational vs commercial and brand vs non-brand queries, rankings and SERP features before writing it in a report (practice).
