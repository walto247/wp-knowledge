# wp-knowledge — maintenance desk

This folder is the shared WordPress knowledge every project in `CC-projects/` reads.
Repository: github.com/walto247/wp-knowledge (branch `main`).

**At session start:** read `README.md` (the rules and open items) and `CHANGELOG.md`.
`CHANGELOG.md` is the only notification channel to other projects: they read its top entry
at the start of each session.

## Workspace house rules (owner, 2026-10-19; full text in the root `CC-projects/CLAUDE.md`)

**Communication & Output Standards (Total Tool Silence)** (owner, 2026-10-20; same text as the root `CLAUDE.md`):
- ZERO INTERMEDIATE CHATTER: Strictly DO NOT emit conversational text, thinking-out-loud commentary, or step-by-step progress play-by-plays before or between tool calls (e.g., NEVER write 'I will now check...', 'Let me inspect...', or 'Now placing images...').
- SILENT EXECUTION: Call tools, read files, and run commands back-to-back in complete silence. Do not narrate your actions; execute them directly.
- SINGLE FINAL RESPONSE: Only output text in your final turn when all tool calls and tasks are 100% complete. That final response must contain ONLY:
  1. **Completed:** Bulleted summary of concrete changes made and verification results.
  2. **Waiting for You:** Direct questions or approvals needed (or 'Ready for next instruction').

- **Safety:** never stage, commit or log credentials, API tokens, private keys (`*.pem`, `id_*`) or `.env` files. Never run
  destructive commands (`rm -rf`, `git push --force`, `git reset --hard`, `DROP TABLE`) without the owner's explicit instruction.
  **Commit locally only; never push automatically** (this replaces any "push after each commit" line in this file).
- **Code quality:** minimal diffs; edit existing code precisely, don't rewrite untouched functions or reformat surrounding files;
  keep existing comments, types and logic unless told to remove them.
- **Multibyte:** always keep UTF-8; never strip or alter Japanese (kanji/kana) characters or keigo phrasing.
- **Hygiene:** leave no temporary test files, debug logs or scratch scripts in the repository; clean up before reporting completion.
- **Scratchpad (rule 7, owner 2026-10-20):** owner-requested reports, audits, summaries and exports go automatically into
  `tmp/01_reports/` as `YYYY-MM-DD_<project>_<description>.<ext>`, never loose in `tmp/` or the project root. Other subfolders:
  `tmp/intake/raw/` (original client files), `tmp/intake/extracted/` (processed media, WebP, exports), `tmp/scratch/`
  (throwaway scripts, test dumps, logs), `tmp/review.html` (visual review, rule 6). All of `tmp/` stays untracked by git.

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

- Markdown only. No site-specific code (short reference snippets allowed; owner 2026-10-21), no client facts, no secrets.
- Edit here first. Account skills (`flatsome-wp`, `swell-wp`, `seo-expert`) are updated
  *from* this folder, never the reverse.
- Client-specific knowledge stays in the client's project.
- Not here: n8n server matters (the `n8n-server-ops` chat) and site work (each site's chat).
- Scratch files go in `tmp/` (git-ignored).

## Model

Opus 5.5 for routine runs. Switch to Fable for verifying against primary sources, resolving
conflicts between sources, or reviewing a big entry before it goes out.
