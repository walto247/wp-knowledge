# CSS and the child theme on Flatsome sites

Status: merged 2026-10-11 from `flatsome-wp/css` and the WSL `child-theme` reference. Unverified against the official docs (pass 2). Design values come from the project's `DESIGN.md` (`../design/design-tokens.md`).

## Where CSS goes, in this order

1. **Theme Options first:** colours, fonts, header, buttons are set in Flatsome → Theme Options. Suggest the setting instead of overriding it with CSS.
2. **Theme Options → Advanced → Custom CSS** (the usual place for site CSS): three boxes, *All screens*, *Tablet*, *Mobile*; Flatsome wraps the last two in media queries. Stored in the `html_custom_css` option. Start each addition with a dated comment naming the change: `/* 2026-09 お問い合わせボタン */`. Change existing rules in place rather than adding overrides.
3. **Child theme `style.css`** only if the site keeps its CSS there (check first).

Never inline CSS in page content except a one-off that cannot be done otherwise.

## Writing CSS

- Target class names that really exist: read the page content and use its `class="…"` values, or add a class to the element in UX Builder (Advanced → CSS Class). No fragile selectors like `.row > .col:nth-child(3) .img`.
- Prefix new class names with the site prefix from the project (`.wpa-`, `.skyus-` …).
- Low specificity; `!important` only to beat an inline style Flatsome prints.
- Phone first: everything you add works at 375 px. Write phone styles, then `@media (min-width: 768px)` upward.
- Variables, never raw hex: `:root { --color-primary: … }` from `DESIGN.md`; rules use `var(--color-primary)`.
- Japanese text: body 16 px, line height 1.7–2.0, `line-break: strict`, no italics (`../design/japan.md`).

## Child theme skeleton

`style.css` header (keep it):
```css
/*
Theme Name:  Flatsome Child
Template:    flatsome
Version:     1.0.0
Text Domain: flatsome-child
*/
:root { /* tokens from DESIGN.md */ }
body { font-size: 16px; line-height: 1.8; }
/* components, sections, utilities, then media queries at the end */
```

`functions.php` (parent styles first, child after, versioned by file time):
```php
<?php
add_action('wp_enqueue_scripts', function () {
    wp_enqueue_style('flatsome-parent-style', get_template_directory_uri() . '/style.css');
    wp_enqueue_style('flatsome-child-style', get_stylesheet_directory_uri() . '/style.css',
        ['flatsome-parent-style'], filemtime(get_stylesheet_directory() . '/style.css'));
});
```
Add scripts in the footer, versioned the same way; pass PHP values with `wp_localize_script`. Wrap custom functions in `function_exists()` guards.

Useful Flatsome filters (⚠ verify names in pass 2): `flatsome_sidebar` (`__return_false` removes the sidebar), `flatsome_footer_copyright`, `flatsome_breadcrumbs`, `body_class` for page-specific hooks.

## Custom page templates

Landing page without header and footer: a `templates/template-lp.php` with `Template Name: Landing Page`, printing `the_content()` in a wrapper. Full-width: `get_header()`, `<div id="content" class="page-wrapper"><div class="row"><div id="main" class="large-12 col">`, the loop, `get_footer()`.

## Fonts and performance

At most two families, few weights; Japanese web fonts subset or self-hosted with `font-display: swap`; prefer the Theme Options font setting. Hero images not lazy-loaded (`skip-lazy` class). More in `../wp-performance.md`.
