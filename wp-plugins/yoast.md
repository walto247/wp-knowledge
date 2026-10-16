# Yoast SEO

Status: checked 2026-10-11. Meta keys and the "save the post afterwards" rule come from WordPress.org support threads and the Yoast REST/API ecosystem (the Yoast developer page on indexables returned 404); Yoast's official page documents the `wpseo_title` output filter.

## Per-page fields (safe to edit)

**Owner rule (2026-10-16): every page gets its SEO title, meta description and focus keyphrase written right after its content is in. No page goes to production with any of them empty.** Site packs keep them in their SEO data file in the same change that adds the page; audit `_yoast_wpseo_title`, `_yoast_wpseo_metadesc` and `_yoast_wpseo_focuskw` on every page before a release. (The "empty = template / Google picks" behaviour below is a fallback, not a choice.)


| Field | Stored as | Guidance |
|---|---|---|
| SEO title | `_yoast_wpseo_title` | Empty = Yoast uses the site template. Set only when the template result is weak. |
| Meta description | `_yoast_wpseo_metadesc` | Empty = Google picks text from the page. Write one for important pages. |
| Focus keyphrase | `_yoast_wpseo_focuskw` | Only for Yoast's own analysis; no effect on Google. |

- Variables work in titles: `%%title%%`, `%%sep%%`, `%%sitename%%`, `%%page%%`, `%%primary_category%%`.
- An empty value removes the custom field. **After writing `_yoast_wpseo_*` meta by code, call `wp_update_post()` (or save in the editor)**: Yoast rebuilds its indexable on post save, not on a meta write. The SEO-score dots in the post list may still lag. The `wpseo_title` filter changes output only, not stored values.
- Lengths and wording: `../seo-geo/README.md`.

## Read before writing

Site templates are in the option `wpseo_titles`; read them so the site name is not repeated twice. Other settings (`wpseo`, `wpseo_social`) are a person's to change.

## Facts

- Yoast prints breadcrumbs, canonical, Open Graph and schema itself. Never add a duplicate `<title>`, description, canonical or JSON-LD by hand.
- `noindex`, redirects (Premium) and sitemap settings are decisions for a person.
- Staging has "search engines discouraged" on; Yoast shows a warning there, which is correct.
