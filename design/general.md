# Design fundamentals (any site)

Status: merged 2026-10-11 from `global-web`, `ux-ui` and `wireframes` (dashboard skills). Not yet verified against WCAG 2.2 / current references (pass 2), except "Screen sizes, breakpoints and widths", the spacing rhythm, "English typography", "Navigation, surfaces and motion" and "Content blocks and page order", researched 2026-10-15. For Japanese sites read `japan.md` as well; where they differ, `japan.md` wins.

## Owner's rules (stand above everything else)

- **The visitor comes first, not the design.** Every choice is judged by how little stress it causes the person using the page (owner rule, 2026-10-09).
- **Follow the designer's render exactly** when a site is built from a design: match it, never simplify, add or recolour. Flag problems; the owner decides (owner rule, 2026-10-10).
- **Commit to one deliberate direction.** No generic "AI look": purple gradients, identical card grids, stock hero + three icons. Decide the impression first (calm, dense, warm, premium…) and let every element serve it.

## Page structure

- **One page, one goal.** Know what the visitor should do (call, request a brochure, buy, read) before touching a page; make that action obvious at the top and the end.
- Visual order = importance: headline → key benefit → proof → action. Never start with history or greetings.
- Scannable: clear H2/H3, short paragraphs, lists, white space. People skim.
- **Consistency:** reuse the site's colours, fonts, spacing, buttons and section styles. A new colour or font size needs a reason; a page must look like the rest of the site.
- Phone first: check every change at 360 and 390 px (all test widths: "Screen sizes" below). The **page** never scrolls sideways; a deliberate sideways row inside a section is fine and expected on phones (card carousel / works or news row: scroll-snap, swipe on phones, mouse drag or arrow buttons on PC, the next card peeking in so people see there is more; owner, 2026-10-15). Buttons reachable with a thumb; text readable without zoom. Test tools: flag `document.documentElement.scrollWidth > innerWidth` only, not inner scrollers with `overflow-x: auto`.

Typical page goals: home = trust and the next step; service page = explain value, convert to an inquiry; blog post = teach, build authority, link inward; contact = remove friction; landing page = one CTA, nothing else.

## Visual hierarchy and spacing

1. Most important: largest, highest contrast, top or left.
2. Secondary: medium weight, secondary colour.
3. Supporting: smaller, muted.
4. Every element has one role; nothing competes.

Spacing scale (use the scale, never arbitrary values): 4 / 8 / 16 / 24 / 32 / 40 / 48 / 64 / 80 / 96 / 128 px.
Sections: 48 px apart on phones, 64–96 px on desktop (premium or editorial sites up to 128 desktop / 64–80 phone, practice). Content width and side padding: "Screen sizes" below. 8 px grid.

**Spacing rhythm** (practice, built on proximity: a heading sits closer to its own text than to what came before it; DADS 余白 uses an 8 px base and shows 8 / 24 / 64 as label→title / title→body / above a block):

| Gap | Desktop | Phone |
|---|---|---|
| Eyebrow label → heading | 8 | 8 |
| H2 → content below | 40–48 | 24–32 |
| H3 → its paragraph | 16 | 16 |
| Paragraph → paragraph | 1–1.5 em (24) | 1–1.5 em (16–24) |
| Paragraph → next H3 | 48 (3 × the H3 → paragraph gap) | 32–40 (2–2.5 ×) |
| Image → text block | 32–48 | 24–32 |
| Image → its caption | 8 | 8 |

## English typography (checked 2026-10-15)

Japanese rules are in `japan.md` (Japanese and English need opposite treatment). Sources: WCAG 2.2, Google Fonts Knowledge, Material 3 type scale (`SOURCES.md`, section "Typography 2").

- **Body:** 16 px or more, line height **1.5–1.6** (WCAG 1.4.12: the layout must survive 1.5 set by the user). Left-aligned, never justified (WCAG 1.4.8, AAA: justified text makes uneven gaps).
- **Headings:** line height **1.1–1.25** (Material: display 57/64, headline 32/40). Large display sizes may take slight negative tracking: Material uses −0.25 px at 57 px (≈ −0.005 em); up to about −0.02 em on very large lines is common practice. Headings at normal sizes and body text stay at 0. Google Fonts: negative tracking only at very large sizes.
- **All-caps labels** (eyebrows, tags, small buttons): add positive tracking, about +0.05 em; never set running text in capitals.
- **Line length:** about 45–75 characters (typographic convention); WCAG 1.4.8 (AAA) caps it at 80. On the web ≈ `max-width: 36em` at 16 px.
- **Italics** are fine in English for emphasis and titles; never on Japanese text.
- Weights: 400 body, 600–700 headings; 800–900 only for large display lines.

Columns: one below 768, two from 768, three or four only from the optional 1024 breakpoint. CTA buttons full width on phones.

## Screen sizes, breakpoints and widths

Researched 2026-10-15 (sources in `SOURCES.md`, section "Screen sizes"). All sizes in CSS px. Japanese data and practice: `japan.md`.

Two different widths: the **design width** (the artboard in Figma) and the **content width** (the `max-width` of text and grid; backgrounds still run edge to edge).

| What | Our default | Why |
|---|---|---|
| Phone design width | **390** (375 is fine when the designer delivers it) | 390 = iPhone 12/13/14 and 16e; 393 = 14 Pro, 15, 16; 375 = SE and mini. Newest iPhones are 402 (16 Pro, 17, 17 Pro), 420 (Air), 430–440 (Plus, Pro Max) |
| Phone test widths | **360, 390, 430** | 360 = smallest common Android (Galaxy S and A series); 412 = Pixel and larger Galaxy models; 430/440 = large iPhones |
| Tablet | no separate design; the layout stretches between phone and desktop | DADS uses one breakpoint; most Japanese agencies design PC + SP only |
| Desktop design width | **1440** (1366 is fine) | Figma's Desktop preset is 1440 × 1024 (check your panel; Figma updates presets) |
| Desktop test widths | **1280, 1366, 1536, 1920** | 1280 = a 1920 screen at 150 % Windows scaling, 1536 = at 125 %; both are common |
| Breakpoint | **one, at 768**: phone below, desktop from `@media (min-width: 768px)`. Add 1024 only where a 3–4 column grid needs it | DADS: one breakpoint at 768 by default, more when needed |
| Content container | **1120** content + side padding; never more than 1200 | leaves 80 px each side on a 1280 screen (Bootstrap's comparable container is its 1140 xl; its 1320 applies only from 1400) |
| Side padding | **16** on phones (20 also fine), **32** from 768 | our choice, taken from the DADS gutter (twice the body text = 32 at 16 px); DADS sets no margin value |
| Reading column (articles) | Japanese: `max-width: 41em` (≈ 40 characters, ≈ 656 at 16 px); see `japan.md`. English: about 65–75 characters (practice) | JLReq: horizontal lines at most about 40 characters |
| Photos and banners | file width = **2 × the slot** (a 390 slot → 780 file, a 1120 slot → 2240); 3× is not worth the bytes | most iPhones are 3× (XR, 11 and SE are 2×), Android 2.6–3.5×; above 2× the visible gain is small (Jake Archibald 2021); web.dev examples use 1×/2×. WordPress `srcset` does this when the image sizes exist (`../wp-performance.md`) |

Theme and framework breakpoints (use the theme's own, do not fight it):
- **Flatsome:** 549 / 849 (`../flatsome/README.md`).
- **Bootstrap 5.3:** 576 / 768 / 992 / 1200 / 1400; containers 540 / 720 / 960 / 1140 / 1320.
- **Tailwind v4:** 640 / 768 / 1024 / 1280 / 1536 (five tiers, not Bootstrap's six); `container` = 100 % width capped at the current breakpoint, no centring or padding by default.

## Navigation, surfaces and motion (checked 2026-10-15)

Checked against WCAG 2.2, DADS components and foundations, Material 3 tokens, NN/g, MDN and web.dev (`SOURCES.md`, section "UX and surfaces"). Values marked practice have no standard behind them. Japanese conventions: `japan.md`.

**Header and navigation**
- Header height is free (practice: about 64–72 desktop, 56–64 phone; Material's top bar is 64). A sticky header is fine: set `scroll-padding-top` (and `scroll-padding-bottom` for a fixed bottom bar) to their heights so a focused field or anchor target is never entirely hidden under them (WCAG 2.4.11, AA; partly covered still passes AA). A blurred header (`backdrop-filter`) works in all current browsers.
- Menu button: a visible label next to or under the icon (「メニュー」/ MENU; DADS requires it); tap area 44 × 44 (WCAG AAA and Apple), never under 24 × 24 (AA).
- Mega menus and drop-downs open on **click or tap and on keyboard focus**, never on hover alone (DADS). If hover is added, wait 0.3–0.5 s before opening and keep it open 0.5 s after the pointer leaves (NN/g). Show levels 1–2 in one panel; avoid menus that fly out sideways from other menus.
- Breadcrumbs go **between the header and the page title** (NN/g, DADS), current page not linked, `BreadcrumbList` structured data (Google sets no position). A second copy above the footer is optional (DADS uses it when the phone trail scrolls sideways).
- Sticky header and sticky bottom bar together take a lot of a zoomed or small screen (WCAG 1.4.10 reflow): keep both short and let one of them scroll away on small screens (Japan keeps both by convention: keep the header short or hide it on scroll-down). A bottom bar needs `padding-bottom: env(safe-area-inset-bottom)` (and `viewport-fit=cover`) on iPhones. Thumb reach (Hoober 2013): the top of the screen is the hardest to reach; bottom corners are easy to reach but less accurate, so make bottom buttons large.

**Colour and surfaces**
- Text colours (contrast on white): near-black #1A1A1A (17.4:1, DADS Solid Gray 900) or #000 (DADS uses pure black; "never pure black" is taste, not a rule); secondary #595959–#666 (7.0–5.7:1); **muted captions no lighter than #767676** (4.5:1). #888 and #86868B fail (3.5:1). On off-white backgrounds re-check: #6E6E73 drops to about 4.7:1.
- Off-white section backgrounds alternated with white separate sections without lines (practice; e.g. #F8F8FB, #F5F5F7, warm #FAF9F6).
- Borders: decorative dividers and card edges may be faint (#E5E5E5, `rgba(0,0,0,.08)`, 1.3:1). **Input fields and icon-only buttons need a 3:1 boundary** (#949494 or darker; WCAG 1.4.11).
- Shadows: pick **one elevation scale** and use only its steps (DADS `--elevation-1…8`, or Material levels 1–5). The "never above 6 % opacity" rule some articles give is a style preference; DADS and Material use stronger two-layer shadows. Flat cards separated by background colour are a valid alternative.
- Corner radius: one scale, e.g. DADS 0 / 8 / 16 / 32 / full; smaller elements get smaller radii. Nested corners: inner radius = outer radius − padding (24 − 16 = 8) keeps curves parallel (practice).
- Accent colour used sparingly (practice: about 10 % of the screen, the "60-30-10" rule from interior design).

**Images**
- Card thumbnails in a row share one ratio: `aspect-ratio: 16 / 9` (or 4 / 3, 3 / 2, 1 / 1, 4 / 5) with `object-fit: cover`.
- Text over a photo needs 4.5:1 against the busiest part of the image (WCAG 1.4.3, failure F83): add a scrim or put the text in a solid box.

**Motion**
- Ease-out for things that enter: Material standard `cubic-bezier(0.2, 0, 0, 1)` or emphasized-decelerate `cubic-bezier(0.05, 0.7, 0.1, 1)`; `cubic-bezier(0.22, 1, 0.36, 1)` (easeOutQuint) is also fine. Linear only for short fades and continuous loops.
- Durations: hover and small UI changes **150–250 ms**; panels and transitions up to **400 ms** (NN/g 100–400 ms; Material medium 250–400); a slow image zoom on hover may take 500–700 ms (practice). Scroll reveals at most about **600 ms**, opacity first, a short 16–24 px move at most; 800–1000 ms reveals feel slow (NN/g: users do not want to wait for animation).
- `@media (prefers-reduced-motion: reduce)` turns off movement triggered by scrolling or clicks (WCAG 2.3.3, AAA; opacity-only fades are not motion under it and may stay). The AA duty is 2.2.2: anything that moves for more than 5 s (sliders, tickers) can be paused.
- **Never hide the hero or main heading in a scroll reveal**: elements at opacity 0 do not count as the LCP element and stay invisible if the script fails. Start reveals only when a `js` class is present.

**Consistency:** one radius scale, one shadow or border style, one accent colour, one grid (DADS: 12 columns, gutter twice the body text size). Edges of headings, text and cards line up on the same columns.

## Content blocks and page order (checked 2026-10-15)

Checked against NN/g, WCAG 2.2 and Baymard (`SOURCES.md`, section "Page structure"). The patterns are house style; the rules marked WCAG or NN/g are not.

- **Section intro:** eyebrow label (optional, not a heading tag, `japan.md`) → H2 (one benefit or topic, 1–2 lines) → a lead of 2–3 lines (about 40–60 English words, 80–120 Japanese characters) → the content. Put a line of text between an H2 and the first H3 cards so the section says what follows (house style).
- **Three or more parallel points** read better as cards than as consecutive paragraphs. Card order: image or icon/number → H3 → 2–3 lines → link.
- **Link text says where it goes** ("See pricing", 「料金を見る」), or the card heading is the link. Not a row of "Learn more →" links: NN/g finds them ambiguous and screen-reader users hear the same label many times (WCAG 2.4.4).
- **Alternating image/text rows (zigzag):** only with images that carry information, and 2–3 rows at most; NN/g eye-tracking found zigzag less predictable than aligned rows. On a 12-column grid: text 5 columns, 1 empty, image 6. On phones every row stacks the same way (image → heading → text). **Source order = visual order:** write the HTML in the reading order and mirror the desktop rows with CSS only where the meaning does not change (WCAG 1.3.2, 2.4.3).
- **Carousels:** no auto-advancing hero sliders (NN/g: later slides are rarely seen; Baymard: 46 % of homepage carousels have usability problems). One strong hero instead; if a slider stays, it must have a pause button (WCAG 2.2.2).
- **Signalling more content below the hero:** let the next section show at the bottom of the first screen. A "SCROLL ↓" cue has no measured effect (Viget eye-tracking); it is decoration.
- **Home page order (practice):** hero → proof (client logos, numbers; Japanese sites: お知らせ, `japan.md`) → what we do → services or features → works/cases → process or key numbers → FAQ (5–7 questions, answers in the HTML) → conversion band before the footer.

## Links, buttons, images

- Link text says where it goes ("See pricing", 「学費を見る」), not "Click here" / 「こちら」 repeated.
- Buttons for actions, links for navigation. Same-site links relative (`/contact/`). External links may open in a new tab; then say so (icon or text).
- Every meaningful image has `alt` text in context; decorative images `alt=""`. No text baked into images. Right size for the slot, WebP, width and height set (see `../wp-performance.md`).

## Wireframe patterns

Home (full order and the zigzag limit: "Content blocks and page order" above): sticky header (logo, 5–7 items, one CTA) → hero (H1 + one line + CTA + visual) → trust bar (logos, numbers, certifications) → three benefits → feature sections alternating image/text → voices → full-width CTA → footer (nav, contact, legal).

Service page: short hero with H1 and breadcrumb → definition block in the first 150 characters/words → benefits → detail sections → proof → FAQ (5+) → CTA.

Article: H1, author, date → hero image (not lazy) → intro with the answer → H2/H3 → author box (E-E-A-T) → related posts.

Landing page: logo-only header → hero with one CTA → benefits → how it works (3 steps) → proof → final CTA → minimal footer (legal only). Full LP guidance, Japanese and global: `../marketing/landing-pages.md`.

## Components (spec level)

- **Button:** height 44–48 px, 16 px text, weight 600, padding 12 × 32, radius from the design tokens, hover = slight opacity or lift, visible focus ring.
- **Card:** image 16:9 or 4:3 (`aspect-ratio` + `object-fit: cover`), optional tag, H3, 2–3 lines, link; 1 px border or one elevation step, hover goes one step up.
- **Testimonial:** quote 2–4 lines, 48 px avatar, name and role, surface background.
- **FAQ accordion:** question as H3, toggle icon on the right, border between items; answers present in the HTML (not loaded on click) so search engines see them.
- **Stat block:** 48 px icon, big number, one line; centred on phones.

Design values (colours, fonts, radii) always come from the project's design tokens: `design-tokens.md`.

## International visitors

- Sites aimed at EU/UK visitors (pages, prices or shipping for them) or tracking them: tracking scripts and non-essential cookies need consent (GDPR; `../legal/japan.md`). Never add tracking, chat widgets or embeds on your own; a person decides and updates the privacy policy.
- Dates, prices and phone numbers in international format for a foreign audience: "September 26, 2026", "¥11,000 (tax incl.)", "+81-3-1234-5678".
