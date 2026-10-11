# WooCommerce on Flatsome

Status: merged 2026-10-11 from the WSL `flatsome-wp/woocommerce` reference. Unverified against current Flatsome and WooCommerce (pass 2). Prices and claims on Japanese shops: `../legal/japan.md` (総額表示, 特定商取引法).

## Where the product page layout is set

Flatsome → WooCommerce → Product Page (gallery style, tabs, sidebar). Prefer these options over code. Child-theme hooks only when the options cannot do it:

```php
// Remove the default tabs
add_filter('woocommerce_product_tabs', function ($tabs) {
    unset($tabs['description'], $tabs['reviews']);
    return $tabs;
}, 98);

// Move the short description lower
remove_action('woocommerce_single_product_summary', 'woocommerce_template_single_excerpt', 20);
add_action('woocommerce_single_product_summary', 'woocommerce_template_single_excerpt', 25);
```

## Galleries

`[ux_gallery ids="…" columns="4" columns__sm="2" lightbox="true" image_height="75%"]` is Flatsome's own gallery: lightbox, lazy load and responsive columns included. Use it instead of hand-written HTML grids with inline styles.

## Shop and archive card CSS (tokens from DESIGN.md)

```css
.products .product { border: 1px solid var(--color-border); border-radius: var(--radius-card); padding: 16px; }
.products .product:hover { box-shadow: 0 4px 12px rgba(0,0,0,.10); }
.woocommerce-loop-product__title { font-size: 16px; font-weight: 600; color: var(--color-text); }
.price { color: var(--color-primary); font-weight: 700; }
.add_to_cart_button, .single_add_to_cart_button { background: var(--color-primary); border-radius: var(--radius-button); }
```

Other small overrides: hide meta with `.product_meta { display: none; }`; square gallery thumbnails with `.woocommerce-product-gallery__image img { object-fit: cover; aspect-ratio: 1; }`.

## "Ready to shop" link in articles

A blockquote with a class (`<blockquote class="shop-cta">…<a href="/product/…">商品名</a></blockquote>`) styled once in the child theme: left border in the primary colour, surface background, 16 × 24 px padding. No inline styles in the post.

## Japanese shops

Prices with tax (「¥11,000（税込）」), shipping and return rules reachable from every product page, the 特定商取引法に基づく表記 page in the footer, and a confirmation step before payment.
