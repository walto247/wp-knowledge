# WPML (multilingual sites)

Status: merged 2026-10-11. Unverified (pass 2). Polylang notes: one language switch does not cover it; treat as a separate case.

- Each language version of a page is a **separate post**, linked by WPML. Editing the Japanese page does not change the English one.
- Two language versions can share a slug. When a slug matches more than one post, stop and ask which language is meant; never guess.
- Edit the content of one language version. Creating translations, linking posts as translations and language settings are a person's work in WPML.
- **Never publish machine translation.** Draft for a native speaker's review and keep it as a draft.
- Translate SEO fields, image alt text and slugs per language, not only the body. No English fallback text on a Japanese page, or the reverse.
- New posts created by code: create them inside the language switch so the post never exists in the default language for a moment. Tags re-sent by name on a translated post can link a same-named tag of another language; check.
