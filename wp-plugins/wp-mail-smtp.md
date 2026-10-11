# WP Mail SMTP

Status: merged 2026-10-11. Unverified (pass 2).

Sends the site's email (form notifications, password resets) through a real mail account. Its settings contain passwords or OAuth tokens: never read, copy or change them.

- Staging has "Do not send" on, so staging tests email nobody.
- Production mail stops arriving: report to the admin; WP Mail SMTP → Tools → Email Test and Email Log are the places to look. Do not guess at settings.
