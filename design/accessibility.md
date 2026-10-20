# Accessibility — WCAG 2.2 AA and JIS X 8341-3

Status: **verified 2026-10-11** against WCAG 2.2 "What's new" (W3C), the JIS X 8341-3:2016 checklist example for 1.4.3 (fsa.go.jp), the Digital Agency design system (DADS) colour and typography pages, and the 2026 status of the JIS revision (gihyo.jp 2026-01, issoh.co.jp). Sources with URLs: `SOURCES.md`. Legal duty in Japan: `../legal/japan.md`. Japanese typography: `japan.md`.

## Which standard

- **JIS X 8341-3:2016** has the same content as **WCAG 2.0** (DADS states this; ISO/IEC 40500:2012). It is still the standard government sites test against (declarations dated September 2026 still cite it).
- A revision to match **ISO/IEC 40500:2025, i.e. WCAG 2.2**, has been in committee since 2025-10-30; WAIC expects publication in 2027, at the latest 2028 (WAIC, 2026-09-28; 61 → 87 success criteria); no new JIS as of 2026-10-17. WCAG 3.0 is still a working draft (2026-09-10) with years to go. **Build new work to WCAG 2.2 AA** so nothing has to be redone.
- A public "JIS準拠" claim follows WAIC's 対応度表記ガイドライン (test method and wording); do not write 「準拠」 casually, say 「WCAG 2.2 AA を目標に設計」 instead.
- WCAG 2.2 was published 2023-10-05. It removed 4.1.1 Parsing.

## Check on every change (AA)

| Item | Rule | Source |
|---|---|---|
| Text contrast | ≥ 4.5:1 normal text; ≥ 3:1 large text | 1.4.3; DADS: 「テキストとその背景色とのコントラスト比は常に 4.5:1 以上」 |
| **Large text, Japanese** | non-bold **22 pt (≈ 29 px)** or more, bold **18 pt (24 px)** or more. Latin text: 18 pt (24 px) / bold 14 pt (≈ 18.5 px). Japanese needs the bigger size before 3:1 is allowed | JIS X 8341-3:2016 checklist 1.4.3: 「太字でないテキストが少なくとも18ポイント（日本語は22ポイント）以上、太字のテキストが少なくとも14ポイント（日本語は18ポイント）以上」 |
| UI contrast | buttons, input borders, focus rings, icons, dividers ≥ 3:1 against the adjacent background | 1.4.11; DADS colour |
| Colour alone | never the only signal: 必須 / `*` text for required fields, error text for errors, **links underlined** (DADS: blue/purple alone is hard to tell apart) | 1.4.1; DADS |
| Headings | one H1; H2 → H3 in order, no skipping for looks | 1.3.1 |
| Images | meaningful `alt`; decorative `alt=""`; text in an image repeated in `alt`; charts described in text | 1.1.1 |
| Links | descriptive text; not 「詳しくはこちら」 / "Read more" repeated | 2.4.4 |
| **Target size** | at least **24 × 24 CSS px** (new in 2.2, AA). Exceptions: spacing (a 24 px circle around each small target touches no other), an equivalent larger control on the page, inline links in text, browser-default size, essential. Practice on phones: 44–48 px, 8 px apart | 2.5.8 |
| Focus visible | visible on every link, button and field; never `outline: none` without a replacement | 2.4.7 |
| **Focus not obscured** | the focused element is not fully hidden by sticky headers, cookie bars, chat widgets (new in 2.2, AA) | 2.4.11 |
| **Dragging** | anything done by dragging (sliders, sortable lists, map pans) also works with single taps/clicks (new in 2.2, AA) | 2.5.7 |
| Forms | visible `<label>` for every field (placeholder is not a label); errors say how to fix, linked with `aria-describedby`; `autocomplete` on personal fields | 1.3.1, 3.3.1–3.3.3 |
| **Redundant entry** | information typed once in a process (name, address) is not asked again; auto-fill or select (new in 2.2, A) | 3.3.7 |
| **Consistent help** | contact, chat and help links sit in the same place on every page (new in 2.2, A) | 3.2.6 |
| **Accessible login** | no puzzle or memory test to log in (CAPTCHA that needs transcription, remembering a code) without an alternative; allow paste and password managers (new in 2.2, AA) | 3.3.8 |
| Motion | no autoplay with sound; sliders and animations can be paused; respect `prefers-reduced-motion` | 1.4.2, 2.2.2 |
| Language | `lang="ja"` / `"en"` on the page; mark long passages in the other language | 3.1.1, 3.1.2 |
| Zoom | works at 200 % zoom and 320 px wide without losing content | 1.4.4, 1.4.10 |
| Media | captions on video with speech; transcripts for audio | 1.2.x |
| Semantics | `header/nav/main/footer/section/article`; lists as lists; `<button>` for actions, `<a href>` for navigation; never a `div` as a control | 4.1.2 |
| Units | `rem` for font sizes so browser preferences work; body text 16 px, never under 14 px (DADS) | 1.4.4; DADS typography |

## Quick fixes

- Low-contrast grey: `#999` on white fails, `#595959` passes.
- Icon-only button: `aria-label="メニューを開く"`.
- Lost focus ring: `:focus-visible { outline: 3px solid <brand>; outline-offset: 2px; }`. DADS uses a two-layer yellow-on-black ring for government sites; a brand colour with 3:1 contrast is fine elsewhere.
- Heading used for size only: change the tag, keep the look with a class.
- Placeholder-only form: add a label; show the required mark in text.
- Small icon buttons in a toolbar: either 24 px boxes or 24 px spacing between them.
- Sticky header hides the focused field: `scroll-margin-top` on focusable elements, or a shorter header.

```html
<label for="email">メールアドレス <span aria-label="必須">*</span></label>
<input type="email" id="email" name="email" required autocomplete="email" aria-describedby="email-error">
<span id="email-error" role="alert">有効なメールアドレスを入力してください</span>
```

## What a machine cannot judge

Screen-reader flow and real keyboard use need a person. Say what was checked and what still needs a human test. Contrast checker: WebAIM (https://webaim.org/resources/contrastchecker/).
