# Accessibility — WCAG 2.2 AA, the basis of JIS X 8341-3

Status: merged 2026-10-11 from `global-web/accessibility` and the WSL `ux-ui/accessibility` (WCAG 2.1). Not yet verified against WCAG 2.2 and JIS X 8341-3:2016 (pass 2; links in `SOURCES.md`). Legal duty in Japan: `../legal/japan.md`.

## Check on every change

| Item | Rule |
|---|---|
| Text contrast | ≥ 4.5:1 normal text; ≥ 3:1 large text (≥ 24 px, or bold ≥ 18.5 px) |
| UI contrast | buttons, input borders, focus rings, icons ≥ 3:1 against their background |
| Colour alone | never the only signal: 必須 / `*` text for required fields, error text for errors |
| Headings | one H1; H2 → H3 in order, no skipping for looks (style with CSS) |
| Images | meaningful `alt`; decorative `alt=""`; text in an image is repeated in `alt`; complex charts described in the text |
| Links | descriptive text; not 「詳しくはこちら」 / "Read more" repeated |
| Tap targets | WCAG 2.2 minimum 24 × 24 px; aim for 44–48 px on phones, 8 px apart |
| Focus | visible on every link, button and field; never `outline: none` without a replacement |
| Forms | visible `<label>` for every field (placeholder is not a label); errors say how to fix and are linked with `aria-describedby`; `autocomplete` on personal fields |
| Motion | no autoplay with sound; sliders and animations can be paused; respect `prefers-reduced-motion` |
| Language | `lang="ja"` / `"en"` on the page; mark long passages in the other language |
| Zoom | works at 200 % zoom and 320 px wide without losing content |
| Media | captions on video with speech; transcripts for audio |
| Semantics | `header/nav/main/footer/section/article`; lists as lists; `<button>` for actions, `<a href>` for navigation; never a `div` as a control |
| Units | `rem` for font sizes so browser preferences work |

## Quick fixes

- Low-contrast grey: `#999` on white fails, `#595959` passes.
- Icon-only button: `aria-label="メニューを開く"`.
- Lost focus ring: `:focus-visible { outline: 3px solid <brand>; outline-offset: 2px; }`.
- Heading used for size only: change the tag, keep the look with a class.
- Placeholder-only form: add a label; show the required mark in text.

```html
<label for="email">メールアドレス <span aria-label="必須">*</span></label>
<input type="email" id="email" name="email" required autocomplete="email" aria-describedby="email-error">
<span id="email-error" role="alert">有効なメールアドレスを入力してください</span>
```

## What a machine cannot judge

Screen-reader flow and real keyboard use need a person. Say what was checked and what still needs a human test. Contrast checker: WebAIM (https://webaim.org/resources/contrastchecker/).
