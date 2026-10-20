# WPForms

Status: shortcode checked 2026-10-11 against WPForms documentation (`[wpforms id="123" title="true" description="true"]`; `false` hides them). Japanese form conventions: `../design/japan.md`.

## Safe

- Place a form: `[wpforms id="566"]` (optionally `title="false" description="false"`). Form IDs are in WPForms → All Forms (post type `wpforms`).
- Style with theme CSS, scoped to the form: `#wpforms-566 .wpforms-submit { … }`. Classes: `.wpforms-container`, `.wpforms-form`, `.wpforms-field`, `.wpforms-field-label`, `.wpforms-submit`, `.wpforms-error`.

## A person does

Fields, labels, validation, notifications (who gets the email), confirmations (thank-you or redirect), spam protection, payments: WP admin → WPForms. Entries and uploaded files hold personal data; do not read or export them for content tasks.

## Japanese form checklist to suggest

Use the form rules in `../design/japan.md` (Forms): fields, ※必須 / ※任意, `autocomplete`, postal-code fill, no email re-type field, privacy link before submit, Japanese error text, a thank-you with the next step.

## Staging

Email sending is off on staging (WP Mail SMTP "do not send"). Test submissions reach nobody; say so when someone asks why no email arrived.
