# Japanese law for websites — what to watch for

Status: **景品表示法 sections verified 2026-10-11** (stealth-marketing designation 内閣府告示第19号 of 2023-03-28 in force 2023-10-01; the 消費者庁 No.1表示 report of 2024-09-26; the amended 景品表示法 in force 2024-10-01) through law-firm and trade-press summaries of the 消費者庁 texts; the 消費者庁 page itself refused the connection twice, so quote the primary text before relying on wording (`SOURCES.md`). 薬機法, 定期購入 details, 個人情報保護法 (利用目的, 第三者提供) and the accessibility duty remain merged practice; 特商法 表記, 最終確認画面 and 外部送信 checked 2026-10-15 on 消費者庁 and 総務省 pages. **A checklist, not legal advice.** When a request touches these areas: do the safe thing, name the risk, suggest the client checks with a legal expert. Never invent facts, results or reviews.

## 景品表示法 (misleading representations)

- **優良誤認:** no claim that quality or effect is better than it is. 「業界No.1」「最高品質」「絶対」「必ず」「100%」 need objective proof; remove or soften otherwise.
- **No.1表示** (消費者庁 report 2024-09-26, treated as the de-facto guideline; no separate guideline planned): the claim needs an objective basis in four parts: a fair choice of the compared products or services, a fair choice of respondents, a fairly run survey (no fixing your own option at the top, no leading questions), and a claim that matches what the survey measured. Show 調査機関・調査期間・対象 next to the claim. An image survey of a few people is not enough; 「顧客満足度No.1」 from a bought ranking is a known enforcement target.
- **有利誤認:** prices and terms must not look better than they are. 「今だけ」「期間限定」 only if true. Conditions (「初回のみ」「送料別」「税込/税抜」) clear and next to the price, not in small print (打消し表示).
- **二重価格** (「通常価格 ¥10,000 → ¥5,000」): the "normal price" must be a price the item was really sold at for a meaningful recent period.
- Consumer prices include tax (総額表示): 「¥11,000（税込）」.
- Since the amendment in force **2024-10-01**, deliberate 優良誤認 / 有利誤認 can be punished directly (fine up to ¥1,000,000) in addition to 措置命令 and 課徴金; a confirmed-measures procedure (確約手続) was also introduced.

## ステルスマーケティング規制 (in force 2023-10-01)

Designated as 不当表示 under 景品表示法 5条3号 (内閣府告示第19号, 2023-03-28). Two conditions make a post a violation: it is **the business's own representation** (the business was involved in the content: payment, product supplied with expectations, instructions, an ongoing relationship) **and** ordinary consumers cannot tell that it is (要件①②). Accepted labels per the 運用基準: 「広告」「プロモーション」「PR」 or a plain sentence such as 「A社から商品の提供を受けて投稿しています」, placed where it is seen, not hidden in tags or small print. The **advertiser** is liable (措置命令), not the influencer. Applies to posts started before the date that remain visible. Never write reviews or testimonials "as a customer"; testimonials must be real and labelled when rewarded.

## 薬機法 / 健康増進法 (health, beauty, supplements, cosmetics)

- Cosmetics and health foods must not claim to treat, cure or prevent illness: 「治る」「改善」「アトピーに効く」「痩せる」「免疫力アップ」 → flag.
- Only approved claims for the product category; no before/after promises.
- Clinics have their own strict rules (医療広告ガイドライン): no patient testimonials about results, no before/after photos without the required details. Flag all clinic content for a human check.

## 特定商取引法 (online sales)

Shops need a page 「特定商取引法に基づく表記」: seller name, address, phone, responsible person, prices and shipping, payment method and timing, delivery time, return and cancellation rules. Subscriptions (定期購入) must show total cost and cancellation terms clearly on the final confirmation screen. Never remove or hide these.

Checked 2026-10-15 against the 消費者庁 特定商取引法ガイド (通信販売 and its Q&A):
- Applies to 通信販売 of goods **and services** (役務): online shops, paid online services, paid bookings and courses sold on the site. A site that only takes inquiries does not need it.
- Items (法11条): price incl. 送料, other costs, payment timing and method, delivery or service timing, 返品特約 (whether returns are possible, period, who pays shipping; **can never be omitted**), seller's legal name (not only a 屋号), address, phone, for a company the 代表者 or 業務責任者 name, and software or system requirements for digital goods.
- Name, address, phone and representative may be left off the page **only** if it says they are sent 「請求があれば遅滞なく」 and that really happens before purchase. Individuals may show a platform or virtual-office address under the Q&A's conditions (clarified 2021).
- **最終確認画面** (法12条の6, since 2022-06-01) for every online sales contract: quantity, price and shipping, payment timing and method, delivery timing, application deadline if any, cancellation terms.

## 個人情報保護法, cookies, email

- Every form that collects personal data needs a privacy policy link (利用目的) and, in practice, a consent checkbox.
- Do not add tracking tags, chat widgets or third-party scripts on your own: they send visitor data to others and may have to be listed in the 外部送信 policy. A person decides.
- **外部送信規律** (電気通信事業法, since 2023-06-16; checked 2026-10-15 on the 総務省 page) covers 電気通信事業者 and 第三号事業 operators: SNS, search, news or curation media, online malls, apps and similar services. A site that only presents its own company (and in practice a shop selling only its own goods) is outside it; for those, listing the tools is good practice. Sites in scope must publish what is sent, to whom and for what purpose (a table in the privacy policy: tool, data, recipient, purpose) or get consent / offer opt-out. It is a **notice duty, not a consent duty**.
- Cookie **consent** banners: required when the site targets people in the EU/UK (pages, prices or shipping aimed at them) or tracks their behaviour (GDPR art. 3(2), ePrivacy); merely receiving EU visits does not bring a Japanese site into scope. In Japan consent is needed only when a recipient will link the data to a person (個人情報保護法 個人関連情報, PPC FAQ; the recipient obtains it, the site confirms it). Whether a site needs one is the owner's decision.
- Newsletter sign-ups need opt-in consent (特定電子メール法).

## Accessibility duty

Since April 2024 private businesses must provide reasonable accommodation to people with disabilities (障害者差別解消法). JIS X 8341-3 (WCAG 2.x AA) is the usual web standard: `../design/accessibility.md`.

## Copyright and portrait rights

Do not copy text or images from other sites. Photos of people need consent (肖像権), above all students and children; use images the site already has or the client provides.

## What changed in pass 2 (2026-10-11)

- ステマ規制: legal basis, the two conditions, accepted labels, who is liable.
- No.1表示: the 2024 report's four conditions.
- 2024-10-01 amendment (direct fines) added.
- Not yet verified: 薬機法, 定期購入 details, 個人情報保護法 (利用目的, 第三者提供), 障害者差別解消法 wording. 2026-10-15: 特商法 表記 items, omissions and the 最終確認画面 checked on the 消費者庁 特商法ガイド; 外部送信規律 checked on the 総務省 page.
