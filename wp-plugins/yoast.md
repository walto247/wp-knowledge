# Yoast SEO

Status: merged 2026-10-11. Unverified against the current Yoast version (pass 2).

## Per-page fields (safe to edit)

| Field | Stored as | Guidance |
|---|---|---|
| SEO title | `_yoast_wpseo_title` | Empty = Yoast uses the site template. Set only when the template result is weak. |
| Meta description | `_yoast_wpseo_metadesc` | Empty = Google picks text from the page. Write one for important pages. |
| Focus keyphrase | `_yoast_wpseo_focuskw` | Only for Yoast's own analysis; no effect on Google. |

- Variables work in titles: `%%title%%`, `%%sep%%`, `%%sitename%%`, `%%page%%`, `%%primary_category%%`.
- An empty value removes the custom field. After changing meta by code, re-save the post so Yoast refreshes its indexable.
- Lengths and wording: `../seo-geo/README.md`.

## Read before writing

Site templates are in the option `wpseo_titles`; read them so the site name is not repeated twice. Other settings (`wpseo`, `wpseo_social`) are a person's to change.

## Facts

- Yoast prints breadcrumbs, canonical, Open Graph and schema itself. Never add a duplicate `<title>`, description, canonical or JSON-LD by hand.
- `noindex`, redirects (Premium) and sitemap settings are decisions for a person.
- Staging has "search engines discouraged" on; Yoast shows a warning there, which is correct.
