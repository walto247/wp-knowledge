# Performance and Core Web Vitals

Status: **thresholds verified 2026-10-11** against web.dev/articles/vitals (last updated 2024-10-31; Core Web Vitals definitions change at most once a year). Fix guidance is practice. Caching plugin: `wp-plugins/wp-rocket.md`. Sources: `wp-plugins/SOURCES.md`.

Shared hosting has had load problems: fast pages matter, and heavy fixes must not load the server. One change at a time, measured before and after.

## Targets (mobile)

| Metric | Good | Poor | Usual cause when bad |
|---|---|---|---|
| LCP (largest element shown) | ≤ 2.5 s | > 4.0 s | big hero image, lazy-loaded hero, slow server response |
| INP (reaction to taps; replaced FID in 2024) | ≤ 200 ms | > 500 ms | heavy JavaScript, sliders, chat widgets, tag managers |
| CLS (layout jumping) | ≤ 0.1 | > 0.25 | images without width/height, late fonts, banners inserted above content |
| Page weight (practice) | under ~1 MB | | originals in content, fonts, embeds |

A page passes when all three are "good" at the **75th percentile** of real visits, mobile and desktop measured separately. Measure with PageSpeed Insights (field data first) or Search Console's Core Web Vitals report; fix the biggest item; clear cache; measure again.

## Images

- Right size for the slot (not a 4000 px original in a 600 px column); WebP (AVIF where supported); descriptive `alt`; explicit `width` and `height` or `aspect-ratio`.
- Size targets (practice): hero image under about 200–250 KB, card images under about 80 KB, after WebP.
- Hero: `fetchpriority="high"`, never lazy. With WP Rocket, exclude it in Media → LazyLoad → **Excluded images or iframes** (a filename, class or attribute, one per line) or give the `<img>` the `skip-lazy` class / `data-skip-lazy` attribute; Flatsome's own lazy load honours `skip-lazy` too. Optionally `<link rel="preload" as="image">`. Below the fold: `loading="lazy"`.
- Responsive: `srcset` + `sizes`; in Flatsome use `image_size="large"` / `"medium"`, not `original`.
- **WebP by default on every site we build (owner rule, 2026-10-12)** — WordPress native, no plugin: filter `image_editor_output_format` maps `image/jpeg` → `image/webp` (quality 82 via `wp_editor_set_quality`). On WordPress 7 every size of a JPEG upload, the full size included, is then saved as WebP; the original JPEG stays on disk (`original_image`) as the regeneration source. Existing images: `wp media regenerate <jpeg IDs> --yes`, then `wp yoast index --reindex` and a cache/CDN purge. Keep PNG as PNG (logos, icons, transparency; GD's WebP alpha shows fringes), keep SVG/GIF; site icon / apple-touch-icon stay PNG. Share images (og:image / twitter:image): point them to the original JPEG (Facebook and LINE do not reliably show WebP previews). Check: page source shows `.webp` in `src`/`srcset`, a card loads the ~768 px WebP, not the original. SKW: belongs in skw-core (request in wp-anshin-com); until then the child theme carries the filters.
- `sizes` must match the slot: a card a third of the page wide with `sizes="100vw"` makes browsers download the biggest file.

## CSS, fonts, scripts

- Remove rules no longer used; no frameworks or icon fonts for one icon; prefer the theme's options.
- At most two font families, few weights; Japanese web fonts are very large (a full Noto Sans JP file is several MB): subset or self-host, `font-display: swap`, or system fonts. Google Fonts already splits Japanese fonts into about 120 `unicode-range` slices and the browser downloads only the slices a page uses (checked 2026-10-15); `preload` would ignore that, so do not preload a whole Japanese font. `font-display: swap` shows fallback text first (small shift); `optional` avoids the shift but may skip the web font on slow connections (web.dev).
- Scripts in the footer, versioned by file time; load libraries (GSAP, maps) only on the pages that need them; break long tasks up.
- Animate only `transform` and `opacity`; never width, height, margin, padding, top or left.
- Mobile-first CSS: base styles for phones, `@media (min-width: …)` upward.

## Content

Long pages with many sliders, videos or embedded maps are slow: static image linking to the map or video, fewer sliders, embeds below the fold.

## A person decides

WP Rocket settings (delay JS, remove unused CSS, preload), image optimisation plugins, server, PHP and database changes, CDN. Name the setting and why.
