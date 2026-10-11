# UX Builder shortcodes

Status: merged 2026-10-11 from both Flatsome skill versions. **Element attributes still unverified** (the official docs have no element reference; next step is reading `inc/shortcodes/` on a Flatsome server); ⚠ marks attributes seen in only one source. Verified: `[accordion-item]` hyphen form and the `hide-for-medium` class on live sites; breakpoints 549/849 px. **Always prefer what the page already uses.**

## Structure

```
[section bg_color="#F8F9FA" padding="60px"]      ← outer container (or [ux_banner])
  [row v_align="middle" h_align="center"]        ← row; col_style="divide" for divided columns
    [col span="6" span__sm="12" span__md="6"]    ← column: 1–12 of 12; __sm = phone, __md = tablet
      [ux_text] … HTML … [/ux_text]               ← element(s)
    [/col]
  [/row]
[/section]
```

Responsive attributes (`__sm` = up to 549 px, `__md` = 550–849 px): add them to most attributes: `span__sm="12"`, `text_align__sm="center"`, `padding__sm="30px"`, `width__sm="90"`, `height__sm="400px"`, `columns__sm="2"`. Hide decorative elements on phones with `visibility="hide-for-small"` (class names `hide-for-small`, `show-for-small`, `hide-for-medium` also exist). ⚠ `hide__sm="true"` appears in one source only.

Mobile spans: span 3 → `span__sm="6"` (two per row) or `"12"`; span 4 → `"12"` or `"6"`; span 6 and 8 → `"12"`.

## Common elements

```
[ux_banner height="500px" height__sm="400px" bg="MEDIA_ID" bg_overlay="rgba(0,0,0,.4)" bg_pos="center center"]
  [text_box width="60" width__sm="90" position_x="50" position_y="50" text_align="center"]
    <h1>見出し</h1>
    <p>説明文</p>
    [button text="お問い合わせ" link="/contact/" style="primary" size="large"]
  [/text_box]
[/ux_banner]

[button text="Label" link="/path/" style="primary|secondary|outline|white|outline white|link|underline" size="small|normal|large|xlarge" radius="99"]
[ux_image id="MEDIA_ID" image_size="large|medium|thumbnail" width="80" lightbox="true" link="URL"]
[ux_gallery ids="1,2,3,4" columns="4" columns__sm="2" lightbox="true" image_height="75%" image_size="medium"]
[gap height="30px"]
[divider width="60px" height="3px" margin="40px"]
[title text="セクション見出し" tag_name="h2" style="center"]
[ux_image_box img="MEDIA_ID" style="vertical" image_width="80" text_align="center"] <h3>Title</h3><p>Text</p> [/ux_image_box]
[ux_testimonial name="お名前" sub="役職・会社" img="MEDIA_ID"] 「引用」 [/ux_testimonial]
[accordion] [accordion-item title="質問"] 回答 [/accordion-item] [/accordion]   ← hyphen (confirmed live); copy the site's anyway
[tabgroup] [tab title="タブ1"] 内容 [/tab] [/tabgroup]
[ux_video url="https://www.youtube.com/watch?v=…" height="56.25%"]
[block id="block-slug"]
```

`image_height` is an aspect ratio: `75%` = 4:3, `56.25%` = 16:9, `100%` = square. `[ux_gallery]` handles lightbox, lazy load and responsive columns itself; prefer it over hand-written HTML grids.

## Section patterns

Hero, text left and image right:
```
[section padding="large"]
  [row v_align="middle"]
    [col span="6" span__sm="12"] <h1>Headline</h1><p class="is-large">…</p> [button …] [/col]
    [col span="6" span__sm="12"] [ux_image id="…" image_size="large"] [/col]
  [/row]
[/section]
```

Three features: one `[row h_align="center"]` with three `[col span="4" span__sm="12" align="center"]`, each icon + `<h3>` + `<p>`.

Alternating text and image: repeat two-column sections, swapping the column order.

Full CTA banner: `[ux_banner height="300px" bg_color="PRIMARY" text_align="center"]` with a `[text_box]` holding `<h2 class="dark">` (white text on dark), one line and one `[button style="white"]`.

Callout inside content: `[ux_text_box text_align="center" bg_color="#F8F9FA" padding="20px" border="1px solid #E5E7EB" border_radius="8px"] … [/ux_text_box]` ⚠ (one source).

## Landing page order

Hero (headline + one CTA) → trust (logos, numbers, awards) → problem → solution (image + text) → features (3 columns) → voices or case studies → price or offer → FAQ → final CTA banner. One purpose per section.

## Helper classes in content

Text: `text-center`, `text-left`, `uppercase`, `is-large`, `is-small`, `dark` (white text on a dark background). Spacing: use element attributes (`padding`, `margin`, `[gap]`) rather than new CSS. ⚠ A `.m-8 / .mt-16 / .bg-primary / .text-large` utility set appears in one source only; confirm against the theme before relying on it.
