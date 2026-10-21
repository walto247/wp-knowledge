# Sources (infrastructure/)

All read 2026-10-19.

| Topic | Source | URL |
|---|---|---|
| Hostinger SSH, document root, File Manager | Hostinger support | https://www.hostinger.com/support/1583245 · https://www.hostinger.com/support/5973000 |
| Hostinger WP-CLI | Hostinger tutorials; WP-CLI hosting list | https://www.hostinger.com/tutorials/wp-cli · https://make.wordpress.org/cli/handbook/guides/hosting-companies/ |
| Hostinger object cache, Cache Manager | Hostinger support | https://www.hostinger.com/support/6099689 · https://www.hostinger.com/support/6215624 |
| Hostinger PHP version and options | Hostinger support | https://www.hostinger.com/support/1575755 · https://www.hostinger.com/support/4622479 |
| Hostinger SSL and failed SSL | Hostinger support | https://www.hostinger.com/support/1583258 · https://www.hostinger.com/support/5613445 |
| Hostinger cron, backups, staging | Hostinger docs and support | https://docs.hostinger.com/websites/cron-jobs · https://docs.hostinger.com/websites/backups · https://www.hostinger.com/support/5720286 |
| LiteSpeed Cache CLI | LiteSpeed docs | https://docs.litespeedtech.com/lscache/lscwp/cli/ |
| WP-CLI: root warning, cache flush, cron, update commands | WP-CLI handbook | https://make.wordpress.org/cli/handbook/guides/common-issues/ · https://developer.wordpress.org/cli/commands/cache/flush/ · https://developer.wordpress.org/cli/commands/plugin/update/ |
| WordPress memory limits | wp-config API | https://developer.wordpress.org/apis/wp-config-php/ |
| cPanel SSH, Terminal, MultiPHP, Cron, Backup Wizard | docs.cpanel.net | https://docs.cpanel.net/cpanel/security/ssh-access/ · https://docs.cpanel.net/cpanel/software/multiphp-manager-for-cpanel/ · https://docs.cpanel.net/cpanel/advanced/cron-jobs/ · https://docs.cpanel.net/cpanel/files/backup-wizard/ |
| cPanel AutoSSL and validation failures | docs.cpanel.net; cPanel support | https://docs.cpanel.net/whm/ssl-tls/manage-autossl/ · https://docs.cpanel.net/cpanel/security/ssl-tls-status/ |
| WP Toolkit CLI | docs.cpanel.net | https://docs.cpanel.net/knowledge-base/cpanel-developed-plugins/wp-toolkit-command-line-interface/ |
| OpenSSH on Ubuntu (drop-ins, service name) | Ubuntu Server docs | https://ubuntu.com/server/docs/how-to/security/openssh-server/ |
| ssh.socket on 24.04 | Ubuntu Discourse / 24.04 release notes | https://discourse.ubuntu.com/t/30189 |
| sshd_config defaults | man sshd_config | https://man.openbsd.org/sshd_config |
| UFW | Ubuntu Server docs | https://ubuntu.com/server/docs/how-to/security/firewalls/ |
| Docker and UFW | Docker docs | https://docs.docker.com/engine/network/packet-filtering-firewalls/ |
| Fail2ban defaults, journal backend | fail2ban jail.conf, paths-debian.conf; Debian 12 release notes 5.1.7 | https://github.com/fail2ban/fail2ban · https://www.debian.org/releases/bookworm/release-notes/ |
| Unattended upgrades | Ubuntu Server docs; Debian wiki | https://ubuntu.com/server/docs/how-to/software/automatic-updates/ · https://wiki.debian.org/UnattendedUpgrades |

Not verified: Debian's default sshd jail file (source page not reachable); cPanel certificate validity and renewal window (host guides only); Hostinger daily-backup retention (two pages disagree).

## WHM and cPanel (`whm-cpanel.md`), read 2026-10-21

| Topic | Source | URL |
|---|---|---|
| Versions, OS, requirements | cPanel docs; v136 release | https://docs.cpanel.net/installation-guide/system-requirements-almalinux/ · https://www.cpanel.net/blog/announcements/introducing-cpanel-whm-version-136/ |
| MySQL / MariaDB versions | cPanel docs | https://docs.cpanel.net/knowledge-base/general-systems-administration/supported-mysql-mariadb-versions/ |
| MultiPHP INI Editor | cPanel docs | https://docs.cpanel.net/cpanel/software/multiphp-ini-editor-for-cpanel/ |
| PHP defaults, OPcache, FPM directives | PHP manual | https://www.php.net/manual/en/info.configuration.php · https://www.php.net/manual/en/opcache.configuration.php · https://www.php.net/manual/en/install.fpm.configuration.php |
| PHP benchmarks | Kinsta; Tideways | https://kinsta.com/blog/php-benchmarks/ · https://tideways.com/?p=9326 |
| WordPress menus and max_input_vars | WordPress Trac #14134 | https://core.trac.wordpress.org/ticket/14134 |
| AutoSSL (Let's Encrypt only, service subdomains) | cPanel docs and KB | https://docs.cpanel.net/whm/ssl-tls/manage-autossl/ · https://support.cpanel.net/hc/en-us/articles/22914390670615 · https://support.cpanel.net/hc/en-us/articles/360052742893 |
| Let's Encrypt validity | Let's Encrypt FAQ | https://letsencrypt.org/docs/faq/ |
| Force HTTPS, Email Deliverability, Optimize Website, Indexes | cPanel docs | https://docs.cpanel.net/cpanel/domains/domains/ · https://docs.cpanel.net/cpanel/email/email-deliverability-in-cpanel/ · https://docs.cpanel.net/cpanel/software/optimize-website/ · https://docs.cpanel.net/cpanel/advanced/indexes/ |
| ea-php CLI wrappers | cPanel docs | https://docs.cpanel.net/ea4/php/easyapache4-and-the-ea-php-cli-package/ |
| MPMs, HTTP/2, handlers, modules | cPanel EA4 docs; Apache HTTP/2 how-to | https://docs.cpanel.net/ea4/apache/multi-processing-modules-mpm/ · https://docs.cpanel.net/ea4/apache/apache-modules/apache-module-http2/ · https://docs.cpanel.net/ea4/php/php-handlers/ · https://httpd.apache.org/docs/2.4/howto/http2.html |
| Apache Global Configuration defaults | cPanel docs | https://docs.cpanel.net/whm/service-configuration/global-configuration/ |
| MaxRequestWorkers, ServerLimit, KeepAlive | Apache docs | https://httpd.apache.org/docs/2.4/mod/mpm_common.html · https://httpd.apache.org/docs/2.4/mod/core.html |
| PHP-FPM defaults and max_children | cPanel docs and KB | https://docs.cpanel.net/knowledge-base/php-fpm/configuration-values-of-php-fpm/ · https://support.cpanel.net/hc/en-us/articles/360047737894 · https://support.cpanel.net/hc/en-us/articles/360057592274 |
| NGINX reverse proxy | cPanel docs | https://docs.cpanel.net/knowledge-base/nginx/nginx-with-reverse-proxy/ |
| ModSecurity vendors, cPHulk, Security Center | cPanel docs | https://docs.cpanel.net/whm/security-center/modsecurity-vendors/ · https://docs.cpanel.net/whm/security-center/cphulk-brute-force-protection/ · https://docs.cpanel.net/whm/security-center/ |
| open_basedir tweak removed | cPanel KB | https://support.cpanel.net/hc/en-us/articles/360053606013 |
| Symlink protection | cPanel docs | https://docs.cpanel.net/ea4/apache/symlink-race-condition-protection/ |
| Tweak Settings | cPanel docs | https://docs.cpanel.net/whm/server-configuration/tweak-settings/mail/ · https://docs.cpanel.net/whm/server-configuration/tweak-settings/security/ |
| CSF maintained by cPanel | cPanel KB | https://support.cpanel.net/hc/en-us/articles/37654028162071 |
| InnoDB buffer pool | MySQL; MariaDB | https://dev.mysql.com/doc/refman/8.4/en/innodb-buffer-pool.html · https://mariadb.com/kb/en/innodb-buffer-pool/ |

Corrected from a pasted guide (2026-10-21): "PHP 8.3 is 20–35 % faster" (benchmarks 5–15 %); "WordPress menus break at 1000 input vars" (fixed in 4.5.1); "AutoSSL Let's Encrypt or Sectigo" (Let's Encrypt only); cron path `/usr/local/bin/ea-php83` (documented `/usr/bin/ea-php83`); "Email Deliverability validates DMARC" (it only suggests a record); "suPHP / ruid2 deprecated" (not deprecated; conflicting); WHM default Keep-Alive (Off, not On); "PHP open_basedir Tweak" (removed); "CSF discontinued" (now maintained by cPanel); innodb buffer pool 40–50 % (25–40 % on a shared WHM box). Practice without a primary source: Apache "10–15 MB per process", the PHP-FPM sizing formula and tiers.
