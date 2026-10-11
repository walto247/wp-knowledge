# Block themes (theme.json)

Status: stub created 2026-10-11 for `wp-master-theme`. To be written in pass 2 against the WordPress theme.json reference and the master theme's own docs. Nothing below is verified.

## What goes here

- How the design tokens (`../design/design-tokens.md`) map to `theme.json`: `settings.color.palette`, `settings.typography.fontFamilies` and `fontSizes` (fluid), `settings.spacing.spacingSizes`, `settings.layout.contentSize` / `wideSize`; the resulting `var(--wp--preset--…)` variables.
- `styles` for elements (headings, buttons, links) and per block; when a block style variation beats a CSS rule.
- Templates and template parts, patterns (`patterns/*.php` with headers), per-site child themes that override only `theme.json` and patterns.
- Japanese defaults for the master theme: body 16 px, line height 1.8–1.9, `line-break: strict`, font stack from `../design/japan.md`, tap targets 44–48 px.
- Rules carried over from the owner: follow the designer's render exactly; the visitor comes first.

Until this file is filled in, the master theme project's own `docs/` are the source.
