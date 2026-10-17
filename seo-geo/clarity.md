# Microsoft Clarity (heatmaps and session recordings)

Status: **researched 2026-10-17** from Microsoft Learn (Clarity docs), the Clarity terms of use, the Clarity blog, the WordPress plugin page, the clarity-js source, 個人情報保護委員会 Q&A and the 総務省 外部送信規律 page (`SOURCES.md`, section "Clarity"). Facts carry a source; points marked practice are our method. GA4 and Search Console: `measurement.md`; reports: `reporting.md`; law: `../legal/japan.md`.

## What it is and when we may use it

Free user-behaviour analytics from Microsoft: session recordings, heatmaps, frustration signals, Core Web Vitals per session and an AI assistant (Copilot). GA4 says **how many**; Clarity shows **why** (where people click, stop, get stuck).

**Before installing, check Microsoft's rules (fact: the under-18 rule is in the Clarity docs and FAQ; the rest in the terms of use):**
- **Not on sites aimed at people under 18.** That rules out sites for pupils (小中高 student pages, children's services); a school site aimed at parents is a grey area: **the owner decides, and in doubt we do not install**.
- **Not with sensitive material**: health care, financial services, government-related information. Clinics, hospitals, finance and public bodies: do not install.
- No user profiles; do not send sensitive data. Microsoft is an **independent controller** and may use the data for its own purposes (including advertising), under the Microsoft Privacy Statement.
- The site's privacy policy must say that Microsoft collects data via Clarity, link to the Microsoft Privacy Statement and offer opt-out where law requires (Microsoft publishes sample wording).

## Cost and limits (fact)

| Item | Value |
|---|---|
| Price | free; no traffic limit; unlimited projects (Microsoft reserves the right to add fees with notice) |
| Sampling | analytics unsampled; recordings kept up to **100,000 per project per day**, sampled above that |
| Retention | recordings **30 days** (favourited or labelled: 9 months); heatmaps and dashboards **9 months** |
| Session | ends after 30 minutes of inactivity; times in **UTC** |
| Data location | Microsoft Azure; no region choice documented |
| UI language | Japanese available (Manage account → Preferences → Language). Copilot output in Japanese is not documented: test before promising it |
| Export API | 10 calls per project per day, last 1–3 days only, 1,000 rows: not a monthly data source; use CSV and PNG downloads |

## Features worth using

- **Heatmaps:** click, scroll (with "average fold"), area, attention; per URL or page group; compare mode (before/after). Clicks are recorded per element, so they hold up on responsive layouts; download as PNG or CSV.
- **Frustration signals** (definitions from the docs): **rage click** (repeated clicks in one spot), **dead click** (no visible response), **excessive scrolling**, **quick back** (returns fast from a page), **JavaScript and click errors**.
- **Filters and segments:** device, entry/exit/visited URL (regex), referrer, UTM, channel, rage/dead clicks, scroll depth, smart events, LCP/INP/CLS, bot traffic; save as a segment per client.
- **Smart events and funnels:** auto-detected form submits, contact clicks, downloads and more; up to 20 custom events; funnels weaken without cookie consent.
- **Copilot:** summaries of the dashboard, a recording or a heatmap. Microsoft says the output "shouldn't be treated as expert recommendations" and it cannot do arithmetic: verify before quoting.

## Installing on WordPress

1. **Official plugin "Microsoft Clarity"** (wordpress.org, 200,000+ installs, updated 2026-10-01): sign in from the Clarity menu in the admin and pick or create a project. Simplest. Do not enable the plugin's extra "Brand Agents" feature without a separate decision (practice).
2. **Google Tag Manager** (official template "Microsoft Clarity – Official", trigger All pages) when the site already runs GTM and a consent tool (practice: preferred there).
3. Manual snippet in `<head>` via the child theme, never the theme file editor.
- **Check it works:** live users in the Clarity dashboard, or DevTools → Network → requests to `clarity.ms/collect` (fact).
- **Speed:** the script loads asynchronously (about 25 KB; TBT 0 ms in Microsoft's own 2021 test); measure PageSpeed before and after on each site (practice).
- **WP Rocket "Delay JavaScript execution"** delays Clarity until the first interaction, so sessions without interaction and the first seconds are lost; exclude the Clarity script from delay or note the gap in reports (practice).
- **Not captured:** third-party iframes (YouTube, Google Maps, payment forms) and canvas; staging behind Basic Auth shows unstyled recordings because Clarity cannot fetch the CSS (fact).

## Privacy, masking and consent

- **Masking modes:** Strict (all text), **Balanced (default: numbers and e-mail addresses)**, Relaxed. In every mode **typed input and drop-downs are masked** and the masked content never leaves the browser (fact).
- **Our default (practice):** Balanced, plus `data-clarity-mask="true"` on forms, confirmation screens (確認画面 show names and addresses as plain text, which Balanced does not mask), My Account, order and booking pages. Strict mode for any site with personal details on screen.
- **Cookies** (fact): first-party `_clck` (user ID, 1 year) and `_clsk` (session link, 1 day), plus Microsoft cookies (`MUID`, `CLID`, …). Without consent ("cookies off" / consent mode) every page view is a separate session.
- **EEA, UK, Switzerland:** since **2025-10-31** Clarity requires a consent signal (Google Consent Mode is honoured automatically; or `clarity('consentv2', …)`); without it, page views are not joined into sessions (fact).
- **Japan:**
  - 個人情報保護法: a cookie ID is 個人関連情報; when a site embeds Microsoft's tag and does not handle the data itself, the site is not "providing" it to Microsoft (PPC Q&A 8-10), so the 31条 consent check does not apply. **Never link Clarity IDs to real customer IDs** (`identify` with names or member numbers would make it 個人データ) (fact for the Q&A; rule practice).
  - 外部送信規律 applies only to covered services (SNS, media, malls, platforms), not to normal company or own-shop sites; a 外部送信ツール一覧 (Clarity: Microsoft Corporation, cookie ID and interaction data, purpose サイト改善) is good practice everywhere and satisfies Clarity's own terms (`../legal/japan.md`).
- Exclude the office IP (IPv4 only) so staff visits do not count.

## Monthly routine (practice, 30–45 minutes per site)

1. Dashboard, last 30 days, bots excluded: sessions, dead / rage / quick-back / excessive-scroll rates, JS errors vs last month. Do it before recordings expire (30 days).
2. Device = mobile → the top landing pages from Search Console and GA4 → scroll map and click map for each.
3. Filter rage and dead clicks → watch 5–10 recordings → label them (kept 9 months).
4. Form pages: visited the form, no submit event → watch abandonment recordings.
5. Organic Search channel for SEO pages; campaign filter for ad landing pages.
6. Save the filters as a client segment; next month use heatmap compare to show the effect of the fix.

Use the findings in the diagnosis table of `reporting.md` ("why" behind a GA4 pattern).

## Presenting it to clients

- Show **heatmap PNGs** (aggregated) and counts; crop any visible personal text.
- Do not paste recording links into PDFs (guest links are public until they expire and show city, device, referrer); describe the recording or use a blurred still.
- Clarity and GA4 numbers never match (UTC vs property time zone, bot filter, consent, blocked IPs): GA4 stays the traffic figure of record; Clarity numbers are behaviour signals (fact for the reasons).
- Do not claim a cause from one recording; give counts and one example. A dead click on a decorative image may be harmless.
- The client's privacy policy names Clarity **before** the first report that uses it.

## Alternatives (one line each)

- **Hotjar** (now Contentsquare): free plan and paid tiers; surveys and EU hosting options.
- **GA4 explorations:** funnels and paths, no heatmaps or recordings.
- **ミエルカヒートマップ, User Insight, Ptengine:** Japanese tools with Japanese support, PowerPoint export, A/B testing or Web接客; paid by page views (check current prices on the vendors' pages). Consider them when a client cannot accept Microsoft's terms (minors, health, public sector).
