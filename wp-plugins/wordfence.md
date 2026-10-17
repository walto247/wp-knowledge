# Wordfence

Status: version checked 2026-10-17 (9.0.2, 2026-09-30; 9.0.0 added **passkey login** for free and premium, an option for the 2FA baseline in `../wp-security.md`). The rules below are practice.

Wordfence is the firewall and malware scanner. **Never change it.** Security decisions belong to the admin.

- Someone is blocked, sees a 403 or cannot log in: Wordfence may have blocked them; the admin checks Wordfence → Firewall / Login Security.
- Content with scripts, iframes or unusual code may be stopped by the firewall when saved. Keep content clean; never try to get around the firewall.
- Suspicious files (`../wp-security.md`): report, never delete or "clean".

Never suggest turning Wordfence off, whitelisting yourself, or disabling the firewall "to test". Do not read its options or `wp-content/wflogs/`.
