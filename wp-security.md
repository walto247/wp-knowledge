# Security review (read-only)

Status: **verified 2026-10-11** against the WordPress hardening guide (developer.wordpress.org/advanced-administration/security/hardening/), php.net supported versions and the WordPress 7.1 hosting handbook. The review routine itself is our practice. Firewall plugin: `wp-plugins/wordfence.md`. Sources: `wp-plugins/SOURCES.md`.

Security **settings** are never part of a content task: Wordfence, users and roles, `wp-config.php`, `.htaccess`, passwords, keys. Look, report, a person acts.

## What to check

1. **Updates:** outdated plugins, themes and core are the most common way in. List them first.
2. **Unused code:** inactive plugins and extra themes still run code if called directly. Suggest deleting what is not used.
3. **Suspicious files:** `.php` inside `wp-content/uploads/` (uploads hold media only); odd names in the WordPress folder or theme (`wp-xyz.php`, random strings, `.ico` files containing PHP); PHP with `eval(`, `base64_decode(`, `gzinflate(`, `str_rot13(`, long encoded strings. Report path, size, date. Open no more than needed; delete nothing; "clean" nothing.
4. **Content:** links, scripts, iframes or redirects nobody recognises (spam links, hidden iframes). Report the page and the suspicious part.
5. **Information exposure:** `readme.html` and `license.txt` reveal little; a web-readable `error_log` leaks paths; mention if large and recent.
6. **Accounts:** admin users that nobody recognises, generic usernames (`admin`), accounts without 2FA where the site supports it.
7. **Plugin integrity:** installed plugin files match the official checksums for their version (`wp plugin verify-checksums`); flag plugins not from the official source and known-vulnerable versions.

## Baseline a site should meet (WordPress hardening guide)

| Item | Value |
|---|---|
| Core, plugins, themes | current; automatic minor updates on; only from wordpress.org or known vendors; delete what is unused |
| PHP | a supported version (table below) |
| Accounts | long unpredictable passwords, **two-step authentication**, no account named `admin`, least privilege |
| File permissions | directories **755**, files **644**; `wp-config.php` **400 or 440**; only `wp-content` writable by the web server |
| `wp-config.php` | `define( 'DISALLOW_FILE_EDIT', true );` (no editor in the dashboard); optionally one level above the web root; denied in `.htaccess` |
| Database | non-default table prefix; DB user with only SELECT, INSERT, UPDATE, DELETE for daily use (do not revoke DROP/ALTER without a tested backup plan, updates need them) |
| Transport | SFTP, never FTP; HTTPS for admin; optional HTTP Basic Auth on `/wp-admin/` |
| Firewall | a plugin firewall (Wordfence on our sites) or a server WAF; Cloudflare in front where used |
| Logs and integrity | review access and error logs; file-integrity monitoring (changed or added files); external malware scan |
| Backups | regular, dated, **stored off the server**, encrypted, restore tested |

## Versions to know (2026-10-17)

| What | State |
|---|---|
| WordPress | **7.1.3 (2026-10-06)** is current; three security releases in Sep–Oct 2026 (7.1.1, 7.1.2 critical, 7.1.3): keep automatic minor updates on. 7.2 due 2026-12-08 (beta 2026-10-20) with a new default theme (proposal: Ipsum). Minimum PHP 7.4; **recommended PHP 8.4 or 8.5**, MySQL 8.4 or MariaDB 10.11 / 11.4 / 11.8 (hosting handbook 7.1) |
| PHP 8.5 | active support to 2027-12-31, security fixes to 2029-12-31 |
| PHP 8.4 | active support to 2026-12-31, security fixes to 2028-12-31 |
| PHP 8.3 | security fixes only, to 2027-12-31 |
| PHP 8.2 | security fixes only, **to 2026-12-31**: plan the move to 8.3+ now |
| PHP 8.1 and older | end of life, no fixes |
| PHP 8.6 | release planned 2026-11-19 |

## If the site looks hacked

Stop and say clearly what was found and where. The admin runs a Wordfence scan and contacts the host. No repairs: a wrong fix destroys evidence or the site.

## Never

- Suggest weakening security to make something work (disabling the firewall, 777 permissions, turning off updates).
- Read or repeat passwords, keys or tokens, even if visible in a file. Say that a secret is exposed and where, not what it is.
