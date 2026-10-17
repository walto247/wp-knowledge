# Advanced Custom Fields (ACF)

Status: checked 2026-10-17 on wordpress.org. Two different plugins exist: **Advanced Custom Fields (ACF®)** by WP Engine (6.8.10, 2026-09-10; 6.8.7 and 6.8.10 were security releases) and **Secure Custom Fields** by WordPress.org (6.9.6, 2026-10-16; installing it deactivates ACF / ACF PRO). Keep whichever the site already has, updated; never switch on your own. Field-handling notes below are practice.

- ACF stores extra fields (a staff member's title, an event date) as post meta; theme templates print them. They are not in the post content.
- Text that is on the page but not in the content is often an ACF field or a theme setting: say so, and point to the fields below the editor or the ACF field group.
- Never edit field groups or the templates that print them as part of a content task; a developer does that, with review.
