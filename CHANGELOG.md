# Changelog — what changed in the shared knowledge, and what to check on existing sites

Newest first. Every project reads the **top entry** at the start of a session (rule in `CC-projects/CLAUDE.md`).
An entry has two parts: what changed in the files, and a **checklist for existing sites** (check and report; change only with the owner's OK and each project's own rules).

## 2026-10-12 — Post slugs carry the title's keywords

Files changed: `seo-geo/README.md` (Japanese specifics).

What changed in the guidance:
- A post slug must describe the post with keywords from its title (English/romaji), not just a series name + date; a date may be appended for repeating posts. Automated posts build the slug from the same facts as the title. Found on wp-anshin-com, whose automated security posts used `security-news-YYYY-MM-DD`.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| Post slugs that are only a series name, a number or a date (`news-2026-10-01`, `?p=123`, `post-5`) | the slug is a small relevance and click signal and tells readers what the page is | count, examples, whether old slugs would redirect |
| Automated or imported posts (n8n, RSS, AI drafts) | slugs are often generated from dates or IDs | which workflow, how the slug is built |

## 2026-10-11 — Folder created; pass 1 (merge) and pass 2 (verification) done

Files changed: all. Sources and dates in each topic's `SOURCES.md`; status line at the top of every file.

What changed in the guidance:
- Japanese typography now follows DADS: body and UI text 16 px, floor 14 px (never below), line height 1.7–1.75 body / 1.4 headings, letter spacing 0.02 em (0 at 45 px+), size scale 16–45 px, Noto Sans JP as reference font, no italics, links underlined, ruby 50 %. 禁則処理 and Latin-in-Japanese rules from JLReq.
- Accessibility: WCAG 2.2 is the target (JIS X 8341-3 still equals WCAG 2.0; revision pending). Six new criteria: target size 24 px, focus not obscured, dragging alternatives, redundant entry, consistent help, accessible login. Japanese large text = 22 pt regular / 18 pt bold before 3:1 contrast is allowed.
- Flatsome (3.20.11 files): button colour is `color=`, shape is `style=`; `[accordion-item]` with hyphen; `[testimonial image= company=]`; no `.m-8` utility scale; visibility values are the four `hide/show-for-small/medium`; breakpoints 549 / 849 px; four filters from old notes do not exist.
- SWELL (2.19): official block list; slugs `loos/`; CSS variables verified, no `--color_accent`; official plugin list (Contact Form 7 not incompatible; SEO SIMPLE PACK is the house SEO plugin).
- SEO/GEO: Google sets no length limit on titles or descriptions; no special markup for AI Overviews / AI Mode; FAQ rich results ended 2026-05-07, HowTo in 2023, seven more types in June 2025; helpful-content and E-E-A-T rules recorded.
- Law: stealth-marketing designation details (2023-10-01), No.1-claim conditions (2024 report), 2024-10-01 amendment with direct fines.
- Security and performance: WordPress hardening baseline; PHP 8.2 security support ends 2026-12-31; Core Web Vitals thresholds and the 75th-percentile rule; WP Rocket exclusion field.

### Checklist for existing sites (run at the next session of each site project, report findings, owner decides)

| Check | Why | Report |
|---|---|---|
| PHP version | 8.1 or lower is end of life; 8.2 loses security fixes on 2026-12-31; WordPress recommends 8.4/8.5 | version, host, whether staging exists to test an upgrade |
| Text under 14 px, Japanese body line height under 1.5 | DADS floor; readability | where (template, CSS rule), how many places |
| Sticky header or bar that covers a focused form field | WCAG 2.2 focus not obscured | pages with sticky elements and forms |
| Controls that need dragging (sliders, carousels without arrows) | WCAG 2.2 dragging movements | element and page |
| Icon buttons or links smaller than 24 × 24 px with no spacing | WCAG 2.2 target size | element and page |
| Links shown by colour only | DADS: underline links | main content area |
| FAQ / HowTo schema present | no longer earns rich results; harmless | note only, no action |
| Titles / meta descriptions | no Google limit; no action unless truncated badly on phones | note only |
| Flatsome sites: buttons written as `style="primary"` in content | `color=` is the real attribute; Flatsome tolerates the old one, but new content should use the right form | note only |
| 「No.1」「最高」「限定」「今だけ」 claims, paid posts without 「PR」 | 景品表示法, ステマ規制 | page and wording |
| Backups stored only on the server | hardening guide: off-server copy | where backups go |

Priority: the live www.wp-anshin.com and the SKYUS staging first; then the SPINGLE sites and clark.ed.jp.

## How to add an entry

1. Change the topic file(s); update their `Status:` line and `SOURCES.md`.
2. Add an entry here: date, what changed, and a checklist row for anything that affects existing sites. Leave the checklist out when nothing does.
3. Commit and push. Nothing else is needed: every project reads this file at its next session.
