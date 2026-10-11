# Performance and Core Web Vitals

Status: merged 2026-10-11 from the dashboard `wp-performance` skill and the WSL `frontend-wp/performance` reference. Unverified against current web.dev guidance (pass 2). Caching plugin: `wp-plugins/wp-rocket.md`.

Shared hosting has had load problems: fast pages matter, and heavy fixes must not load the server. One change at a time, measured before and after.

## Targets (mobile)

| Metric | Good | Usual cause when bad |
|---|---|---|
| LCP (largest element shown) | ≤ 2.5 s | big hero image, lazy-loaded hero, slow server response |
| CLS (layout jumping) | ≤ 0.1 | images without width/height, late fonts, banners inserted above content |
| INP (reaction to taps) | ≤ 200 ms | heavy JavaScript, sliders, chat widgets, tag managers |
| Page weight | under ~1 MB ideally | originals in content, fonts, embeds |

Measure with PageSpeed Insights (field data first) or Search Console's Core Web Vitals report; fix the biggest item; clear cache; measure again.

## Images

- Right size for the slot (not a 4000 px original in a 600 px column); WebP (AVIF where supported); descriptive `alt`; explicit `width` and `height` or `aspect-ratio`.
- Hero: `fetchpriority="high"`, never lazy (`skip-lazy` class with WP Rocket), optionally `<link rel="preload" as="image">`. Below the fold: `loading="lazy"`.
- Responsive: `srcset` + `sizes`; in Flatsome use `image_size="large"` / `"medium"`, not `original`.

## CSS, fonts, scripts

- Remove rules no longer used; no frameworks or icon fonts for one icon; prefer the theme's options.
- At most two font families, few weights; Japanese web fonts are very large: subset or self-host, `font-display: swap`, or system fonts.
- Scripts in the footer, versioned by file time; load libraries (GSAP, maps) only on the pages that need them; break long tasks up.
- Animate only `transform` and `opacity`; never width, height, margin, padding, top or left.
- Mobile-first CSS: base styles for phones, `@media (min-width: …)` upward.

## Content

Long pages with many sliders, videos or embedded maps are slow: static image linking to the map or video, fewer sliders, embeds below the fold.

## A person decides

WP Rocket settings (delay JS, remove unused CSS, preload), image optimisation plugins, server, PHP and database changes, CDN. Name the setting and why.
