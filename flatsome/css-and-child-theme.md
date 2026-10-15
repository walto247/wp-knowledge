# CSS and the child theme on Flatsome sites

Status: **verified 2026-10-11** for the custom CSS location (docs.uxthemes.com article 235: "Advanced > Custom CSS"), the breakpoints (live site) and the hook names (docs.uxthemes.com/article/385-hooks, 67 actions and 67 filters). Child-theme skeleton is standard WordPress practice. Design values come from the project's `DESIGN.md` (`../design/design-tokens.md`).

## Where CSS goes, in this order

1. **Theme Options first:** colours, fonts, header, buttons are set in Flatsome → Theme Options. Suggest the setting instead of overriding it with CSS.
2. **Flatsome → Advanced → Custom CSS** (the usual place for site CSS): three boxes, *All screens*, *Tablet* (`max-width: 849px`), *Mobile* (`max-width: 549px`); Flatsome wraps the last two in those media queries and prints everything in a `<style id="custom-css">` block. Stored in the `html_custom_css` option. Start each addition with a dated comment naming the change: `/* 2026-09 お問い合わせボタン */`. Change existing rules in place rather than adding overrides.
3. **Child theme `style.css`** only if the site keeps its CSS there (check first).

Never inline CSS in page content except a one-off that cannot be done otherwise.

## Writing CSS

- Target class names that really exist: read the page content and use its `class="…"` values, or add a class to the element in UX Builder (Advanced → CSS Class). No fragile selectors like `.row > .col:nth-child(3) .img`.
- Prefix new class names with the site prefix from the project (`.wpa-`, `.skyus-` …).
- Low specificity; `!important` only to beat an inline style Flatsome prints.
- Phone first: everything you add works at 360 and 390 px (Japan: also 375 and 414). Write phone styles, then `@media (min-width: 768px)` upward for your own layouts; when overriding Flatsome's own rules, use its 549 / 849 breakpoints.
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

Flatsome hooks (official list, 2026-10). **The filters `flatsome_sidebar`, `flatsome_footer_copyright`, `flatsome_breadcrumbs` and `flatsome_demo_content_notice` from the old skills do not exist.** What does:
- Actions for placing content: `flatsome_before_header`, `flatsome_after_header`, `flatsome_before_footer`, `flatsome_after_footer`, `flatsome_before_page_content`, `flatsome_after_page_content`, `flatsome_breadcrumb`, `flatsome_before_blog`, `flatsome_after_blog`, `flatsome_before_product_page`, `flatsome_after_product_page`, `flatsome_product_box_actions`, `flatsome_header_elements`, `flatsome_footer`, `flatsome_absolute_footer_primary` / `_secondary` (the copyright line area).
- Filters: `flatsome_sidebar_class`, `flatsome_header_class`, `flatsome_main_class`, `flatsome_html_atts`, `flatsome_viewport_meta`, `flatsome_payment_icons`, `flatsome_follow_links`, `flatsome_share_links`, `flatsome_product_labels`, `flatsome_product_box_classes`, `flatsome_lightbox_close_button`, `flatsome_maintenance_mode`, `flatsome_text_formats`, `flatsome_wpseo_breadcrumb_remove_last`, `flatsome_cache_clear_items`, plus WooCommerce swatch, mini-cart and search filters.
- To remove the sidebar or breadcrumbs use the page's own settings or Theme Options, not a filter. Copyright text is a Theme Options field (Footer → Absolute Footer).

## Custom page templates

Landing page without header and footer: a `templates/template-lp.php` with `Template Name: Landing Page`, printing `the_content()` in a wrapper. Full-width: `get_header()`, `<div id="content" class="page-wrapper"><div class="row"><div id="main" class="large-12 col">`, the loop, `get_footer()`.

## Fonts and performance

At most two families, few weights; Japanese web fonts subset or self-hosted with `font-display: swap`; prefer the Theme Options font setting. Hero images not lazy-loaded (`skip-lazy` class). More in `../wp-performance.md`.
