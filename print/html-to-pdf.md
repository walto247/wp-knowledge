# Building print files from HTML/CSS (for code agents)

Status: **verified 2026-10-20** against W3C css-page-3, MDN, caniuse, Puppeteer and Playwright docs, the Vivliostyle docs and CMYK cookbook, Prince docs and the Ghostscript docs (`SOURCES.md`). Production values: `production.md`.

## What a browser can and cannot do (fact)

- **Chromium (Puppeteer, Playwright) writes RGB PDFs only**: every colour is DeviceRGB, CMYK images are converted to RGB, no spot colours, no overprint, no PDF/X output intent. Never promise a press-ready CMYK or PDF/X file from Chromium alone.
- Chromium ignores CSS `marks` and `bleed` (no browser supports them): draw crop marks yourself, or send a bleed-only PDF where the vendor accepts it.
- Fonts are embedded (subset) automatically.

## Page setup (fact)

- `@page { size: 216mm 303mm; margin: 0 }` for A4 with bleed (trim + 6 mm); JIS B4 `263mm 370mm`, B5 `188mm 263mm`, A5 `154mm 216mm`. Puppeteer/Playwright: `preferCSSPageSize: true` (their `format` option knows ISO A and Letter, not JIS B) and `printBackground: true`.
- `print-color-adjust: exact` (plus `-webkit-print-color-adjust: exact` for older Chromium) keeps backgrounds.
- One fixed-size box per page (`width`/`height` in mm, `overflow: hidden`, `break-after: page`) so nothing spills onto an extra page.
- Sizes in **mm** for layout and **pt** (or Q via mm) for type; never `px`, `vh` or `%` of the viewport.
- Maps, icons, badges and QR codes as inline **SVG** (vector, sharp at any resolution).

## Japanese typography in print engines (fact)

- `writing-mode: vertical-rl`, `font-feature-settings: "palt"` and `line-break: strict` work in Chromium, Vivliostyle and Prince.
- `word-break: auto-phrase` is **Chromium only** (119+) and needs `lang="ja"`; not in Vivliostyle-on-other-engines, Firefox, Safari or Prince.
- Pair a Latin face for numbers with the Japanese face (practice).

## Three output routes

| Route | When | How |
|---|---|---|
| **A. RGB PDF from Chromium** (default) | ラクスル / グラフィック jobs, short runs, no brand-critical colour | embedded fonts, bleed size, `printBackground`; tell the vendor it is RGB; they convert to CMYK (ラクスル free, グラフィック paid, Japan Color 2011); approve the converted proof |
| **B. Vivliostyle CLI** | press jobs needing CMYK / PDF/X-1a | colours written as `device-cmyk()`; `pdfPostprocess.cmyk` converts text, fills and borders (images must be CMYK files beforehand, gradients and filters are not converted); `--preflight press-ready` makes PDF/X-1a via Ghostscript + poppler (Docker recommended). Supports `marks: crop`, `bleed`, JIS-B size keywords |
| **C. PrinceXML** (paid licence) | full control: CMYK, spot colours, PDF/X | `--pdf-profile="PDF/X-1a:2003"` and `--pdf-output-intent=<Japan Color ICC>`; `cmyk()` / `device-cmyk()`; spot colours via `@prince-color`; `marks: crop cross`, `bleed` |

- Ghostscript can convert an RGB PDF to CMYK with a Japan Color ICC (`-sColorConversionStrategy=CMYK`), but its PDF/X support is documented inconsistently: check the result with Acrobat preflight or Ghostscript `inkcov` (ink coverage) before sending.
- For every route: keep small text and thin lines K100 (`device-cmyk(0 0 0 1)`; in route A use pure #000 and accept the vendor's conversion), rich black C50 M40 Y40 K100 for big areas, total ink ≤ 300 %.

## Checks before handing over (practice)

1. Page size = trim + 6 mm exactly; page count right (two-sided = 2 pages).
2. Text ≥ 3 mm inside the trim (our default 10 mm); nothing important on folds.
3. Fonts embedded; images 350 dpi at placed size.
4. Black text is K-only (CMYK routes); ink total within the limit (`inkcov`).
5. QR scans from the printed size; the URL carries UTM.
6. File named `<client>_<item>_<size>_<date>_v<n>.pdf`; the HTML source and assets kept in the project, the PDF in `tmp/01_reports/` until approved.
