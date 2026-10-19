# wp-knowledge — maintenance desk

This folder is the shared WordPress knowledge every project in `CC-projects/` reads.
Repository: github.com/walto247/wp-knowledge (branch `main`).

**At session start:** read `README.md` (the rules and open items) and `CHANGELOG.md`.
`CHANGELOG.md` is the only notification channel to other projects: they read its top entry
at the start of each session.

## Workspace house rules (owner, 2026-10-19; full text in the root `CC-projects/CLAUDE.md`)

- **Communication:** lead with deliverables and results; no preambles or step-by-step narration; don't print trial-and-error
  attempts, routine command output or internal scans unless blocked by an unrecoverable error. Answers to the owner have two
  sections: **Completed** (changes and verification checks) and **Waiting for You** (decisions or approvals needed, or "Ready for
  next instruction"). Reports to the Orchestrator still include the full outputs and diffs the worker protocol asks for.
- **Safety:** never stage, commit or log credentials, API tokens, private keys (`*.pem`, `id_*`) or `.env` files. Never run
  destructive commands (`rm -rf`, `git push --force`, `git reset --hard`, `DROP TABLE`) without the owner's explicit instruction.
  **Commit locally only; never push automatically** (this replaces any "push after each commit" line in this file).
- **Code quality:** minimal diffs; edit existing code precisely, don't rewrite untouched functions or reformat surrounding files;
  keep existing comments, types and logic unless told to remove them.
- **Multibyte:** always keep UTF-8; never strip or alter Japanese (kanji/kana) characters or keigo phrasing.
- **Hygiene:** leave no temporary test files, debug logs or scratch scripts in the repository; clean up before reporting completion.

## What this chat does

1. **News in, verified update out.** When the owner pastes news (Google Search Central post,
   Flatsome or SWELL release note, law change, SEO article):
   - verify it against the primary source (never "verified" from memory);
   - update the topic file and its `Status:` line (source + date);
   - update that topic's `SOURCES.md`;
   - add a dated `CHANGELOG.md` entry, with a checklist row if existing sites are affected;
   - commit and push.
2. **Finish pass 2.** The open items are listed at the end of `README.md`.
3. **Monthly check.** Open every `SOURCES.md` URL, compare with the `Status:` lines, propose
   changes on a branch with a draft `CHANGELOG.md` entry. The owner approves the merge;
   never merge it yourself.

## Rules

- Markdown only. No code, no client facts, no secrets.
- Edit here first. Account skills (`flatsome-wp`, `swell-wp`, `seo-expert`) are updated
  *from* this folder, never the reverse.
- Client-specific knowledge stays in the client's project.
- Not here: n8n server matters (the `n8n-server-ops` chat) and site work (each site's chat).
- Scratch files go in `tmp/` (git-ignored).

## Model

Opus 5.5 for routine runs. Switch to Fable for verifying against primary sources, resolving
conflicts between sources, or reviewing a big entry before it goes out.
