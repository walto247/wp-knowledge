# Wordfence

Status: merged 2026-10-11. Unverified (pass 2).

Wordfence is the firewall and malware scanner. **Never change it.** Security decisions belong to the admin.

- Someone is blocked, sees a 403 or cannot log in: Wordfence may have blocked them; the admin checks Wordfence → Firewall / Login Security.
- Content with scripts, iframes or unusual code may be stopped by the firewall when saved. Keep content clean; never try to get around the firewall.
- Suspicious files (`../wp-security.md`): report, never delete or "clean".

Never suggest turning Wordfence off, whitelisting yourself, or disabling the firewall "to test". Do not read its options or `wp-content/wflogs/`.
