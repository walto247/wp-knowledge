# Security review (read-only)

Status: merged 2026-10-11 from the dashboard `wp-security` skill. Unverified against the WordPress hardening guide (pass 2). Firewall plugin: `wp-plugins/wordfence.md`.

Security **settings** are never part of a content task: Wordfence, users and roles, `wp-config.php`, `.htaccess`, passwords, keys. Look, report, a person acts.

## What to check

1. **Updates:** outdated plugins, themes and core are the most common way in. List them first.
2. **Unused code:** inactive plugins and extra themes still run code if called directly. Suggest deleting what is not used.
3. **Suspicious files:** `.php` inside `wp-content/uploads/` (uploads hold media only); odd names in the WordPress folder or theme (`wp-xyz.php`, random strings, `.ico` files containing PHP); PHP with `eval(`, `base64_decode(`, `gzinflate(`, `str_rot13(`, long encoded strings. Report path, size, date. Open no more than needed; delete nothing; "clean" nothing.
4. **Content:** links, scripts, iframes or redirects nobody recognises (spam links, hidden iframes). Report the page and the suspicious part.
5. **Information exposure:** `readme.html` and `license.txt` reveal little; a web-readable `error_log` leaks paths; mention if large and recent.
6. **Accounts:** admin users that nobody recognises, generic usernames (`admin`), accounts without 2FA where the site supports it.
7. **Plugin integrity (later, owner toolkit):** compare installed plugin files with the official checksums per version; flag plugins not from the official source or differing from it, and known-vulnerable versions.

## If the site looks hacked

Stop and say clearly what was found and where. The admin runs a Wordfence scan and contacts the host. No repairs: a wrong fix destroys evidence or the site.

## Never

- Suggest weakening security to make something work (disabling the firewall, 777 permissions, turning off updates).
- Read or repeat passwords, keys or tokens, even if visible in a file. Say that a secret is exposed and where, not what it is.
