# Japanese web design and UX

Status: merged 2026-10-11 from `japan-web` (ux-patterns, typography, audience) and the WSL `japanese-web` skill. Not yet verified against JIS X 8341-3, DADS and JLReq (pass 2; links in `SOURCES.md`). Builds on `general.md`; this file wins for Japanese sites. Writing rules: `../writing/japanese.md`. Law: `../legal/japan.md`.

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

| Item | Value |
|---|---|
| Body | 16 px (15 px minimum on dense pages); nothing under 12 px anywhere; captions 14 px |
| Line height, body | 1.7–2.0 (1.5 is too tight for Japanese) |
| Line height, headings | 1.3–1.5 |
| Letter spacing | 0.02–0.08 em body; headings may use more |
| Line length | about 25–40 characters on desktop |
| Paragraph gap | 1–1.5 em |
| Headings | `clamp()` sizes, e.g. H1 `clamp(1.5rem, 4vw, 2.5rem)`; break at phrase boundaries, never one lone character on the last line |

```css
.prefix-content p {
  line-height: 1.85;
  letter-spacing: 0.04em;
  line-break: strict;            /* 禁則処理 */
  overflow-wrap: anywhere;       /* long URLs on phones */
  font-feature-settings: "palt"; /* proportional kana: good for headings, test for body */
}
```

Fonts:
- Prefer the theme's font setting or system fonts: `"Hiragino Sans", "Hiragino Kaku Gothic ProN", "Yu Gothic Medium", "Noto Sans JP", Meiryo, sans-serif`; serif for premium: `"Hiragino Mincho ProN", "Yu Mincho", "Noto Serif JP", serif`.
- Japanese web fonts are several MB: subset or self-host, `font-display: swap`, at most 2 families and few weights.
- **No italics** for Japanese (browsers fake them). **Do not use `word-break: break-all`** on body text (it splits English words); use `line-break: strict` + `overflow-wrap`.
- Furigana with `<ruby>漢字<rt>かんじ</rt></ruby>`: all kanji for 小学生 pages, hard kanji and names on first use elsewhere.
- Vertical text (`writing-mode: vertical-rl`) only decoratively.
- Full-width and half-width used consistently: 全角 for kana and 「、。」「」（）, 半角 for digits and Latin.

## Forms

- Fields: お名前（姓・名）, フリガナ, メールアドレス（確認）, 電話番号, 郵便番号 → 住所 auto-fill, お問い合わせ内容.
- Mark **必須 / 任意** on every field in text, not colour alone. Show examples (「例：山田 太郎」).
- Accept full-width digits (「０９０」) and normalise; never reject them.
- Privacy policy link and consent checkbox before submit (legally expected). Confirmation screen is common; a clear thank-you with what happens next (「2営業日以内にご連絡します」).
- Error text in Japanese, next to the field. Short forms convert; every extra field loses people.

## Mobile

- Most traffic is on phones. Tap targets at least 44 px (48 px preferred), 8 px between them.
- Full-width inputs and buttons; no hover-only interactions; LINE share or 友だち追加 where relevant.

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
