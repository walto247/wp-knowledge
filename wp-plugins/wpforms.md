# WPForms

Status: shortcode checked 2026-10-11 against WPForms documentation (`[wpforms id="123" title="true" description="true"]`; `false` hides them). Japanese form conventions: `../design/japan.md`.

## Safe

- Place a form: `[wpforms id="566"]` (optionally `title="false" description="false"`). Form IDs are in WPForms → All Forms (post type `wpforms`).
- Style with theme CSS, scoped to the form: `#wpforms-566 .wpforms-submit { … }`. Classes: `.wpforms-container`, `.wpforms-form`, `.wpforms-field`, `.wpforms-field-label`, `.wpforms-submit`, `.wpforms-error`.

## A person does

Fields, labels, validation, notifications (who gets the email), confirmations (thank-you or redirect), spam protection, payments: WP admin → WPForms. Entries and uploaded files hold personal data; do not read or export them for content tasks.

## Japanese form checklist to suggest

お名前 + フリガナ · 郵便番号 → 住所 auto-fill · 電話番号 (digits normalised) · メールアドレス + confirmation · 必須 / 任意 labels · privacy consent checkbox before submit · Japanese error text next to the field · clear thank-you with next step.

## Staging

Email sending is off on staging (WP Mail SMTP "do not send"). Test submissions reach nobody; say so when someone asks why no email arrived.
