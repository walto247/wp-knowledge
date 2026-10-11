# Flatsome theme

Status: **partly verified 2026-10-11.** Verified: current version **3.20.8 (2026-07-10)** and the planned v4 hybrid classic/block theme (ThemeForest listing); the full hook list (docs.uxthemes.com/article/385-hooks); custom CSS location (article 235); the responsive breakpoints 549 px / 849 px, the `custom-css` block, the `hide-for-medium` class and the `[accordion-item]` hyphen form, all read from live Flatsome sites. **Not verified:** the element attribute reference in `ux-builder.md`; the official docs have no element list, so it must be checked against the theme's own `inc/shortcodes/` files on a Flatsome server (next step). Items marked ⚠ remain doubtful.

| Need | Read |
|---|---|
| Page layout, sections, elements, landing pages | `ux-builder.md` |
| Where CSS goes, child theme, design tokens | `css-and-child-theme.md` |
| Shop and product pages | `woocommerce.md` |
| Blog posts and article layout | `posts.md` |

## How Flatsome works

Pages are built with **UX Builder**, which stores the layout as shortcodes in the post content: `[section]`, `[row]`, `[col]`, `[ux_banner]`, `[button]`, … Reusable parts are **UX Blocks** (post type `blocks`), placed with `[block id="slug"]`. Header, footer, menus and global styles live in **Flatsome → Theme Options** (the Customizer). Customisations go in a **child theme**.

## Workflow for a page change

1. Read the page content first. For a shared section, find the UX Block; the same block may sit on many pages, so say so before changing it.
2. Find the exact place. Copy the site's existing shortcodes and attributes; each site has its own habits. The accordion item is **`[accordion-item title="…"]`** with a hyphen (confirmed on a live 3.20 site); `accordion_item` with an underscore is not confirmed anywhere. Still copy what the page uses.
3. Change only that part. Keep everything else byte for byte, including line breaks. Never "tidy up" the rest.
4. Save, clear the cache (WP Rocket where present), check on desktop **and** phone.

## Rules

- **Flatsome first, simple is best.** Flatsome elements and Theme Options before custom HTML, CSS or PHP.
- Every `[col]` has a phone layout: `span__sm="12"` unless there is a reason.
- Balanced shortcodes: every `[section]`, `[row]`, `[col]`, `[ux_banner]`, `[text_box]`, `[accordion]` closes. Count before saving; one missing close tag breaks the page.
- Images by media ID (`[ux_image id="123" image_size="large"]`), not full URLs, when the site does; never hot-link other sites.
- One `<h1>` per page; sections `<h2>`, then `<h3>`.
- Same-site links relative (`/contact/`) so they work on staging and production.
- Never edit the parent theme. Child theme PHP is wrapped in `function_exists()` guards and linted before it goes live.
- Japanese text minimums apply (`../design/japan.md`): body 16 px, line height ≥ 1.7, tap targets ≥ 44 px, contrast ≥ 4.5:1.

## Breakpoints (verified on a live 3.20 site)

Phone: `max-width: 549px` (desktop/tablet from 550 px). Tablet: `max-width: 849px` (desktop from 850 px). The three Custom CSS boxes (all / tablet / mobile) wrap tablet and mobile rules in those queries. `span__sm` = up to 549 px, `span__md` = 550–849 px.

## Versions

3.20.8 (2026-07-10): accessibility markup updates, `Flatsome.cookie` deprecated for `Flatsome.Cookies`, scripts moved under `assets/js/extensions/`, new `flatsome-header-unsticky` event. Flatsome 4 is planned as a hybrid classic + block theme; migration will not be mandatory. The theme is pinned per site; update on staging first.

## Before saving (checklist)

Tags balanced · every column has `span__sm` · nothing wider than a phone screen · links relative · media by ID · cache cleared after · checked at 375 px.

## What changed in pass 2 (2026-10-11)

- Version, breakpoints, custom CSS location, accordion tag and hook names verified (see `css-and-child-theme.md` for the hook corrections).
- Element attributes still unverified: official docs carry no reference; verify against `wp-content/themes/flatsome/inc/shortcodes/` on a Flatsome server.
