# SWELL theme (Japanese block-editor theme)

Status: merged 2026-10-11 from the dashboard `swell-wp` skill and the account `swell-wp` skill. School-site specifics removed. **Not yet verified against swell-theme.com documentation (pass 2).** ⚠ **Open conflict:** the two sources name SWELL's custom blocks differently, `loos/…` (dashboard, 2026-09) versus `swell/…` (account skill). Until verified, copy block names from the site itself.

| Need | Read |
|---|---|
| Customizer panel map and how to hand over settings | `customizer.md` |

## How SWELL works

SWELL uses the **WordPress block editor**. Page content is HTML with block comments:

```
<!-- wp:heading {"level":2} -->
<h2 class="wp-block-heading">見出し</h2>
<!-- /wp:heading -->
```

SWELL adds its own blocks (full-width sections, buttons, FAQ, steps, balloons, caption boxes, cards, CTA). Colours, fonts, header, footer and layout are set in **外観 → カスタマイズ** (`customizer.md`). Customisations go in the child theme (`swell-child`).

## The one rule that prevents broken pages

**Never write a block from memory.** Block comments carry JSON attributes that must match the HTML inside exactly; a wrong attribute or a hand-made SWELL block shows "このブロックには予期しないコンテンツが含まれています" in the editor.

1. Read a page on the same site that already contains the block you need.
2. Copy that block's full markup (comment + HTML) and change only text, link or image.
3. For a block the site does not use yet: use a core block (`wp:paragraph`, `wp:heading`, `wp:list`, `wp:image`, `wp:buttons`, `wp:columns`, `wp:group`), or have a person add the SWELL block once in the editor and then copy it.

Core block skeletons (safe to write):

```
<!-- wp:paragraph --><p>本文</p><!-- /wp:paragraph -->
<!-- wp:image {"sizeSlug":"large","linkDestination":"none"} --><figure class="wp-block-image size-large"><img src="URL" alt="説明"/></figure><!-- /wp:image -->
<!-- wp:buttons --><div class="wp-block-buttons"><!-- wp:button --><div class="wp-block-button"><a class="wp-block-button__link" href="URL">ラベル</a></div><!-- /wp:button --></div><!-- /wp:buttons -->
<!-- wp:columns --><div class="wp-block-columns"><!-- wp:column --><div class="wp-block-column">左</div><!-- /wp:column --><!-- wp:column --><div class="wp-block-column">右</div><!-- /wp:column --></div><!-- /wp:columns -->
```

## Workflow

Read the page → change only the needed blocks, keep the rest byte for byte → save → clear cache → check on desktop and phone.

## Styling

- Suggest the Customizer setting before CSS (`カスタマイズ → サイト全体設定 → カラー設定 → メインカラー`).
- Use SWELL's CSS variables, not hex: `var(--color_main)`, `var(--color_accent)` ⚠, `var(--color_text)`, `var(--color_link)`, `var(--color_bg)`, `var(--color_border)` ⚠.
- Custom CSS in the child `style.css` with the site's class prefix; do not duplicate what the Customizer controls.
- Japanese typography: `font-feature-settings: "palt"`, `letter-spacing: 0.05em`, line height 1.8–1.9 for paragraphs, `line-break: strict`. **Not** `word-break: break-all` (one source recommended it; it breaks English words).

## Plugins

Works well with WPForms, Yoast SEO (or SEO SIMPLE PACK), WP Rocket, Wordfence. Known conflicts, do not recommend: Jetpack, Autoptimize, WP Fastest Cache, other page builders (one source also lists Contact Form 7 ⚠).

## Deliverables for a SWELL change

Two blocks: **Customizer settings** (listed as `カスタマイズ → パネル → セクション → 項目: 値`, done by a person) and **child code / block markup** (to paste or upload).
