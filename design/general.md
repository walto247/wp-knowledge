# Design fundamentals (any site)

Status: merged 2026-10-11 from `global-web`, `ux-ui` and `wireframes` (dashboard skills). Not yet verified against WCAG 2.2 / current references (pass 2). For Japanese sites read `japan.md` as well; where they differ, `japan.md` wins.

## Owner's rules (stand above everything else)

- **The visitor comes first, not the design.** Every choice is judged by how little stress it causes the person using the page (owner rule, 2026-10-09).
- **Follow the designer's render exactly** when a site is built from a design: match it, never simplify, add or recolour. Flag problems; the owner decides (owner rule, 2026-10-10).
- **Commit to one deliberate direction.** No generic "AI look": purple gradients, identical card grids, stock hero + three icons. Decide the impression first (calm, dense, warm, premium…) and let every element serve it.

## Page structure

- **One page, one goal.** Know what the visitor should do (call, request a brochure, buy, read) before touching a page; make that action obvious at the top and the end.
- Visual order = importance: headline → key benefit → proof → action. Never start with history or greetings.
- Scannable: clear H2/H3, short paragraphs, lists, white space. People skim.
- **Consistency:** reuse the site's colours, fonts, spacing, buttons and section styles. A new colour or font size needs a reason; a page must look like the rest of the site.
- Phone first: check every change at 375 px. No sideways scrolling; buttons reachable with a thumb; text readable without zoom.

Typical page goals: home = trust and the next step; service page = explain value, convert to an inquiry; blog post = teach, build authority, link inward; contact = remove friction; landing page = one CTA, nothing else.

## Visual hierarchy and spacing

1. Most important: largest, highest contrast, top or left.
2. Secondary: medium weight, secondary colour.
3. Supporting: smaller, muted.
4. Every element has one role; nothing competes.

Spacing scale (use the scale, never arbitrary values): 4 / 8 / 16 / 24 / 32 / 48 / 64 / 96 px.
Sections: 48 px apart on phones, 64–96 px on desktop. Max content width about 1120–1200 px, side padding 16–24 px. 8 px grid.

Columns: one on phones, at most two on tablets, up to four on desktop. CTA buttons full width on phones.

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
