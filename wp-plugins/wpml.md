# WPML (multilingual sites)

Status: checked 2026-10-11 against WPML documentation and support answers for the slug settings. **WPML 5.0 (2026-09-13) redesigned the admin** (one Translations menu, one searchable Settings page, languages as language + country, automatic translation in the background, new pricing by words): the menu path below is for WPML 4.x; find the same setting on a 5.0 site before relying on it. After switching to WPML's AI engine, new translations **publish without review by default**: a person must turn review on (our rule below). Update all WPML components together. Polylang notes: one language switch does not cover it; treat as a separate case.

- Each language version of a page is a **separate post**, linked by WPML. Editing the Japanese page does not change the English one.
- Two language versions can share a slug. Whether they do is set in **WPML → Settings → Translated documents options → Page URL** ("Auto-generate from title" default, "Translate", or "Copy from original language", the last only when the secondary language uses encoded URLs); post-type base slugs are translated under Slug translations (String Translation); a translation's slug can also be set by hand in the translation editor. When a slug matches more than one post, stop and ask which language is meant; never guess.
- Edit the content of one language version. Creating translations, linking posts as translations and language settings are a person's work in WPML.
- **Never publish machine translation.** Draft for a native speaker's review and keep it as a draft.
- Translate SEO fields, image alt text and slugs per language, not only the body. No English fallback text on a Japanese page, or the reverse.
- New posts created by code: create them inside the language switch so the post never exists in the default language for a moment. Tags re-sent by name on a translated post can link a same-named tag of another language; check.
