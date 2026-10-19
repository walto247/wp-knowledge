# Site maintenance: health check and upkeep

Status: merged 2026-10-11 from the dashboard `wp-maintenance` skill; version facts verified 2026-10-11 (php.net, WordPress hosting handbook); the routine is practice. Plugins: `wp-plugins/`. Security: `wp-security.md`.

## Health check routine (read-only)

1. Versions: WordPress, PHP, theme and child theme, plugins with status (active, inactive, must-use).
2. Updates available: core, plugins, themes.
3. PHP errors: `error_log` in the WordPress folder and `wp-admin/`, `wp-content/debug.log` (they may not exist). Only the tail matters: `Fatal error`, repeated warnings, the plugin or theme named in the path, the dates.
4. Report in the format below. Change nothing during a health check.

## What to flag

| Finding | Why | Suggest |
|---|---|---|
| Plugin or theme update available | security fixes | update on staging, check key pages and forms, then production after a backup |
| WordPress core update | security | same; minor versions (x.y.**z**) are low risk |
| PHP 8.1 or older (end of life); 8.2 after 2026-12-31 | no security fixes | plan the move to 8.3+ with the host, tested on staging (table in `wp-security.md`) |
| Inactive plugins | attack surface, clutter | delete if not needed (a person decides) |
| Inactive themes beyond one default | same | keep one default theme as a fallback |
| Fatal errors in the log | something is broken | name the file, plugin and page |
| Plugin not updated for years | possibly abandoned | look for an alternative |

## Report format (short, in the reader's language)

```
サイト点検（staging / 2026-09-26）
✅ 正常: WordPress 7.1.2 / PHP 8.3 / 有効プラグイン 7件
⚠️ 要対応: 〇〇 に更新あり（2.0.1 → 2.0.2）
⚠️ 要確認: error_log に Fatal error 3件（wp-content/plugins/xxx/…、9/25）
💡 提案: 無効のプラグイン「worker」は不要なら削除を検討
```

## Update procedure (a person, or an approved automation)

Backup (UpdraftPlus or the host's snapshot) → update on staging → clear cache → check home, one normal page, the contact form page, any page the changelog mentions, site health, error log → same on production → record what changed (plugin, from → to, date, result).

## Monthly

Database upkeep (export first, autoloaded options, transients, revisions, WooCommerce HPOS): `database/wp-database.md`. Host-specific steps (caches, cron, backups, staging on Hostinger and cPanel): `infrastructure/shared-hosting.md`.

Health check as above, plus: backups exist and are recent, SSL valid, forms deliver, Search Console has no new errors, database clean-up that keeps revisions and trash (never a blind "optimise everything"), a short report to the client.
