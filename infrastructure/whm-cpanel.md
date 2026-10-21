# WHM and cPanel servers: settings for speed and security

Status: **verified 2026-10-21** against docs.cpanel.net and support.cpanel.net, the cPanel v136 release notes, the Apache 2.4, PHP, MySQL and MariaDB manuals, and the Let's Encrypt FAQ (`SOURCES.md`, section "WHM and cPanel"). Marked **fact** (source) or **practice** (our default). Account-level basics (SSH, document roots, caches, cron, backups, staging): `shared-hosting.md`. Generic Linux hardening: `vps-hardening.md`. Changes on a live server: back up, one change at a time, measure before and after.

## Versions and requirements (fact, 2026-10)

- Current cPanel & WHM: **138** (v136 released 2026-05-27). Supported OS: **AlmaLinux 8/9/10, CloudLinux 8/9/10, Rocky 8/9, Ubuntu 24.04 LTS** (CentOS 7 is gone). Minimum 2 GB RAM / 20 GB disk; recommended 4 GB / 40 GB.
- Databases: default **MariaDB 10.11**; MariaDB 10.5–11.8 and MySQL 8.0/8.4 supported; MySQL 5.7 is no longer selectable.
- v136 merged the SSL screens into one SSL/TLS page and marks end-of-life PHP versions in MultiPHP Manager: menu names in older guides may differ.

## cPanel account side (port 2083)

- **PHP version:** 8.3 or 8.4 where the plugins allow (`../wp-security.md`). Speed gain over 7.4 is about **5–15 %** in benchmarks (Kinsta, Tideways), not the "20–35 %" often quoted; the real reason is security support.
- **MultiPHP INI Editor** writes to `php.ini`, `.user.ini` and `.htaccess` where each file supports the directive; the three may differ, and which one counts depends on the PHP handler (fact).
- **PHP values** (practice): `memory_limit` 256M (512M for builders or WooCommerce), `upload_max_filesize` 64–128M, `post_max_size` **≥** `upload_max_filesize` (PHP rule), `max_execution_time` 120–300 (never 0), `max_input_vars` 3000, `display_errors` Off and `log_errors` On, `zlib.output_compression` Off when Apache or a cache plugin already compresses. PHP defaults: `max_input_vars` 1000, `max_execution_time` 30.
  - WordPress core menus no longer hit `max_input_vars` (fixed in 4.5.1); large page-builder, theme-option and mega-menu forms still can.
- **AutoSSL:** **Let's Encrypt is the only provider** (Sectigo was removed in v120); 90-day certificates, checked nightly and renewed automatically. `mail.`, `webmail.`, `cpanel.` subdomains are covered when Tweak Settings → "Service subdomains" is On **and** the main domain uses the AutoSSL certificate (not a paid one). Dead subdomains: SSL/TLS Status → **"Exclude during AutoSSL"**. Validation fails when DNS is at Cloudflare (cPanel cannot write the TXT record) or when Cloudflare redirects, WAF or "Always Use HTTPS" intercept `/.well-known/acme-challenge/` (AutoSSL does not follow redirects): exempt that path or pause the proxy for one run.
- **Force HTTPS Redirect:** the toggle in Domains (main domains with a valid certificate only). Use one HTTPS redirect, not the toggle plus a plugin plus an `.htaccess` rule (redirect chains and loops; practice).
- **Cron:** `DISABLE_WP_CRON` plus a real cron job (`shared-hosting.md`). PHP path: the documented wrappers are **`/usr/bin/ea-php83`** (one per version) or `/usr/local/bin/php`; check with `ls /usr/bin/ea-php*`. End the command with `>/dev/null 2>&1` or every run sends a mail.
- **Email Deliverability** checks and repairs **SPF and DKIM** (and reports reverse-DNS problems); for **DMARC** it only suggests a record to install. Repair works only when the server is the domain's nameserver.
- **Optimize Website** = compression through mod_deflate (all content or listed types); does **not** work with the NGINX reverse proxy.
- **Indexes** → "No Indexing" on `public_html` hides folder listings.

## WHM server side (port 2087)

### EasyApache 4 stack

- **MPM:** EasyApache 4 installs **prefork by default**; cPanel and Apache recommend **event** (with PHP-FPM). Only one MPM at a time.
- **HTTP/2 (mod_http2)** conflicts with prefork, mpm_itk, mod_ruid2 and the DSO handler: switch to event first.
- Modules to have (fact: all in EA4): `mod_http2`, `mod_brotli` or `mod_deflate`, `mod_expires`, `mod_headers`, `mod_proxy_fcgi` (PHP-FPM, installed by default), `mod_security2`; `mod_remoteip` only behind Cloudflare or a CDN (`RemoteIPHeader CF-Connecting-IP`).
- **PHP handler:** **PHP-FPM** (on by default for new installs; cPanel wants at least 2 GB free or 30 MB per domain before enabling it on all domains). CloudLinux: LSAPI. **DSO is not supported from PHP 8.0.** suPHP, mod_ruid2 and mpm_itk are **not deprecated** but conflict with event, FPM and HTTP/2: avoid them unless a legacy reason exists.
- **PHP extensions** (practice): `opcache` (on once loaded; memory 128–256 MB, `max_accelerated_files` 10000+), `mbstring`, `intl`, `imagick` or `gd`, `curl`, `zip`, `xml`; `redis` or `memcached` for an object cache. No `xdebug` on production.
- **NGINX reverse proxy (ea-nginx)** is an option in front of Apache with per-user caching; WordPress needs correct `Cache-Control` headers or a plugin for logged-in pages; not compatible with LiteSpeed.

### Apache (WHM → Service Configuration → Apache Configuration → Global Configuration)

- WHM defaults (fact): Start Servers 5, **Server Limit 256, Max Request Workers 150**, Max Connections Per Child 10000, **Keep-Alive Off**, Keep-Alive Timeout 5, Max Keep-Alive Requests 100, **Timeout 300**. `ThreadsPerChild` and the spare-thread values are not in the form (Include Editor; Apache defaults 25 / 75 / 250).
- Apache rule (fact): `MaxRequestWorkers` ≤ `ServerLimit` × `ThreadsPerChild` and a multiple of `ThreadsPerChild` (Apache default 16 × 25 = 400).
- **Our defaults with event** (practice): Keep-Alive **On**, Keep-Alive Timeout 2–5, Timeout 60–120, `MaxRequestWorkers` 400 on a 4–8 GB server (16 × 25), higher only after measuring. Apache's own memory per process is small under event because PHP runs in the FPM pools; measure it (`ps -C httpd -o rss=`) instead of trusting a fixed figure.

### PHP-FPM pools (WHM → MultiPHP Manager)

- cPanel defaults per domain (fact): `pm` **ondemand**, **Max Children 5**, **Max Requests 20**, **Process Idle Timeout 10**; dangerous functions (`exec`, `shell_exec`, `system`, `passthru`) disabled; error log `~/logs/<domain>.php.error.log`. Global defaults live in `/var/cpanel/ApachePHPFPM/`; per domain in `/var/cpanel/userdata/<user>/<domain>.php-fpm.yaml`; rebuild with `/scripts/php_fpm_config --rebuild`.
- **"server reached max_children setting"** in the log = visitors queued or 503 errors: raise Max Children for that domain (fact, cPanel KB).
- **Sizing** (practice): free RAM after the OS, database, Apache and mail ÷ measured worker size (a WordPress worker is often 60–100 MB) = total children for all busy sites. Typical: small company site 5–10 children; ad-traffic or busy business site 10–20; shop or membership site 20–40 on 8–16 GB. Max Requests 200–500 (not 20); Process Idle Timeout 10–30 s.

### Security

- **ModSecurity:** install cPanel's **`ea-modsec2-rules-owasp-crs`** (OWASP Core Rule Set, kept updated; the old "V3.0" vendor entry is no longer updated). Watch for false positives on WordPress admin and forms.
- **cPHulk:** turn it on; defaults block an IP after 5 failures, accounts after 15; add country rules (Country Management) where logins only come from Japan.
- **Firewall:** ConfigServer stopped CSF in August 2025; **cPanel now maintains CSF** and delivers it through its signed updates (v136). Alternatives: Imunify360 (paid licence; the free ImunifyAV only scans). Open a changed SSH port in the firewall before restarting SSH.
- **open_basedir:** the old WHM "PHP open_basedir Tweak" was removed (cPanel 76+); set `open_basedir` in the WHM MultiPHP INI Editor or per FPM pool.
- **Symlink attacks between accounts:** on CloudLinux use **CageFS**; on AlmaLinux/Rocky use the **KernelCare** free patch set; Apache "Symlink Protection" (Bluehost patch) only if neither is possible.
- **Tweak Settings** (exact names): "Max hourly emails per domain" (default unlimited; practice 200–500), "Prevent "nobody" from sending mail" (On), "Restrict outgoing SMTP to root, exim, and mailman" (On), "Restrict document roots to public_html" (On), "Service subdomains" (On), "Require SSL for cPanel Services" (On), "Hide login password from cgi scripts" (default Off; turn On).

### Database

- `innodb_buffer_pool_size`: MySQL and MariaDB suggest up to 70–80 % of RAM on a **dedicated** database server. On a WHM server that also runs Apache, PHP and mail, **25–40 %** (up to 50 % when the sites are database-heavy) (practice); check the hit rate before raising it.

### Paid add-ons (fact)

- Imunify360 and JetBackup are separate paid licences, not included with cPanel; some hosts bundle them.
