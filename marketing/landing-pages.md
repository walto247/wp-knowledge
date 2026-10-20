# Landing pages (LP / ランディングページ), global and Japanese

Status: **checked 2026-10-16** against NN/g, Unbounce, HubSpot, Baymard, Google and Meta ad policies, LINE広告 review guidelines, 総務省 data and 消費者庁 / 厚労省 guidance (`SOURCES.md` in this folder). Layout and copy patterns are **practice**; numbers marked fact have a source; law points are summarised in `../legal/japan.md` (a checklist, not legal advice). Page design basics: `../design/general.md`, Japanese conventions: `../design/japan.md`, writing: `../writing/japanese.md`.

## What an LP is

One page, one action (buy, book, request a brochure), usually reached from an ad or a campaign link. A normal site is for exploring; an LP is a salesperson that walks one visitor through one decision. Western LPs tend to be short and outcome-first; Japanese LPs tend to be long and reassurance-first (empathy, proof, risk removal). A minimal Western LP can feel thin to Japanese buyers; a dense Japanese LP can feel heavy to Western ones (practice).

## Core rules

| Rule | Default | Evidence |
|---|---|---|
| **One goal, no exits** | No header menu; logo + CTA (or phone) at the top. In-page anchor links (特徴・料金・よくある質問) are fine. Footer keeps only 会社概要, プライバシーポリシー and, when selling, 特定商取引法に基づく表記, as trust and legal links. | Unbounce: attention ratio 1:1. HubSpot test on 5 LPs: removing menu and footer links gave +0–4 % on early-stage offers, +16–28 % on mid-funnel offers. There is no "−X % per link" figure. |
| **First view** | Who it is for + the main benefit + one proof + the CTA, all on the first screen of a phone. Japanese LPs often add a キャッチコピー and proof badges (導入社数, 満足度) — only when the claim is substantiated (see "Law"). | NN/g 2018: 57 % of viewing time above the fold, 74 % in the first two screens; keep the main CTA above the fold. No source for "70–80 % leave in 3 seconds". |
| **Phone first** | Build for 375–430 px first. B2C ad LPs: a single centred column (Japanese スマホ特化型LP, about 375–550 px wide on PC with brand colour or images at the sides) is accepted practice. B2B LPs: the normal responsive layout (container 1120 px, `../design/general.md`). | 総務省 2024: 80.5 % of individuals own a smartphone; METI 2022: 56 % of goods B2C-EC on smartphones. No published "85 % of LP traffic" figure; check the client's own GA4. |
| **Speed** | The LP must load fast on a phone; the form on the page itself avoids a second load. | Google 2016: 53 % of mobile visits abandoned when a page takes more than 3 s (old but still cited by Google). No source for "2 s form page = −30 %". |

## Story order

- **新PASONAの法則** (神田昌典, 『稼ぐ言葉の法則』, 2016): **P**roblem → **A**ffinity (共感) → **S**olution → **O**ffer → **N**arrowing down (絞り込み: who it is for, why now) → **A**ction. Updated from his 1999 PASONA (Agitation instead of Affinity). Widely used for Japanese direct-response copy; a framework, not a standard.
- **AIDA** (Attention, Interest, Desire, Action; attributed to E. St. Elmo Lewis, c. 1898) and **PAS** (Problem, Agitate, Solve) for shorter Western pages.

### Ten-block wireframe (practice)

| # | Block | What goes in |
|---|---|---|
| 1 | First view | top bar (logo; phone or CTA), who it is for, headline with a concrete result, up to 3 proof points, CTA with a short reassurance line |
| 2 | Problem (P) | 「こんなお悩みありませんか？」 with 3–5 concrete worries; a muted background |
| 3 | Why it has not been solved (A) | empathy and the cause; then the turn to the solution |
| 4 | Solution: 3 reasons (S) | 選ばれる3つの理由: three pillars, each a benefit, not a feature list |
| 5 | Comparison | a table against alternatives **only with objective, substantiated criteria** (see "Law"); ◎○△× is the familiar Japanese notation, with a legend |
| 6 | Proof | real customer cases with name/company (with permission), the situation before and after, and how typical the result is; client logos with permission |
| 7 | Offer (O) | price or plans (one marked おすすめ), what is included, the free first step |
| 8 | Narrowing (N) | who it is for, and a reason to act now **only if true** (real capacity limit, real end date) |
| 9 | Risk removal | ご利用の流れ in 3–4 steps (what happens after sending), FAQ with the hard questions (営業電話は？料金は後から増える？) answered truthfully |
| 10 | Action (A) | the main benefit again and the form on the page |

## CTA, form and layout

- **CTA colour:** one colour used only for CTAs, nothing else on the page (isolation / von Restorff effect: what differs is noticed); contrast 3:1 against the background and 4.5:1 for its text (`../design/accessibility.md`).
- **Label:** the action and its value (「無料で資料をダウンロード」, "Get the price guide"), not 「送信」 or "Submit". A short reassurance line above the button (「＼ 60秒で入力完了 ／」「しつこい営業はしません」) is common Japanese practice; it must be true. No data supports a fixed uplift.
- **Repeat the CTA** after the reasons, after the proof and at the end; on phones a bottom bar (about 56 px, safe-area padding) that appears after the first view (`../design/general.md`).
- **Form on the page** (フォーム一体型LP) at the end, reached by every CTA. Ask only what the next step needs (4–6 fields as a target, practice; Baymard's checkout research shows most forms ask more than they need); ※必須 / ※任意 on every field; no email re-type; privacy-policy link and a consent checkbox (or 「プライバシーポリシーに同意のうえ送信」) before the submit button; HTTPS (`../design/japan.md`, Forms).
- **Rhythm:** alternate section backgrounds (white, light grey, a muted problem block, a brand-tint offer block) so a long page does not blur; a ▼ between problem and solution guides the eye (practice).
- **Numbers over adjectives:** 「3営業日以内に返信」 instead of 「迅速対応」; set key numbers larger than the text around them. **Every number is a claim** under 景品表示法: keep its source. For effect or performance claims 消費者庁 can demand the basis, to be submitted within 15 days (不実証広告規制).

## Law and ad platforms (Japan)

Details and sources: `../legal/japan.md`. On every LP check:
- **No.1, 満足度, 導入社数 badges:** a valid survey (fair comparison set, real users chosen fairly, fair method, claim = result) **and** a legible note with 調査機関・時期・対象・方法 next to the badge. A small ※ footnote does not make an invalid survey legal; 「検索上位○社」 or image-survey notes are named by 消費者庁 as insufficient.
- **Comparison tables:** allowed when the content is objectively proven, quoted accurately and compared fairly (消費者庁 比較広告ガイドライン). Subjective ◎○△× ratings or a hand-picked set of rivals are a 優良誤認 risk.
- **Testimonials and results:** 「個人の感想です」 does not neutralise an effect claim; state how many people and how typical the result is. Solicited or rewarded reviews are labelled 広告 / PR (ステマ規制). Clinics: no treatment testimonials; before/after photos only with treatment, cost, risks and side effects (医療広告等ガイドライン). Cosmetics and supplements: no cure or permanent-change claims (薬機法).
- **Prices and urgency:** a crossed-out "normal price" must have been charged recently (rule of thumb: more than half of the last 8 weeks); 「期間限定」「月5社様限定」 must be real and not rolled over — 消費者庁 issued 措置命令 in 2025 for "limited" campaigns that were extended or kept giving the same deal (パソコン工房 March, 創建 September).
- **Ad platforms:** Google Ads and Meta do not require specific footer links, but hiding who you are, misleading claims or unclear pricing break their misrepresentation rules; Google's lead-form assets and Meta's Instant Forms (forms inside the ad) require a privacy-policy URL; LINE広告 requires the advertiser name on the LP to match the account's 広告主正式名 and rejects LPs that collect personal data without a privacy policy. 特商法 表記 is required when the LP sells (通信販売), not for a pure inquiry LP. Keep the three footer links anyway: they cost nothing and build trust.
