# UpdraftPlus

Status: merged 2026-10-11. Unverified (pass 2).

UpdraftPlus makes the site's regular backups (database, plugins, themes, uploads). Backup files live in `wp-content/updraft/` and contain the whole database: never expose, copy into a repository or paste from them.

- Big changes (redesigns, plugin updates on production) are preceded by an UpdraftPlus backup taken by a person. Remind them.
- Restores are a person's decision. Never suggest a restore to fix a small mistake: it also removes everything since (form entries, orders, posts). Small mistakes are undone by changing the item back.
- Automated assistants keep their own safety net (change sets with before/after, snapshots before the first write) and do not rely on UpdraftPlus for undo.
