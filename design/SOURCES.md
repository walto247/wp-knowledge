# Sources for pass 2 (design and accessibility)

Links given by the owner on 2026-10-11, to check `design/japan.md` and `design/accessibility.md` against.
Shortened links; resolve and record the final URL and the date checked when used.

| Topic | Source | Link (resolved) | Read |
|---|---|---|---|
| Japanese accessibility standard | JIS X 8341-3:2016 達成基準 1.4.3 implementation checklist example (金融庁 site, InfoCreate) | https://www.fsa.go.jp/accessibility/2018/fsa18023/7.1.4.3.html (short: https://chibko.me/gj7zn) | 2026-10-11 |
| Japanese government design system, typography | デジタル庁デザインシステム（DADS）タイポグラフィ | https://design.digital.go.jp/dads/foundations/typography/ (short: https://chibko.me/mtk86) | 2026-10-11 |
| DADS colour (contrast, links, focus) | デジタル庁デザインシステム カラー | https://design.digital.go.jp/dads/foundations/color/ | 2026-10-11 |
| DADS foundations index | 余白, レイアウト, アイコン, リンクテキスト, 角の形状, エレベーション | https://design.digital.go.jp/dads/foundations/ | 2026-10-11 (index only) |
| Japanese government design system, policy page | デジタル庁 デザインシステム | https://www.digital.go.jp/policies/servicedesign/designsystem (short: https://chibko.me/kz2fx) | **not reachable 2026-10-11** (connection reset twice); retry |
| Japanese text layout requirements | W3C 日本語組版処理の要件（JLReq） | https://w3c.github.io/jlreq/?lang=ja (short: https://chibko.me/jquow) | 2026-10-11 (line composition, 禁則, ruby, Latin mixing) |
| International standard | WCAG 2.2 (W3C), "What's new in 2.2" | https://www.w3.org/TR/WCAG22/ · https://www.w3.org/WAI/standards-guidelines/wcag/new-in-22/ | 2026-10-11 |
| JIS revision status | gihyo.jp 2026-01 outlook; issoh.co.jp column | https://gihyo.jp/article/2026/01/web-accessibility-prospect · https://www.issoh.co.jp/column/details/3022/ | 2026-10-11 (revision to WCAG 2.2 in committee since 2025-10, expected 2026, not yet published) |
| Conformance claims | WAIC JIS X 8341-3:2016 対応度表記ガイドライン | https://waic.jp/ | not read; cited by the articles above |


## Screen sizes (read 2026-10-15, for `general.md` and `japan.md` "Screen sizes")

| Topic | Source | Link | Read |
|---|---|---|---|
| Bootstrap breakpoints and containers | Bootstrap 5.3 docs | https://getbootstrap.com/docs/5.3/layout/breakpoints/ · https://getbootstrap.com/docs/5.3/layout/containers/ | 2026-10-15 |
| Tailwind breakpoints and container | Tailwind CSS v4 docs | https://tailwindcss.com/docs/responsive-design · https://tailwindcss.com/docs/container | 2026-10-15 |
| iPhone and Android viewport widths | Use Your Loaf (transcribes Apple's point sizes; Apple HIG page did not load) · yesviz device table | https://useyourloaf.com/blog/iphone-17-screen-sizes/ · https://yesviz.com/mobiles.php | 2026-10-15 |
| Figma frame presets | Figma Help (categories only, no sizes; 1440 × 1024 Desktop from tutorials) | https://help.figma.com/hc/en-us/articles/360041539473-Frames-in-Figma-Design | 2026-10-15 |
| Japan phone OS and resolutions | StatCounter Japan, September 2026 | https://gs.statcounter.com/os-market-share/mobile/japan · https://gs.statcounter.com/screen-resolution-stats/mobile/japan | 2026-10-15 |
| Japan desktop resolutions | StatCounter Japan, September 2026 | https://gs.statcounter.com/screen-resolution-stats/desktop/japan | 2026-10-15 |
| Breakpoint, grid, gutter | DADS レイアウト (v2.18.1): one breakpoint at 768, 12 columns, gutter = 2 × body text; no max width, no margin value | https://design.digital.go.jp/dads/foundations/layout/ | 2026-10-15 |
| Line length | JLReq §2.4.2 note (horizontal: at most about 40 characters) | https://www.w3.org/TR/jlreq/ | 2026-10-15 |
| Japanese agency practice (PC/SP, 375/1366/1440, 768, container) | LIG 2022 · KKI DESIGN 2025 · issoh 2026 · zenn tak_dcxi 2020 | https://liginc.co.jp/582225 · https://note.com/kki_design_/n/n3a2c00bd3cba · https://www.issoh.co.jp/tech/details/15329/ · https://zenn.dev/tak_dcxi/articles/88762df24ef2eb3013c2 | 2026-10-15 (practice, not a standard) |
| Japanese article column survey | LIG 2016 (ten media sites, 670 px most common) | https://liginc.co.jp/299824 | 2026-10-15 |
| Image density | web.dev Learn Images · Jake Archibald 2021 (above 2× rarely worth it) | https://web.dev/learn/images/descriptive · https://jakearchibald.com/2021/serving-sharp-images-to-high-density-screens/ | 2026-10-15 |

Checked and corrected from a pasted article (2026-10-15): Tailwind does not share Bootstrap's six tiers; 1366 × 768 is about 5 % in Japan, not "massive"; JLReq gives a 40-character maximum, not a 35–45 range, so 720–840 px article columns are too wide; web.dev does not set a 2× cap (expert advice does); newest iPhones are 402 wide, not 393.

## Typography 2 (read 2026-10-15, for `japan.md` "Brand and premium typography" and `general.md` "English typography" and spacing rhythm)

| Topic | Source | Link | Read |
|---|---|---|---|
| Japanese sizes, line height, spacing, weights, italics | DADS タイポグラフィ | https://design.digital.go.jp/dads/foundations/typography/ | 2026-10-15 |
| Spacing base and example steps (8 / 24 / 64) | DADS 余白 | https://design.digital.go.jp/dads/foundations/spacing/ | 2026-10-15 |
| Character frame, line gap, 40-character maximum, 禁則, 両端揃え, Japanese–Latin spacing | W3C JLReq §2.1, §2.4, §3.1.7, §3.2, §3.8 | https://www.w3.org/TR/jlreq/ | 2026-10-15 |
| Line length 80 / 40 CJK, not justified (AAA); text spacing must survive 1.5 (AA) | WCAG 2.2 1.4.8, 1.4.12 | https://www.w3.org/WAI/WCAG22/Understanding/visual-presentation.html · https://www.w3.org/TR/WCAG22/ | 2026-10-15 |
| English tracking and measure | Google Fonts Knowledge (tracking, measure) | https://fonts.google.com/knowledge | 2026-10-15 |
| English type scale numbers | Material 3 type scale tokens | https://github.com/material-components/material-web (tokens `_md-sys-typescale.scss`) | 2026-10-15 |
| `text-spacing-trim`, `text-autospace`, `word-break: auto-phrase`, `text-wrap`, `text-justify` | MDN, caniuse, Chrome i18n blog | https://developer.mozilla.org/en-US/docs/Web/CSS/text-spacing-trim · https://caniuse.com/mdn-css_properties_word-break_auto-phrase · https://developer.chrome.com/blog/css-i18n-features | 2026-10-15 |
| Phrase wrapping script | Google BudouX | https://github.com/google/budoux | 2026-10-15 |
| `palt` and Meiryo | ICS MEDIA | https://ics.media/en/entry/14087/ | 2026-10-15 |
| Body ベタ組み, palt on headings only (practice) | kiso.css (tak-dcxi) | https://gist.github.com/tak-dcxi/0f8b924d6dd81aaeb58dc2e287f2ab3a | 2026-10-15 |
| Noto Sans JP weights (variable 100–900, no italic) | google/fonts METADATA | https://github.com/google/fonts/tree/main/ofl/notosansjp | 2026-10-15 |
| Latin font matching | MDN `size-adjust`; W3C inline spacing | https://developer.mozilla.org/docs/Web/CSS/@font-face/size-adjust · https://www.w3.org/International/articles/styling/inline-space | 2026-10-15 |
| Eyebrow is not a heading | Primer heading accessibility; Deque | https://primer.style/product/components/heading/accessibility · https://docs.deque.com/issue-help/1.0.0/en/semantic-heading/ | 2026-10-15 |
| Proximity | NN/g | https://www.nngroup.com/articles/gestalt-proximity/ | 2026-10-15 |
| Mincho vs Gothic (practice) | Fujifilm design seminar | https://www.fujifilm.com/fb/ja/support/colorprint/howto/design/seminar-05 | 2026-10-15 |

Rejected from a pasted article (2026-10-15): Japanese body letter spacing 0.04–0.08 em and headings +3–8 % (DADS: 2 % / 1 % / 0, less as size grows); body line height "1.8–1.9 sweet spot" and "collides below 1.7" (DADS 1.5–1.75; JLReq's usual range ends at line height 2.0 for long lines); 12–13 px captions (DADS floor 14); 42-character lines (JLReq / WCAG 40); Japanese body justified on the web (WCAG 1.4.8, uneven mixed-script lines). No source for "kanji fill 90 %", "looks 10–15 % larger" or "titles 1–4 px smaller".

## UX and surfaces (read 2026-10-15, for `general.md` "Navigation, surfaces and motion" and the `japan.md` navigation, forms and surfaces additions)

| Topic | Source | Link | Read |
|---|---|---|---|
| Focus not obscured, reflow, target size, non-text contrast, text over images, animation, redundant entry, input purpose | WCAG 2.2 Understanding 2.4.11, 1.4.10, 2.5.8, 1.4.11, 1.4.3, 2.3.3, 3.3.7, 1.3.5 | https://www.w3.org/WAI/WCAG22/Understanding/ | 2026-10-15 |
| Menu button label, mega menu (no hover-only), breadcrumb placement, input text (※必須/※任意, 郵便番号) | DADS components | https://design.digital.go.jp/dads/components/hamburger-menu-button/ · https://design.digital.go.jp/dads/components/mega-menu/ · https://design.digital.go.jp/dads/components/breadcrumb/ · https://design.digital.go.jp/dads/components/input-text/usage/ | 2026-10-15 |
| Elevation, corner radius, layout grid | DADS foundations; DADS design tokens (#000 text, Solid Gray 900 #1A1A1A, elevation 1–8) | https://design.digital.go.jp/dads/foundations/elevation/ · https://design.digital.go.jp/dads/foundations/corner-shapes/ · https://unpkg.com/@digital-go-jp/design-tokens/dist/tokens.css | 2026-10-15 |
| Motion easing and duration, elevation, top bar | Material 3 tokens (material-web source) | https://github.com/material-components/material-web | 2026-10-15 |
| Mega menus, hover timing, hidden navigation, breadcrumbs, animation duration | NN/g | https://www.nngroup.com/articles/mega-menus-work-well/ · https://www.nngroup.com/articles/timing-exposing-content/ · https://www.nngroup.com/articles/hamburger-menus/ · https://www.nngroup.com/articles/breadcrumbs/ · https://www.nngroup.com/articles/animation-duration/ | 2026-10-15 |
| Breadcrumb structured data | Google Search Central | https://developers.google.com/search/docs/appearance/structured-data/breadcrumb | 2026-10-15 |
| Safe area, backdrop-filter, aspect-ratio | MDN | https://developer.mozilla.org/en-US/docs/Web/CSS/env · https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter · https://developer.mozilla.org/en-US/docs/Web/CSS/aspect-ratio | 2026-10-15 |
| Opacity 0 and LCP | web.dev | https://web.dev/articles/lcp | 2026-10-15 |
| How people hold phones | Steven Hoober (A List Apart, UXmatters 2013) | https://alistapart.com/article/how-we-hold-our-gadgets/ | 2026-10-15 |
| Easing default (ease-out; linear for fades) | ICS MEDIA | https://ics.media/entry/18730/ | 2026-10-15 |
| What makes Japanese visitors distrust a site | デザポケ survey, Web担当者Forum 2025-11-20 | https://webtan.impress.co.jp/n/2025/11/20/50449 | 2026-10-15 |
| 最終確認画面 (sales contracts only) | 消費者庁 通信販売の申込み段階における表示についてのガイドライン | https://www.caa.go.jp/ (PDF consumer_transaction_cms101_2401119_03.pdf) | 2026-10-15 (via the PDF; to re-check in the 特商法 pass) |
| 白銀比 / 大和比 | CGWORLD 2019 | https://cgworld.jp/regular/201901-colobito04-ratio-2.html | 2026-10-15 |

Rejected or softened from a pasted article (2026-10-15): muted captions #86868B / #888 (fail 4.5:1); "never pure black" and kanji "halation" (DADS uses #000; no source); shadows "never above 6 %" (DADS and Material use stronger); hover menus with a 150 ms delay (DADS: no hover-only; NN/g 0.3–0.5 s); breadcrumbs above the footer as the main place (DADS and NN/g: below the header); scroll fades of 800–1000 ms (NN/g 100–400 ms); "never linear" (fine for fades); email confirmation fields (WCAG 3.3.7); "bottom bar boosts conversion dramatically" and "Japanese users spot foreign stock photos" (no data).

## Page structure (read 2026-10-15, for `general.md` "Content blocks and page order" and `japan.md` "Top page order")

| Topic | Source | Link | Read |
|---|---|---|---|
| "Learn more" links | NN/g | https://www.nngroup.com/articles/learn-more-links/ | 2026-10-15 |
| Link purpose | WCAG 2.2 Understanding 2.4.4 | https://www.w3.org/WAI/WCAG22/Understanding/link-purpose-in-context.html | 2026-10-15 |
| Zigzag layouts | NN/g eye-tracking | https://www.nngroup.com/articles/zigzag-page-layout/ | 2026-10-15 |
| Reading and focus order vs CSS order | WCAG 2.2 Understanding 1.3.2, 2.4.3 | https://www.w3.org/WAI/WCAG22/Understanding/meaningful-sequence.html · https://www.w3.org/WAI/WCAG22/Understanding/focus-order.html | 2026-10-15 |
| Carousels | NN/g auto-forwarding; Baymard | https://www.nngroup.com/articles/auto-forwarding/ · https://baymard.com/blog/homepage-carousel | 2026-10-15 |
| Scroll indicators | Viget eye-tracking study | https://www.viget.com/articles/should-you-use-a-custom-scroll-indicator-a-study-with-eye-tracking/ | 2026-10-15 |

Rejected from a pasted article (2026-10-15): "Learn more →" as the card link (NN/g, WCAG 2.4.4); zigzag as a general rule (NN/g: 2–3 rows, informational images only); scroll indicators as a proven cue (no effect measured).

## Monthly check 2026-10-17

| Topic | Source | Link |
|---|---|---|
| JIS X 8341-3 revision timing (2027, at the latest 2028) | WAIC news 2026-09-28 | https://waic.jp/news/news-7938/ |
| WCAG 3.0 working draft | W3C, 2026-09-10 | https://www.w3.org/TR/wcag3/ |
| DADS still v2.18.1 (design data re-issued 2026-10-14; React v1 components removed 2026-09-09) | デジタル庁デザインシステム update history | https://design.digital.go.jp/dads/ |
