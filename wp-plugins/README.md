# Standard plugins on our WordPress sites

Status: merged 2026-10-11; **checked 2026-10-11** where the vendor documents it (WPForms shortcode, WP Mail SMTP Do Not Send, WP Rocket exclusions, WPML slug settings, UpdraftPlus folder, Yoast meta keys via community sources). Wordfence and ACF notes are practice. Sources: `SOURCES.md`.

| Plugin | File | Routine work that is safe | Needs a person (settings, secrets, data) |
|---|---|---|---|
| Yoast SEO | `yoast.md` | a page's SEO title, description, focus keyphrase | site-wide templates, schema settings, sitemaps, redirects, noindex |
| WP Rocket | `wp-rocket.md` | clear the cache after a change | every setting |
| WPForms | `wpforms.md` | place a form shortcode, style it with CSS | fields, notifications, confirmations, entries |
| Wordfence | `wordfence.md` | nothing (read-only by design) | every setting, unblocking, scans |
| UpdraftPlus | `updraftplus.md` | nothing | backups, restores, settings |
| WP Mail SMTP | `wp-mail-smtp.md` | nothing | every setting (holds passwords or tokens) |
| WPML | `wpml.md` | edit one language version at a time | create or link translations, language settings |
| ACF | `acf.md` | read field data shown on a page | fields and field groups |

## Rules for every plugin

- Plugin **settings** are a person's decision. When a request needs one, name the setting and the menu path and ask.
- Never install, update, activate, deactivate or delete plugins as part of a content task. Report available updates; a person applies them on staging first, then production, after a backup (`../wp-maintenance.md`).
- Never read or repeat settings that hold passwords, API keys, licence keys or tokens.
- A plugin that seems broken: collect facts (versions, the PHP error log) and report; no fixes inside plugin files.

## Versions and advisories (checked 2026-10-17)

Keep at least these versions (security fixes in Aug–Oct 2026; check Patchstack or Wordfence Intelligence before quoting a CVE to a client):

| Plugin | Keep at least | Note |
|---|---|---|
| Yoast SEO | 28.7 (2026-10-13) | 28.6–28.7 add WordPress Abilities so AI agents can read and update titles and descriptions |
| WP Rocket | 3.23.5.1 (2026-10-02) | fixes for exposed config backups, stored XSS and access control |
| WPForms | 2.0.2.2 (2026-10-06) | several unauthenticated issues fixed in Sep 2026 (shortcode execution, Stripe refund, XSS) |
| Wordfence | 9.0.2 (2026-09-30) | passkey login since 9.0.0 |
| UpdraftPlus | 1.26.11 (2026-10-16) | three security releases in three days |
| WP Mail SMTP | 4.10.2 (2026-10-08) | new Email Detective tool next to Email Test and Email Log |
| WPML | 5.0.x (2026-09-13) | admin redesign; see `wpml.md` |
| ACF / Secure Custom Fields | 6.8.10 / 6.9.6 | two different plugins; see `acf.md` |
| WooCommerce | 11.2.1 (2026-10-09) | security releases 11.1.1, 11.1.2; Flatsome needs 3.20.10+ for 11.1 |
