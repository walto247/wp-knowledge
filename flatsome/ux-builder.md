# UX Builder shortcodes (Flatsome 3.20.11)

Status: **verified 2026-10-11** against the theme's own files (`inc/shortcodes/*.php` and `inc/builder/shortcodes/*.php` of Flatsome 3.20.11, read from a staging server, read-only). Attribute names and defaults below are the real ones; values shown as `''` mean "empty unless set". 3.20.11 is the public release (2026-09-22) and the build on our sites. **Always prefer what the page already uses.** Breakpoints: `__sm` = up to 549 px, `__md` = 550–849 px.

## Element names (all registered shortcodes)

Layout: `section`, `section_inner`, `row`, `row_inner`, `col`, `col_inner`, `col_grid`, `ux_banner`, `ux_banner_grid`, `ux_stack`, `ux_stack_inner`, `gap`, `divider`, `title`, `scroll_to`, `block`, `ux_html`, `ux_text`.
Content: `button`, `header_button`, `ux_image`, `ux_image_box`, `ux_gallery`, `ux_slider`, `ux_video`, `video_button`, `featured_box`, `message_box`, `testimonial`, `team_member`, `accordion` + `accordion-item`, `tabgroup` + `tab`, `tabgroup_vertical`, `ux_countdown`, `ux_hotspot`, `ux_lottie`, `ux_price_table`, `page_header`, `lightbox`, `map`, `search`, `share`, `follow`, `logo`, `ux_menu` / `ux_menu_link` / `ux_menu_title`, `ux_nav`, `ux_pages`, `ux_sidebar`, `blog_posts`, `ux_portfolio`, `featured_items_grid` / `_slider`, `ux_instagram_feed`, `ux_payment_icons`, `ux_current_year`, `site_url`.
WooCommerce: `ux_products`, `ux_products_list`, `ux_product_categories`, `ux_product_categories_grid`, `ux_featured_products`, `ux_latest_products`, `ux_sale_products`, `ux_bestseller_products`, `ux_custom_products`, `ux_product_flip`, `product_lookbook`, and the custom-product-page parts `ux_product_title`, `ux_product_price`, `ux_product_gallery`, `ux_product_add_to_cart`, `ux_product_description`, `ux_product_excerpt`, `ux_product_meta`, `ux_product_rating`, `ux_product_tabs`, `ux_product_related`, `ux_product_upsell`, `ux_product_breadcrumbs`, `ux_product_next_prev_nav`, `ux_product_hook`.

## Attributes common to most elements

`class`, `visibility` (`hide-for-small`, `hide-for-medium`, `show-for-small`, `show-for-medium`), `animate`, `depth` / `depth_hover` (0–5 shadow), `border…` group (`border`, `border_color`, `border_style`, `border_radius`, `border_margin`, `border_hover`), and responsive twins `…__sm` / `…__md` on paddings, margins, heights, widths, positions, text sizes. Phone = `small`, tablet = `medium`.

## Structure

```
[section bg_color="#F8F9FA" padding="60px" padding__sm="30px"]
  [row v_align="middle" h_align="center"]
    [col span="6" span__sm="12" span__md="6"]
      [ux_text] … HTML … [/ux_text]
    [/col]
  [/row]
[/section]
```

- **section:** `padding='30px'` (default), `padding__sm`, `padding__md`, `height`, `margin`, `bg` (media ID), `bg_size`, `bg_color`, `bg_overlay` (+ `__sm`/`__md`), `bg_pos`, `parallax`, `effect`, `dark='false'` (white text), `mask`, `sticky`, `loading`, `scroll_for_more`, video (`video_mp4|ogg|webm`, `youtube`, `video_sound='false'`, `video_loop='true'`, `video_visibility='hide-for-medium'`), shape dividers (`divider_top`, `divider`, each with `_height='150px'`, `_width='100'`, `_fill`, `_flip`, `_to_front`).
- **row:** `style`, `col_style` (`divide`, `solid`, `collapse`…), `width` (`full-width`, `custom`), `custom_width`, `v_align`, `h_align`, `padding`, `col_bg`, `col_bg_radius`, `depth`, `border_color`.
- **col:** `span='12'` (1–12), `span__md` (defaults to `span`), `span__sm` (defaults to `12`), `padding` / `margin` / `max_width` with `__sm`/`__md`, `align`, `color` (`light` for white text), `divider`, `sticky`, `sticky_mode`, `parallax`, `force_first` (put this column first on phones), `hover`, `tooltip`, `bg`, `bg_color`, `bg_radius`, `depth`, border group.

## Banner and text box

```
[ux_banner height="500px" height__sm="400px" bg="MEDIA_ID" bg_overlay="rgba(0,0,0,.4)" bg_pos="center center"]
  [text_box width="60" width__sm="90" position_x="50" position_y="50" text_align="center"]
    <h1>見出し</h1><p>説明文</p>
    [button text="お問い合わせ" link="/contact/" color="primary" size="large"]
  [/text_box]
[/ux_banner]
```

- **ux_banner:** `height` (+`__sm`/`__md`; old `mob_height` / `tablet_height` still accepted), `bg` (media ID), `bg_size='large'`, `bg_color`, `bg_overlay` (+`__sm`/`__md`), `bg_pos`, `parallax`, `parallax_style`, `effect`, `hover`, `link` + `target` + `rel` + `link_aria_label`, `animation='fadeIn'`, `text_width='60%'`, `text_align='center'`, `text_color='light'`, `text_pos='center'`, `text_bg`, `padding`, `sticky`, `container_width`, video and shape-divider groups as on `section`, `alt`.
- **text_box:** `position_x='50'`, `position_y='50'` (+`__sm`/`__md`), `width='60'` (+`__sm`/`__md`), `height`, `scale='100'`, `text_align='center'`, `text_color='light'`, `bg`, `padding`, `margin`, `radius`, `rotate`, `res_text='true'` (responsive text), `parallax`, `animate`, `style`, border/depth groups.

## Common elements, real attribute names

```
[button text="Label" link="/path/" color="primary|secondary|alert|success|white" style="|outline|link|underline|shade|bevel|gloss" size="xxsmall|xsmall|smaller|small||large|larger|xlarge|xxlarge" radius="99" expand="true" icon="icon-angle-right" icon_pos="left"]
[ux_image id="MEDIA_ID" image_size="large" width="80" lightbox="true" lightbox_image_size="large" link="URL" caption="…" image_hover="zoom" height=""]
[ux_gallery ids="1,2,3,4" columns="4" columns__sm="2" col_spacing="small" lightbox="true" style="overlay" image_size="medium" image_height="75%" type="slider|grid|masonry" image_hover="…"]
[gap height="30px" height__sm="15px"]
[divider width="60px" height="3px" margin="40px" align="center" color="#…"]
[title text="セクション見出し" tag_name="h2" style="normal|center|bold|bold-center" size="100" color="#…" margin_top="" margin_bottom="" sub_text="" link_text="" link=""]
[ux_image_box img="MEDIA_ID" style="vertical|overlay|…" image_width="80" text_pos="bottom" text_align="center"] <h3>Title</h3><p>Text</p> [/ux_image_box]
[featured_box img="MEDIA_ID" img_width="60" pos="top|left|center" title="…" link="…"] text [/featured_box]
[testimonial name="お名前" company="役職・会社" image="MEDIA_ID" image_width="80" stars="5" pos="left" font_size="" text_align=""] 「引用」 [/testimonial]
[message_box bg_color="#…" text_color="dark|light" padding="15"] … [/message_box]
[accordion auto_open="" open="" title="" faq_schema="true"] [accordion-item title="質問" anchor=""] 回答 [/accordion-item] [/accordion]
[tabgroup style="line|outline|pills|vertical|…" align="left" nav_style="uppercase" nav_size="normal"] [tab title="タブ1" anchor=""] 内容 [/tab] [/tabgroup]
[ux_video url="https://www.youtube.com/watch?v=…" height="56.25%"]
[ux_text font_size="1.2" font_size__sm="1" line_height="1.8" text_align="center" text_align__sm="left" text_color="#…"] … [/ux_text]
[ux_slider timer="6000" bullets="true" arrows="true" auto_slide="true" auto_height="true" columns="1" nav_style="circle" nav_color="light"] slides… [/ux_slider]
[block id="block-slug"]
```

Facts that corrected the old notes:
- **`style="primary"` is wrong.** The button's colour is `color="primary|secondary|alert|success|white"`; `style` is the shape (`outline`, `link`, `underline`, `shade`, `bevel`, `gloss`, or empty for filled). `size` values are `xxsmall … xxlarge`; "normal" is simply no `size`.
- Accordion item is **`[accordion-item]`**, default title "Accordion Panel"; `[accordion faq_schema="true"]` prints FAQ structured data (the Google rich result for it is gone since May 2026, the markup is harmless).
- `[testimonial]` uses `image=` and `company=`, not `img=` / `sub=`. `[ux_image_box]` uses `img=`. `[title]` default tag is `h3`.
- `[divider]` has `width`, `height`, `margin`, `align`, `color` only. `[gap]` default is 30 px.
- `image_height` is an aspect ratio: `75%` = 4:3, `56.25%` = 16:9, `100%` = square.
- Images are referenced by media ID. The hero banner background is `bg="ID"`.

## Helper classes present in flatsome.css

Text: `text-center`, `uppercase`, `is-small`, `is-large`, `is-xlarge`, `is-xxlarge`, `dark` (white text on dark). Spacing: only `mt-0`, `mb-0`, `ml-0`, `mr-0`, `pt-0`, `pb-0` and the `-half` variants (`mb-half`, `pb-half` …). **There is no `.m-8 / .mt-16` scale**; use element `padding` / `margin` attributes or `[gap]`. Backgrounds: `bg-primary`, `bg-secondary`. Visibility classes `hide-for-small`, `hide-for-medium`, `show-for-small`, `show-for-medium` match the `visibility` attribute.

## Lazy loading

Flatsome has its own lazy-load options (`lazy_load_images`, `lazy_load_backgrounds`, `lazy_load_icons`, `lazy_load_google_fonts`, `lazy_load_scripts` in Theme Options → Performance) and honours the `skip-lazy` class on an image. With WP Rocket, keep Flatsome's image lazy load off so the two do not fight (`../wp-plugins/wp-rocket.md`).

## Landing page order

Hero (headline + one CTA) → trust (logos, numbers, awards) → problem → solution (image + text) → features (3 columns) → voices or case studies → price or offer → FAQ → final CTA banner. One purpose per section.

## Before saving

Count opening and closing tags of `section`, `row`, `col`, `ux_banner`, `text_box`, `accordion`, `tabgroup`. Every column has `span__sm`. Nothing wider than the screen on phones. Links relative (`/contact/`). Media by ID. Check at 360 and 390 px (Japan: also 375 and 414).
