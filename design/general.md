# Design fundamentals (any site)

Status: merged 2026-10-11 from `global-web`, `ux-ui` and `wireframes` (dashboard skills). Not yet verified against WCAG 2.2 / current references (pass 2), except "Screen sizes, breakpoints and widths", researched 2026-10-15. For Japanese sites read `japan.md` as well; where they differ, `japan.md` wins.

## Owner's rules (stand above everything else)

- **The visitor comes first, not the design.** Every choice is judged by how little stress it causes the person using the page (owner rule, 2026-10-09).
- **Follow the designer's render exactly** when a site is built from a design: match it, never simplify, add or recolour. Flag problems; the owner decides (owner rule, 2026-10-10).
- **Commit to one deliberate direction.** No generic "AI look": purple gradients, identical card grids, stock hero + three icons. Decide the impression first (calm, dense, warm, premium…) and let every element serve it.

## Page structure

- **One page, one goal.** Know what the visitor should do (call, request a brochure, buy, read) before touching a page; make that action obvious at the top and the end.
- Visual order = importance: headline → key benefit → proof → action. Never start with history or greetings.
- Scannable: clear H2/H3, short paragraphs, lists, white space. People skim.
- **Consistency:** reuse the site's colours, fonts, spacing, buttons and section styles. A new colour or font size needs a reason; a page must look like the rest of the site.
- Phone first: check every change at 360 and 390 px (all test widths: "Screen sizes" below). No sideways scrolling; buttons reachable with a thumb; text readable without zoom.

Typical page goals: home = trust and the next step; service page = explain value, convert to an inquiry; blog post = teach, build authority, link inward; contact = remove friction; landing page = one CTA, nothing else.

## Visual hierarchy and spacing

1. Most important: largest, highest contrast, top or left.
2. Secondary: medium weight, secondary colour.
3. Supporting: smaller, muted.
4. Every element has one role; nothing competes.

Spacing scale (use the scale, never arbitrary values): 4 / 8 / 16 / 24 / 32 / 48 / 64 / 96 px.
Sections: 48 px apart on phones, 64–96 px on desktop. Content width and side padding: "Screen sizes" below. 8 px grid.

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

## Links, buttons, images

- Link text says where it goes ("See pricing", 「学費を見る」), not "Click here" / 「こちら」 repeated.
- Buttons for actions, links for navigation. Same-site links relative (`/contact/`). External links may open in a new tab; then say so (icon or text).
- Every meaningful image has `alt` text in context; decorative images `alt=""`. No text baked into images. Right size for the slot, WebP, width and height set (see `../wp-performance.md`).

## Wireframe patterns

Home: sticky header (logo, 5–7 items, one CTA) → hero (H1 + one line + CTA + visual) → trust bar (logos, numbers, certifications) → three benefits → feature sections alternating image/text → voices → full-width CTA → footer (nav, contact, legal).

Service page: short hero with H1 and breadcrumb → definition block in the first 150 characters/words → benefits → detail sections → proof → FAQ (5+) → CTA.

Article: H1, author, date → hero image (not lazy) → intro with the answer → H2/H3 → author box (E-E-A-T) → related posts.

Landing page: logo-only header → hero with one CTA → benefits → how it works (3 steps) → proof → final CTA → minimal footer (legal only).

## Components (spec level)

- **Button:** height 44–48 px, 16 px text, weight 600, padding 12 × 32, radius from the design tokens, hover = slight opacity or lift, visible focus ring.
- **Card:** image 16:9 or 4:3, optional tag, H3, 2–3 lines, link; 1 px border, subtle shadow, hover lifts the shadow.
- **Testimonial:** quote 2–4 lines, 48 px avatar, name and role, surface background.
- **FAQ accordion:** question as H3, toggle icon on the right, border between items; answers present in the HTML (not loaded on click) so search engines see them.
- **Stat block:** 48 px icon, big number, one line; centred on phones.

Design values (colours, fonts, radii) always come from the project's design tokens: `design-tokens.md`.

## International visitors

- EU/UK visitors: tracking scripts and non-essential cookies need consent. Never add tracking, chat widgets or embeds on your own; a person decides and updates the privacy policy.
- Dates, prices and phone numbers in international format for a foreign audience: "September 26, 2026", "¥11,000 (tax incl.)", "+81-3-1234-5678".
