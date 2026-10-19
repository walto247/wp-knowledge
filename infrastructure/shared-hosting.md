# Shared hosting for WordPress: Hostinger (hPanel) and cPanel

Status: **verified 2026-10-19** against Hostinger support and docs, docs.cpanel.net, LiteSpeed docs and the WP-CLI handbook (`SOURCES.md`). Procedures are practice. VPS servers: `vps-hardening.md`; the n8n VPS itself: the `n8n-server-ops` project. Update procedure: `../wp-maintenance.md`.

## Hostinger web hosting (hPanel)

- **SSH:** Premium plans and higher (not Single). Turn it on in the site's SSH Access page; the port is non-standard (for example 65002) and the user is `u<digits>`; add a public key there. Practice: keys only.
- **Document root:** `/home/u<digits>/domains/<domain>/public_html`. Only site files belong in `public_html`.
- **WP-CLI** is preinstalled on Premium and higher. Run it as the hosting user inside the site folder (or with `--path=`). **Never `--allow-root`** (WP-CLI: running as root is "extremely dangerous").
- **Three caches** (purge all three after a change, practice):
  1. LiteSpeed Cache plugin: `wp litespeed-purge all` (or `url <url>`).
  2. Object cache (LiteSpeed Memcached, Business plans and higher): `wp cache flush` (flushes every site on a multisite; brief load on production).
  3. hPanel → Advanced → Cache Manager: the server's page cache (automatic every 30 minutes, or purge the site or one URL). A CDN cache is purged separately under CDN.
- **PHP:** hPanel → website dashboard → PHP Configuration; one version for every site on the plan (8.2–8.5 offered; per-folder version via `.htaccess`). PHP Options (memory, upload size, execution time) are capped at the plan limit; higher values are silently reduced. WordPress itself sets `WP_MEMORY_LIMIT` 40M and `WP_MAX_MEMORY_LIMIT` 256M. Practice for builder-heavy sites: memory 256M, uploads 64M, execution time 300 s, `max_input_vars` 3000.
- **SSL:** free "Lifetime SSL" (Let's Encrypt-based), installed within about 2 hours and renewed automatically. If it fails: the domain must point to Hostinger (nameservers or A record), only **one** A record, no CAA record blocking it, Cloudflare proxy off (DNS only) until active, domain name 64 characters or fewer; then uninstall and install again in hPanel. WP-CLI cannot issue certificates.
- **Cron:** hPanel → Cron Jobs. Hostinger's own advice: `define('DISABLE_WP_CRON', true);` in `wp-config.php` and run `wp-cron.php` from a real cron job (practice: every 5–15 minutes; `wp cron event run --due-now` also works).
- **Backups:** weekly on all plans, daily on Business and higher (add-on below); restore files only, database only or everything (overwrites, cannot be undone); a manual backup once per 24 hours on Business and higher. Retention: check hPanel (Hostinger's pages disagree). Practice: the host backup is the second net; UpdraftPlus off-site stays the first (`../wp-plugins/updraftplus.md`).
- **Staging:** Business and higher; hPanel → Staging → Create (a subdomain); root domains only, no multisite. **Push to live replaces the live files and database**: everything changed on live since the copy (orders, form entries) is lost; back up first.

## cPanel (features depend on the host)

- **SSH:** Security → SSH Access (generate or import a key, then **Authorize**; deauthorize to block). Not every host allows shell access; Terminal appears only when it does.
- **Document root:** `/home/<account>/public_html` for the main domain; addon domains have their own folder (check Domains, never assume).
- **WP-CLI** is not guaranteed: check `wp --info`; where the host runs WP Toolkit, it can run WP-CLI commands for you.
- **Caches:** whatever the site uses (LiteSpeed Cache on LiteSpeed servers: same command as above); an object cache only if the host provides Redis or Memcached.
- **PHP:** Software → MultiPHP Manager (version per domain) and MultiPHP INI Editor (values).
- **SSL:** AutoSSL (default provider Let's Encrypt), checked nightly. Status and the last error per domain: Security → SSL/TLS Status. Validation fails when the domain does not point to the server, when `/.well-known/acme-challenge/` or `/.well-known/pki-validation/` is blocked (redirects, `.htaccess` rules, Cloudflare WAF), or when a CAA record excludes the issuer. Practice: exempt `/.well-known/` from redirects, fix DNS, re-run once; do not loop (rate limits).
- **Cron:** Advanced → Cron Jobs; absolute paths; add `>/dev/null 2>&1` to avoid a mail per run. Same `DISABLE_WP_CRON` pattern.
- **Backups:** Files → Backup Wizard: a full backup can only be restored by the host; partial backups (home folder, database, mail) can be restored by you. Host-level backups (JetBackup and similar) vary: ask the host.
- **Staging:** WP Toolkit Clone and "Copy Data" back to production (with a restore point), inside the same account; otherwise a subdomain and a manual copy.
