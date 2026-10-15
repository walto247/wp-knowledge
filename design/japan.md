# Japanese web design and UX

Status: typography and accessibility sections **verified 2026-10-11** against the Digital Agency design system (DADS) typography and colour pages, JLReq (W3C 日本語組版処理の要件) and the JIS X 8341-3:2016 contrast checklist (URLs in `SOURCES.md`). "Screen sizes in Japan" researched 2026-10-15 (StatCounter Japan, DADS レイアウト, agency articles); "Brand and premium typography" checked 2026-10-15 (DADS typography and 余白, JLReq, WCAG 2.2, MDN/caniuse). The UX, forms, audience and seasons sections are merged practice (2026-09 skills), not from a standard. Builds on `general.md`; this file wins for Japanese sites. Writing rules: `../writing/japanese.md`. Law: `../legal/japan.md`. Accessibility checklist: `accessibility.md`.

## What Japanese visitors expect

- **More information on one page** than Western minimal designs: details, prices, schedules, FAQs, access maps. Order it with clear headings, tabs or accordions; do not hide it. A hero-plus-CTA-only page feels empty.
- **Trust before selling:** 会社概要 (name, address, representative, founded, capital), 実績 with the year, 導入企業ロゴ, 資格・認定, 代表挨拶, real staff photos with names, media coverage. Phone number visible in the header with 受付時間.
- **Footer, always:** 会社概要, プライバシーポリシー, and for shops 特定商取引法に基づく表記; 利用規約 where a service is used online.
- **Breadcrumbs** on every inner page; site search on large sites; **お知らせ / News** on the top page for schools, clinics and local businesses.
- **Contact choices:** phone (tap-to-call), form, and **LINE** where the audience uses it. Many people prefer 資料請求 (brochure request) before a consultation. QR codes bridge print to web.

## Navigation

- Japanese labels (English only for brand words). 5–7 main items; drop-downs are expected on large sites.
- Phones: hamburger menu plus a **fixed bottom bar** with the 1–3 key actions (電話・資料請求・LINE).
- Hover-only menus fail on touch; sub-menus must open on tap.
- School sites usually need: トップ, 学校について, コース, キャンパス, 入学案内, よくある質問, お知らせ, お問い合わせ, アクセス.

## Typography

| Item | Value | Source |
|---|---|---|
| Body and UI text | **16 CSS px or more**. 14 px only where space forces it (footer notes); **under 14 px is not acceptable** | DADS: 「本文とUIの基準値は 16 CSS px 以上」「14 CSS px 未満は原則として許容されません」 |
| Line height, body | **1.7–1.75** for reading text (DADS body tokens are 170 % and 175 %); 1.5 is the floor; up to 2.0 on dense pages | DADS: 「少なくとも1.5倍」; JLReq: line gap ½–1 em of the character size, 1 em for lines over about 35 characters |
| Line height, headings | **1.4** (DADS heading and display tokens 140 %); 1.3–1.5 acceptable | DADS |
| Letter spacing | **0.02 em** for 16–26 px text, 0.01 em for 28–36 px, **0** for 45 px and larger and for display sizes | DADS (2 % / 1 % / 0) |
| Line length | up to about **40 characters** per line in horizontal text; use columns or a narrower measure beyond that. Article body: `max-width: 41em` (40 characters + 0.02 em spacing ≈ 656 px at 16 px); 45 characters (≈ 734 px) is the outer limit | JLReq §2.4.2 (a maximum, not a range; print figure that applies well to screens) |
| Paragraph gap | 1–1.5 em | practice |
| Size scale | 16–45 px for headings and body; 48–64 px only for display elements that need visual impact | DADS |
| Headings | `clamp()` sizes within that scale, e.g. H1 `clamp(1.75rem, 4vw, 2.8rem)`; break at phrase boundaries, never one lone character on the last line | DADS + practice |
| Ruby (ふりがな) | **half the size** of the base text, above it in horizontal writing; browsers default to 50 % | JLReq, DADS |

```css
.prefix-content p {
  line-height: 1.75;
  letter-spacing: 0.02em;
  line-break: strict;            /* 禁則処理, see below */
  overflow-wrap: anywhere;       /* long URLs on phones */
}
.prefix-content h2 { line-height: 1.4; letter-spacing: 0.01em; font-feature-settings: "palt"; }
```

禁則処理 (line-breaking rules, JLReq): closing brackets and 句読点 (、。) never start a line (行頭禁則); opening brackets never end a line (行末禁則). The strict rule also keeps 長音「ー」, 小書き仮名 (ゃゅょっ) and 々 off the line start; many books allow those three. `line-break: strict` applies the strict set; `line-break: normal` the relaxed one. Browsers handle brackets and punctuation in both modes. Hanging punctuation (ぶら下げ) is optional: `hanging-punctuation: allow-end`.

Latin and numbers inside Japanese (JLReq): use half-width proportional Latin and digits in horizontal text, never full-width monospace Latin; keep units and symbols with their number (¥1,000, 10 %, 5 km do not break). A thin space between Japanese and Latin is a typesetting convention (about ¼ em after unit symbols); on the web leave it to the browser or use a normal space consistently; do not hand-insert full-width spaces.

Fonts:
- **Noto Sans JP** is the reference Japanese web font (DADS uses it; SIL Open Font License, free to self-host); weights 400 and 700 are enough. System stack when no web font: `"Hiragino Sans", "Hiragino Kaku Gothic ProN", "Yu Gothic Medium", "Noto Sans JP", Meiryo, sans-serif`; serif for premium: `"Hiragino Mincho ProN", "Yu Mincho", "Noto Serif JP", serif`.
- Japanese web fonts are several MB: subset or self-host, `font-display: swap`, at most 2 families and few weights.
- **No italics** for Japanese: fonts have none, browsers synthesise an oblique that reads badly (DADS). **Do not use `word-break: break-all`** on body text (it splits English words); use `line-break` + `overflow-wrap`.
- Furigana with `<ruby>漢字<rt>かんじ</rt></ruby>`: all kanji for 小学生 pages, hard kanji and names on first use elsewhere. Ruby at 50 % of the base size; keep the line height constant where ruby appears rather than opening gaps (JLReq).
- Links underlined, not colour alone; visited links in a distinguishable purple (DADS).
- Vertical text (`writing-mode: vertical-rl`) only decoratively; horizontal is the norm for official and business documents (JLReq).
- Full-width and half-width used consistently: 全角 for kana and 「、。」「」（）, 半角 for digits and Latin.

### Brand and "premium" typography (checked 2026-10-15)

Checked against DADS, JLReq, WCAG 2.2, MDN and caniuse (`SOURCES.md`, section "Typography 2"). The table above still sets the values; this adds what a brand or editorial site may do on top.

- **Japanese and English need opposite treatment.** Japanese characters each sit in a square frame (仮想ボディ, JLReq) with no ascenders or descenders, so they look larger and denser than Latin at the same px (practice: no source gives a number). English display type can be tracked tighter; Japanese headings are not (DADS: less spacing as size grows, 0 from 45 px).
- **Letter spacing beyond DADS** is a brand choice, not a rule: up to **0.05 em** for short display lines and eyebrow labels. Not on body text. Articles that prescribe 0.04–0.08 em body or 0.1 em+ "luxury" spacing have no standard behind them; Japanese practice articles put body text at about 0.05 em at most.
- **Line height:** 1.7–1.75 as the default, up to 2.0 on dense or long-line pages (table above). "1.8–1.9 is the sweet spot" and "kanji lines collide below 1.7" are not supported: DADS allows 1.5–1.75, and JLReq's usual range ends at a 1 em gap (line height 2.0), used for long lines.
- **Weights:** 400 and 700 (DADS). Noto Sans JP is variable (100–900), so **500** for sub-headings is a fine brand option, but Meiryo has only 400/700 (the browser fakes 500/600) and Yu Gothic has Medium (500) but no 600. Avoid 800–900 on kanji text.
- **Captions and notes stay at 14 px or more.** 12–13 px captions break the DADS floor.
- **Gothic or Mincho (practice).** Gothic (ゴシック) reads best on screens and is the default for body text. Mincho (明朝) reads as refined, traditional, editorial; Mincho headings with Gothic body is a valid brand pattern. Never mix both inside one heading.
- **Latin inside Japanese (欧文・和文混植):** put a Latin web font **first** in `font-family` (browsers pick a font per character), the Japanese font after it. Limit the Latin `@font-face` with `unicode-range`, and match size and baseline with `size-adjust` and `ascent-override` / `descent-override`; Latin often needs about 105–110 % to sit well next to Japanese (test). Spacing between Japanese and Latin: Chrome 140+ and Safari 18.4+ insert it automatically (`text-autospace: normal` is their default; `no-autospace` turns it off); do not type spaces, other browsers simply show none.
- **Punctuation tightening (約物詰め):** `font-feature-settings: "palt"` on headings only; body text stays ベタ組み (JLReq base setting). Meiryo has no `palt` table. Chrome/Edge 123+ already trim full-width bracket space by default (`text-spacing-trim: normal`); set `space-all` to keep the full-width spacing. Other browsers ignore the property.
- **Phrase wrapping for headings:** `word-break: auto-phrase` on `lang="ja"` breaks between phrases (Chrome/Edge 119+ only); add `text-wrap: balance` (all current browsers) so short headings still split evenly elsewhere. Use the BudouX script only where a clean break on Safari/Firefox really matters. A manual `<br>` breaks on other widths.
- **Alignment:** body text **left-aligned** on the web. Justified (両端揃え) is the print default (JLReq), but WCAG 1.4.8 (AAA) says not justified, lines with Latin words justify unevenly in browsers, and `text-justify: inter-character` is missing in Safari. Justify only short blocks of pure Japanese, never on phones or headings.
- **English eyebrow + Japanese heading** (`ABOUT US` over 私たちについて): the Japanese text is the heading (`<h2>`); the eyebrow is a `<span lang="en">` or `<p>`, never its own heading tag. If it only repeats the heading, hide it from screen readers (`aria-hidden="true"`). Keep it 8 px from the heading so they read as one unit (DADS spacing: closer = related).

## Forms

- Fields: お名前（姓・名）, フリガナ, メールアドレス（確認）, 電話番号, 郵便番号 → 住所 auto-fill, お問い合わせ内容.
- Mark **必須 / 任意** on every field in text, not colour alone. Show examples (「例：山田 太郎」).
- Accept full-width digits (「０９０」) and normalise; never reject them.
- Privacy policy link and consent checkbox before submit (legally expected). Confirmation screen is common; a clear thank-you with what happens next (「2営業日以内にご連絡します」).
- Error text in Japanese, next to the field. Short forms convert; every extra field loses people.

## Mobile

- Most traffic is on phones. Tap targets: WCAG 2.2 requires at least 24 × 24 CSS px (AA); our practice is 44–48 px with 8 px between them, and 24 px spacing around any smaller icon control (`accessibility.md`).
- Full-width inputs and buttons; no hover-only interactions; LINE share or 友だち追加 where relevant.

## Screen sizes in Japan

Researched 2026-10-15 (StatCounter Japan, September 2026; DADS レイアウト; agency articles listed in `SOURCES.md`). Our defaults are in `general.md` ("Screen sizes"); this section adds what is different in Japan.

- **iPhone country.** iOS 60.5 %, Android about 39 % of phone traffic. Top phone widths: **414** (23 %, iPhone XR/11 class), **390** (14 %), **375** (9 %, SE and older), 393 (5 %), 412 (4 %). Add **375 and 414** to the phone test widths for Japanese sites.
- **Office PCs.** Desktop: 1920 × 1080 28 %, **1536 × 864 9 %** (a 1920 screen at 125 %), 2560 × 1440 7 %, 1366 × 768 5 %, 1280 × 720 4 %. 1366 is a small group now; the 1280–1536 range of scaled Windows laptops is what the content width must survive. A 1120 container leaves 80 px each side at 1280.
- **Agency practice** (not a standard; LIG, KKI DESIGN, issoh): artboards labelled **PC** and **SP**; SP at 375 (often drawn at 750 = 2×) or 390; PC at 1366, 1440 or 1920; tablet not designed; switch at **767 / 768**; inner container 1000–1200 (real sites 1032–1280). DADS uses the same single 768 breakpoint.
- **Reading column.** Body text at most about 40 characters per line (JLReq): `max-width: 41em` at 16 px ≈ 656 px. Columns of 720–840 px give 44–52 characters at 16 px: too wide. A 2016 LIG survey of ten Japanese media sites found 670 px the most common column.
- **Text baked into banners** is still common in Japan. Avoid it (`general.md`); when a client insists, export at 2× the slot and repeat the text in the page or the `alt`.

## Colour

Blue = trust (companies, schools, finance); green = safety, health, nature; red = energy and urgency (one CTA, never body text); pink/pastel = friendly, family, care; gold = awards and premium; white space = clean. Always check contrast (`accessibility.md`).

## Audiences

- **保護者 (parents):** safety and credibility, clear costs (学費・入学金・その他費用, no hidden costs), results with the year (進路実績), support (相談体制, response speed), other parents' voices. Tone polite and specific; acknowledge worries before explaining. Trust block: real staff with names and titles, 校長メッセージ, accreditation, dated statistics, easy contact.
- **Students:** 小学生 = ふりがな on all kanji, 18 px+, short sentences, illustrations; 中学生 = ふりがな on hard kanji, peer voice, real student life; 高校生 = aspirational, photo-led, future paths. They ask: will I fit in, is it fun, can I succeed, what comes after.
- **Both on one page:** shared hero, then 「生徒のみなさんへ」 and 「保護者の方へ」 sections, voices from both, one shared CTA (資料請求・個別相談).
- **不登校・通信制:** warm, non-judgemental (「自分のペースで」「あなたらしく」), never blaming words; show flexible options and real support people. Group harmony usually sells (「みんなで」「仲間と」); for these students the message flips to individuality.
- **B2B:** 実績, 料金の目安, 導入の流れ, サポート体制, security. 敬語, concise; 資料ダウンロード and 無料相談 as low-commitment steps.
- **Older visitors:** larger text, high contrast, phone number prominent, simple menus. PDF versions of important documents are often expected.

## Seasons that move traffic

1–3月 受験・進学・新生活 (3月 graduation) · 4月 new school and business year, peak for schools and B2B · 7–8月 summer campaigns, open campuses · 9月 transfers · 12月 year-end notices. Holidays: Golden Week (late April–early May), お盆 (mid-August), 年末年始. Post business-hours notices before each.

## What changed in pass 2 (2026-10-11)

- Typography table rebuilt on DADS values: 16 px floor (14 px exceptional, below 14 not allowed), line height 1.7–1.75 body / 1.4 headings, letter spacing 0.02 em → 0, size scale 16–45 px, display 48–64 px, ruby 50 %, no italics, underlined links. Old ranges (12 px floor, 0.08 em, line height 2.0 as normal) dropped.
- 禁則処理 spelled out from JLReq (what may not start or end a line, strict vs normal), Latin-in-Japanese rules, line length ≈ 40 characters, line gap ½–1 em.
- Tap target minimum tied to WCAG 2.2 (24 px) with our 44–48 px practice kept as practice.
- Not verified by a standard (kept as practice): information density, trust blocks, navigation, forms, colour meanings, audiences, seasons. Verify against DADS components (forms, navigation) in a later pass if needed.
