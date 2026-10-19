# WordPress database upkeep

Status: **verified 2026-10-19** against the WP-CLI handbook, the wp-config API page, the WordPress 6.6 autoload dev note, the Site Health source and the WooCommerce HPOS docs (`SOURCES.md`). Thresholds and routines are practice. Health check and monthly routine: `../wp-maintenance.md`.

## Before anything

- **Export first:** `wp db export` before any database operation (it runs mysqldump with the `wp-config.php` credentials). Save it **outside the web root**: the dump holds every user, order and setting. Never in a repository; delete it when done.
- **Never hard-code `wp_`:** `wp db prefix` prints the real table prefix (our sites use a custom one, `../wp-security.md`).

## Autoloaded options (fact unless marked)

- Since **WordPress 6.6** the autoload column holds `on`, `off`, `auto`, `auto-on`, `auto-off` (old `yes` / `no` still mean on / off). Rows that load on every page: `yes`, `on`, `auto-on`, `auto`. Options without an explicit flag are no longer autoloaded above **150 KB**.
- **Site Health** warns "Autoloaded options could affect performance" when the autoloaded total passes **800,000 bytes**. Use that number in reports.
- Finding the large ones: `wp option list --autoload=on` lists only `yes` / `on` rows and misses `auto` / `auto-on`; for the full list query the options table (real prefix) for all four values, ordered by size.
- Fix (practice): options left by removed plugins → set autoload off or delete, **after** confirming the plugin is gone; the Performance Lab plugin also lists them.

## Routine clean-ups

- **Transients:** `wp transient delete --expired`. With a persistent object cache, transients live in the cache, not the database.
- **Revisions, trash, autosave** (`wp-config.php`): `WP_POST_REVISIONS` (default unlimited; practice: cap at 5–10), `EMPTY_TRASH_DAYS` (default 30; never 0, that turns the trash off), `AUTOSAVE_INTERVAL` (default 60 s). Owner rule (`../wp-maintenance.md`): clean-ups keep revisions and trash, so cap revisions going forward instead of deleting history.
- **`wp db optimize`** (mysqlcheck optimize) rebuilds InnoDB tables: rarely, after large deletions, after the export, off-peak (practice). **`wp db repair`** helps only MyISAM tables; a damaged InnoDB table needs a restore.

## WooCommerce: High-Performance Order Storage (HPOS)

- Default for new stores since WooCommerce 8.2 (October 2023): orders live in their own tables (`wc_orders`, `wc_order_addresses`, `wc_order_operational_data`, `wc_orders_meta`, with the site's prefix), not in posts and postmeta. Setting: WooCommerce → Settings → Advanced → Features ("Order data storage" and "compatibility mode" = keep the old tables in sync).
- Check with `wp wc hpos status` and `wp wc hpos compatibility-info` (which plugins declare support). Switch back only through compatibility mode: let the sync finish, then choose the legacy storage.
- **WooCommerce 10.7** (2026-04-14) turned "sync on read" off by default: plugins that still write orders to posts must be updated; stores stable on HPOS should turn compatibility mode off for speed.
- On HPOS stores, order clean-up queries on posts/postmeta are wrong; revision and transient clean-ups are unaffected.
