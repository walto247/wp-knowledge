# Design tokens — a project's DESIGN.md and how it maps to code

Status: merged 2026-10-11 from the Flatsome `design-system` reference, made theme-neutral. Each project keeps its own `DESIGN.md`; this is the template and the mapping rules.

## DESIGN.md template

```markdown
# DESIGN.md — <project>

## Impression
- Impression: <trustworthy / warm / dense / premium …>   Tone: <…>   Avoid: <…>

## Colours (nothing outside this palette)
- Primary #… (CTAs, headings, nav) · Secondary #… (links, accents) · Text #… · Muted #…
- Surface #… (cards, alternate sections) · Border #… · White #FFFFFF

## Typography
- Family: <e.g. Noto Sans JP> (weights …) · Body 16 px / 1.8 · Small 14 px / 1.6 muted
- H1 … px / 700 / 1.2 · H2 … / 700 / 1.3 · H3 … / 600 / 1.4 · phone sizes …

## Spacing (8 px grid)
- Section padding … px (phone … px) · element gap … · card padding 24 · button 12 × 32

## Components
- Button primary / outline · Card · Navigation (max items, alignment, active style, phone menu)

## Layout
- Max width … px · side padding … · 1 section = 1 purpose · phone single column
```

## Extracting tokens from a screenshot or an existing site

Primary colour (CTA or header) → background → body text colour → heading font (weight, size) → body font → spacing rhythm → radius (buttons, cards) → shadow style. Write the result into the template above and confirm it with the owner before use.

## Mapping tokens to code

- Classic themes (Flatsome, SWELL child themes): CSS custom properties on `:root` in the child `style.css`; every rule uses `var(--color-primary)` and friends, never a raw hex.
- SWELL exposes its own variables (`var(--color_main)` …): set the tokens in the Customizer and use those variables rather than redefining them (see `../swell/`).
- Block themes: tokens live in `theme.json` (`settings.color.palette`, `settings.typography.fontSizes`, `settings.spacing`) and come out as `var(--wp--preset--color--primary)` (see `../block-themes/`).
- Page-builder attributes (UX Builder `bg_color="#…"`) use the hex from the palette, nothing else.

## Checks before any output

Every colour from the palette? Every size from the scale? Spacing in grid units? Buttons match the component spec? If a new value is truly needed, add it to `DESIGN.md` first.
