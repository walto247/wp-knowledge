# VPS hardening (Ubuntu 22.04 / 24.04, Debian 12)

Status: **verified 2026-10-19** against the Ubuntu Server docs and 24.04 release notes, `man sshd_config`, the Docker docs on firewalls, fail2ban's own config files, the Debian 12 release notes and wiki, and the WP-CLI handbook (`SOURCES.md`). Order and values are practice. Generic only: the facts and runbooks of our n8n VPS live in the `n8n-server-ops` project.

## Access

- **First login** (practice): create a user, give it sudo, install your public key, test the key login in a **second terminal**; only then turn off password login.
- **SSH settings in a drop-in file** `/etc/ssh/sshd_config.d/<name>.conf`: `PasswordAuthentication no` (the default is yes, so this is the line that matters), `PermitRootLogin prohibit-password` (already the default; `no` once the sudo user works), `PubkeyAuthentication yes`. Ubuntu reads the drop-ins first and **the first value wins**, so check existing drop-ins (hosts often ship a cloud-init file with `PasswordAuthentication yes`). Check with `sudo sshd -t` and `sudo sshd -T | grep -i passwordauth`.
- **Restart:** the service is `ssh` on Ubuntu and Debian (`sudo systemctl restart ssh`; `sshd` is only an alias on Debian). Ubuntu 22.10 and later start SSH through `ssh.socket`; on 24.04 a changed port is read from `sshd_config` by a generator, so after a port change run `systemctl daemon-reload` and restart `ssh.socket`, and open the new port in the firewall first. Practice: keep port 22 and rely on keys + fail2ban.
- **Keys** (practice): one key per person and device, named by server login (`CC-projects/secrets/ssh-keys/README.md`); remove a key from `authorized_keys` when the person or device leaves; rotate after any suspected exposure.

## Firewall

- UFW is off by default. Order: `ufw default deny incoming`, `ufw default allow outgoing`, allow SSH (from the office IP only where it is fixed), 80 and 443, **then** `ufw enable`; `ufw status verbose`, `ufw logging on`; `--dry-run` previews a change.
- **Docker bypasses UFW**: Docker's own docs call them incompatible; a published container port is reachable even when UFW blocks it. Publish container ports on `127.0.0.1` only and put a reverse proxy (Traefik, nginx) in front, or filter in the `DOCKER-USER` chain.

## Fail2ban

- Install it; configure in `/etc/fail2ban/jail.local` (never edit `jail.conf`). `[sshd]` with `enabled = true` is enough: on Debian-family systems fail2ban reads the systemd journal, and Debian 12 has **no `/var/log/auth.log`** by default, so do not set `logpath`. Debian may enable the sshd jail already: check with `fail2ban-client status sshd` (not verified from the package file).
- Defaults: ban 10 minutes after 5 failures in 10 minutes. Practice: ban 1 hour. `fail2ban-client reload` after changes.
- WordPress login attacks are handled by the site's firewall plugin (`../wp-security.md`), not by fail2ban.

## Updates, time, backups, monitoring

- **Security updates:** Ubuntu installs `unattended-upgrades` by default (daily, security only, **no automatic reboot**, logs in `/var/log/unattended-upgrades/`); Debian: `dpkg-reconfigure unattended-upgrades`. Practice: security only; reboot in a maintenance window when `/var/run/reboot-required` exists.
- **Time:** Ubuntu 24.04 uses `systemd-timesyncd` (chrony from 25.10). `timedatectl` must show NTP active and synchronized; wrong time breaks TLS, cron and logs.
- **Backups** (practice): provider snapshots are not application backups. Export the application data (database dumps, volumes) to storage off the server and test a restore (`../wp-security.md` baseline).
- **Monitoring** (practice): an outside uptime check (HTTPS and certificate expiry), disk, memory, load, journal errors, fail2ban bans.

## Updating many WordPress sites on one server (practice, built on the WP-CLI docs)

1. Run as **each site's own user** (`sudo -u <user> -i -- wp --path=…`), never `--allow-root` (wrong file owners, and WP-CLI warns against it).
2. `wp db export` to a folder **outside the web root**.
3. `wp core check-update`; `wp plugin update --all --dry-run` to preview.
4. Staging first; then `wp plugin update --all` (`--exclude=` for plugins that need a manual check), `wp core update --minor`, `wp core update-db`.
5. Purge caches, check the home page, a page, the form, Site Health and the error log; note plugin, from → to, date.

Same steps as the update procedure in `../wp-maintenance.md`.
