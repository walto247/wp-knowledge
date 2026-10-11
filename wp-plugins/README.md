# Standard plugins on our WordPress sites

Status: merged 2026-10-11 from the dashboard `wp-plugins` skill, tool-specific wording removed. Unverified against current plugin versions and docs (pass 2).

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
