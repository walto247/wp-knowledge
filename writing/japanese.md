# Japanese copywriting

Status: merged 2026-10-11 from `japan-web/copy-jp` and the WSL `content-jp` skill. Lengths are guidance; verify SEO lengths in pass 2 (`../seo-geo/`). Law for claims: `../legal/japan.md`. Design and audiences: `../design/japan.md`.

## Always

- Natural Japanese written for the reader, never machine-translated wording. One politeness level per page (usually 丁寧語 です・ます); never mix with だ・である in body text.
- Know the audience and the target keyphrase before writing. Read the project's `CLAUDE.md` / `DESIGN.md` (brand voice, forbidden words).
- Trust before selling; soft, benefit-first CTAs; specific dated numbers (「2025年度 進路決定率95%」) with the source if not ours.

## Tone by audience

| Audience | Style | Endings |
|---|---|---|
| General consumers | 丁寧語 | 〜です／〜ます |
| Parents / guardians | 丁寧語, warm, reassuring | 〜いたします／〜ください |
| Children (小学生) | やさしい言葉 + ふりがな | 〜だよ／〜です |
| Students (中高生) | 親しみのある丁寧語 | 〜ですよ／〜しよう |
| B2B / corporate | 敬語 (尊敬語・謙譲語) | 〜いたします／〜でございます (sparingly) |

## Structure

- The first 1–2 sentences answer the page's main question (readers, Google and AI answers all want this):
  ✅「通信制高校とは、毎日通学せずに自分のペースで学べる高校です。」
  ❌「このページでは通信制高校について説明します。」
- Headings as the reader's question or benefit: 「学費はいくらかかりますか？」「3つの特長」.
- Short paragraphs (2–4 sentences), one idea each. Lists for 3+ parallel points. Transitions between sections.
- End a section with the next step, not a hard sell.

## CTAs

✅ まずは無料資料請求 · お気軽にご相談ください · 詳しく見る · 無料体験に申し込む · LINEで相談する
❌ 今すぐ買え！ · Click here · 限定！急げ！ (pushy, or English inside Japanese copy)

Button text says the action (資料請求する); the line above says the benefit (1分で完了・無料).

## Lengths (guidance, not rules)

| Item | Length |
|---|---|
| Hero headline (H1) | 15–25字 |
| Section lead | 50–150字 |
| Service page body | 800–1,500字 |
| Blog article | 1,500–4,000字 depending on the topic (competitive keywords need more), never a target in itself |
| FAQ answer | 60–200字 |
| SEO title / meta description | `../seo-geo/README.md` |

## Style details

- 全角: カタカナ, 句読点「、。」, 括弧「」（）. 半角: 英数字 (2025年, 10%, SEO).
- Avoid 〜的な, 〜という形, double negatives, long noun chains. Prefer verbs.
- 漢字 : ひらがな ≈ 3 : 7 reads easiest; 〜する時→〜するとき, 〜の事→〜のこと, 出来る→できる.
- Numbers: 「約3割」 for general readers; exact figures with the year for claims.
- Company names, products, people: check spelling and 様/さん usage on the site.

## Check before finishing any Japanese text

- [ ] Reads naturally aloud; no literal translation; consistent です・ます
- [ ] Numbers specific and dated, with source if not ours
- [ ] No claim that breaks `../legal/japan.md` (No.1, 最高, 絶対, 治る, hidden conditions)
- [ ] Full-width / half-width consistent; no mixed punctuation (、。 vs , .)
- [ ] Headings say what the section answers; the CTA says what happens next

## Reports

Client and internal reports (SEO, analytics): `../seo-geo/reporting.md` (structure, 公用文作成の考え方 and やさしい日本語 rules, talk script).
