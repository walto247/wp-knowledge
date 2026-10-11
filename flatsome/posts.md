# Blog posts and articles on Flatsome

Status: merged 2026-10-11 from the WSL `flatsome-wp/posts` reference, product-article example generalised. Unverified (pass 2). Article structure and SEO: `../seo-geo/README.md`; copy: `../writing/`.

## Layout settings

- Global: Flatsome → Blog → Post Layout (sidebar position, featured image, meta: author, date, categories, tags).
- Per post: the Flatsome meta box below the editor (sidebar, featured image display).
- All posts full width: set it in Flatsome → Blog → Post Layout (sidebar: none). There is no `flatsome_sidebar` filter (checked against the official hook list 2026-10-11); the old snippet was wrong.

## Article structure

Featured image → intro that answers the question (no H2) → H2 sections of 2–3 paragraphs each, H3 inside → a gallery or figure where it helps → "why choose" or summary → one CTA (blockquote with a class or a Flatsome button). Author box and dated update line for E-E-A-T.

## Shortcodes inside posts

Flatsome shortcodes work in post content (Classic editor or a Shortcode block): `[ux_gallery …]`, `[ux_text_box …]` callouts, `[row][col]` for two columns, `[button …]`. Keep inline styles out of posts; give elements a class and style it once in the child theme.

## Article typography (child theme)

```css
.entry-content { max-width: 780px; margin: 0 auto; }
.entry-content h2 { margin: 48px 0 16px; padding-bottom: 8px; border-bottom: 2px solid var(--color-surface); }
.entry-content h3 { margin: 32px 0 12px; }
.entry-content p  { margin-bottom: 20px; line-height: 1.8; }   /* Japanese: 1.85–1.9 */
.entry-content blockquote { border-left: 4px solid var(--color-primary); background: var(--color-surface); padding: 16px 24px; border-radius: 0 8px 8px 0; margin: 40px 0; font-style: normal; }
.post-image img { width: 100%; height: auto; border-radius: 8px; margin-bottom: 32px; }
```

A checklist look for feature lists: `.entry-content .feature-list li::before { content: "✓ "; color: var(--color-primary); }` with `list-style: none` and a bottom border per item.
