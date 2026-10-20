# SWELL theme (Japanese block-editor theme)

Status: **verified 2026-10-11** against swell-theme.com (home page: current version **2.19, released 2026-08-20**; 機能一覧 `/function/75/`; 推奨・非推奨プラグイン `/basic-setting/4688/`; 更新情報 `/category/update/`) and the public front end of a live SWELL 2.19.0 site (CSS variable names, block class names, child theme in use). Block slugs are editor-only and not visible on public pages: `loos/…` is what real page content showed when read in 2026-09; the `swell/…` names from the older account skill were wrong and are dropped. Always copy a block from the site anyway.

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

SWELL's own blocks (official list, 2026-10): キャプション付きブロック, 関連記事ブロック (blog card), ふきだしブロック, SWELLボタンブロック, FAQブロック, アコーディオンブロック, ステップブロック (timeline), バナーリンクブロック, 説明リストブロック (`dl`), ABテストブロック, 投稿リストブロック, フルワイドブロック, 広告タグブロック, ブログパーツブロック. Rendered class names start with `swell-block-` (`swell-block-full`, `swell-block-columns`, `swell-block-button`, `swell-block-banner`, `swell-block-tab` seen live). SWELL also extends core blocks (box styles on paragraph and group, list styles, table and column options, device-specific display, five bottom-margin steps) and adds toolbar shortcodes (PC/SP-only line break, icons, star rating, login-only content, in-article ad). Colours, fonts, header, footer and layout are set in **外観 → カスタマイズ** (`customizer.md`). Customisations go in the official child theme **`swell_child`** (downloaded from the SWELL purchase page; it already enqueues the parent CSS).

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
- Use SWELL's CSS variables, not hex (names verified on a live 2.19 site): `--color_main`, `--color_main_thin`, `--color_main_dark`, `--color_deep`, `--color_pale`, `--color_text`, `--color_link`, `--color_bg`, `--color_border`, `--color_gray`, `--color_header_text`, `--color_gradient`, marker colours `--color_mark_yellow|orange|green|blue`, list icon colours `--color_list_check|good|bad|num|triangle`. There is **no `--color_accent`**; the Customizer's アクセントカラー maps to `--color_deep` / `--color_pale` shades of the main colour.
- Custom CSS in the child `style.css` with the site's class prefix; do not duplicate what the Customizer controls.
- Japanese typography follows `../design/japan.md` (verified values): body 16 px, line height 1.7–1.75, letter spacing 0.02 em, `line-break: strict`, `palt` on headings only. SWELL's フォント設定 (ベースサイズ / 行間) sets these; CSS only for what the Customizer lacks. **Not** `word-break: break-all` (one source recommended it; it breaks English words).

## Plugins (official list, swell-theme.com 2026-10)

- **Needed:** an SEO plugin, because SWELL prints no meta/OGP tags itself. Official: **SEO SIMPLE PACK** (same developer). Yoast SEO works too; never both.
- **Recommended by the developer:** Highlighting Code Block, Useful Blocks, Pochipp (affiliate links), XML Sitemap & Google News (then untick SWELL's own sitemap option), WP Revisions Control, CloudSecure WP Security, WPvivid (backup), **Contact Form by WPForms**.
- **Not recommended:** the Gutenberg plugin, WooCommerce and other EC plugins (not supported), Elementor and other page builders, Flying Scripts (duplicates SWELL's deferred JS; iOS first-tap bug), Autoptimize, Async JavaScript, Table of Contents Plus / RTOC / Lazy Load / speech-bubble plugins (built into SWELL).
- **Unnecessary:** Classic Editor, AddQuicktag, TinyMCE Advanced (can disable SWELL features).
- **Only with a reason:** Jetpack (heavy, overlaps), WP Super Cache / W3 Total Cache (SWELL has its own cache; stale-CSS problems). **WP Rocket is not on the official list either way**; our sites use it, so test after every SWELL update and clear both caches.
- **Reported conflicts:** SiteGuard WP Plugin (login lockouts), EWWW Image Optimizer (upload failures; enable only while compressing). Contact Form 7 is *not* listed as incompatible (the older account skill was wrong).

## Versions

2.19 (2026-08-20, WordPress 7.1 UI), 2.18 (2026-08-09), 2.17 (2026-05-21, WordPress 7.0), 2.16 (2025-12-03), 2.15, 2.14 (2025-04, WordPress 6.8). Updates arrive through the dashboard with an activated licence; after an update that breaks the editor, SWELL設定 → リセット (cache clear) first.

## Deliverables for a SWELL change

Two blocks: **Customizer settings** (listed as `カスタマイズ → パネル → セクション → 項目: 値`, done by a person) and **child code / block markup** (to paste or upload).
