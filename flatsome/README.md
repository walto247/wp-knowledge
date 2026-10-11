# Flatsome theme

Status: merged 2026-10-11 from the dashboard `flatsome-wp` skill and the WSL/account `flatsome-wp` skill (five references). Tool- and client-specific text removed. **Not yet verified against the official Flatsome documentation and current version (pass 2)**; items marked ⚠ are doubtful.

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
2. Find the exact place. Copy the site's existing shortcodes and attributes; each site has its own habits (for example the accordion item tag name: `accordion_item` or `accordion-item` depending on site and version; **always copy the one the site uses**).
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

## Before saving (checklist)

Tags balanced · every column has `span__sm` · nothing wider than a phone screen · links relative · media by ID · cache cleared after · checked at 375 px.
