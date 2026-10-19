# Japanese online shops: prices, payment, checkout fields, delivery

Status: **verified 2026-10-19** against 国税庁, 経済産業省 / 日本クレジット協議会, Shopify Help, Stripe docs, WooCommerce docs, KOMOJU, Paidy, Pay-easy, Yamato and Sagawa pages (`SOURCES.md`). Marked **law**, **platform** (as of 2026-10) or **practice**. The 特定商取引法 page and the final confirmation screen: `../legal/japan.md` only. Form rules (必須, autocomplete, full-width digits): `../design/japan.md`. Selling abroad: `cross-border.md`.

## Prices and tax

- **Law, 消費税:** 10 %; 8 % for 飲食料品 (not alcohol, not eating in) and newspapers delivered twice a week or more. 国税庁 announces a lower food rate for 2027-04-01 to 2029-03-31: re-check the figure before then.
- **Law, 総額表示:** prices shown to consumers in advance include tax: 「11,000円」「11,000円（税込）」「11,000円（税抜価格10,000円）」 and similar. Quotes and invoices are not covered.
- **Law, インボイス制度** (since 2023-10-01): only registered businesses issue 適格請求書 (登録番号, per-rate totals and tax); a shop may issue the simpler 適格簡易請求書. **Platform:** neither WooCommerce nor Shopify prints one by default; B2B shops need an invoice plugin or app.
- **Practice:** WooCommerce prices entered tax-inclusive with two tax classes (10 % and 8 %); Shopify "include tax in prices". Show 送料 and the free-shipping threshold on the product page and cart, not only at checkout (stating shipping costs is a 特商法 duty).

## Payment

- **No law requires any payment method.** Choose by audience (practice).
- **Cards + EMV 3-D Secure:** the credit-card security guideline (5.0, 2024-03) asked every EC shop to use 3-D Secure 2 by **end of March 2025**; version 6.0 (2025-03) made it a standard measure, enforced by card acquirers and payment providers under 割賦販売法 (they can end the contract). Use a provider that runs 3-D Secure 2 (Stripe, KOMOJU, SBPS, GMO, Shopify Payments all do).
- **Shopify Payments Japan** (platform): Visa, Mastercard, AmEx; JCB after review (up to 3 weeks, JPY only); Apple Pay, Google Pay, Shop Pay. **No コンビニ決済, bank transfer, PayPay or Paidy inside Shopify Payments**: those come through apps (SBPS, GMO イプシロン, KOMOJU, ペイジェント, Paidy). Bank transfer and 代引 are also possible as manual payment methods.
- **WooCommerce** (platform): WooPayments works in Japan (cards). **KOMOJU** is an official Marketplace extension (PayPay, コンビニ, local cards). **Japanized for WooCommerce** (free) adds 銀行振込 with Japanese bank fields, ゆうちょ振替, 代金引換, 店頭払い and Paidy. Plugins for SBPS / GMO-PG on wordpress.org are third-party, not official.
- **Stripe** (platform): コンビニ決済 at FamilyMart, Lawson, Ministop, Seicomart (**not 7-Eleven**), ¥120–¥300,000; PayPay ¥50–¥1,000,000, no subscriptions. Stripe checks the 特商法 page before enabling コンビニ (complete page, matching business details, shipping and cancellation terms).
- **PayPay:** through a PayPay-partner provider or a direct contract with screening.
- **コンビニ決済:** which stores are covered depends on the provider (Stripe has no 7-Eleven; SBPS covers 7-Eleven, FamilyMart, Lawson, Ministop, Seicomart).
- **Pay-easy** is not the same as bank transfer: the buyer pays at an ATM or in online banking with numbers issued by the provider; not at konbini.
- **銀行振込** (practice): show bank, branch, account type, number and holder name in katakana on the thank-you page and in the order mail, with the payment deadline and who pays the transfer fee.
- **Paidy (あと払い):** the bill comes on the 1st–5th of next month, payable by the 27th; merchant review about 10 business days.
- **Practice:** offer cards first, then PayPay / wallets, コンビニ, 後払い, 銀行振込, 代引 (older buyers still use the last two).

## Checkout fields

- **WooCommerce default** has first/last name in Western order, no フリガナ. Japanized for WooCommerce adds フリガナ, Japanese field order, postal-code fill (classic checkout only) and a delivery date + time picker. The Checkout block needs the additional-checkout-fields API instead.
- **Shopify:** name as two fields or last name only; Japan has address autocomplete; no フリガナ field by default.
- **Postal-code fill:** YubinBango (successor of ajaxzip3, MIT, data kept current) converts full-width digits. Keep the address editable after fill (`../design/japan.md`).
- **Practice:** フリガナ helps call centres and labels; make it optional rather than blocking checkout.

## Delivery

- **Yamato 宅急便 time slots:** 午前中 (8–12), 14–16, 16–18, 18–20, 19–21; free; 12–14 and 20–21 ended in 2017.
- **Sagawa** (private addresses): 午前中, 12–14, 14–16, 16–18, 18–20, 18–21, 19–21; business addresses use 飛脚ジャストタイム便.
- **Practice:** show only your carrier's slots; delivery date and time slot are separate fields; blackout days and lead times belong in the shipping plugin's settings.
- **置き配:** Yamato EAZY (EC parcels; not for クール, 代引, 着払い); Sagawa since 2024-09-02 (up to 260 cm / 50 kg, no liability in principle). The 国土交通省 plans 置き配 as a standard service from FY2026 (secondary report; date not verified). Practice: offer a "置き配OK" choice and pass it to the carrier through the shipping plugin.
