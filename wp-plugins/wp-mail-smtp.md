# WP Mail SMTP

Status: checked 2026-10-11 against wpmailsmtp.com docs: **WP Mail SMTP → Settings → Misc → Do Not Send** blocks everything sent through `wp_mail()`; mail sent by other means (PHP `mail()`) is not blocked.

Sends the site's email (form notifications, password resets) through a real mail account. Its settings contain passwords or OAuth tokens: never read, copy or change them.

- Staging has "Do not send" on, so staging tests email nobody.
- Production mail stops arriving: report to the admin; WP Mail SMTP → Tools → Email Test and Email Log are the places to look. Do not guess at settings.
