# Selling abroad from Japan: duties, taxes, shipping, currencies

Status: **verified 2026-10-19** against ICC (Incoterms), EU Commission and Council, HMRC (gov.uk), US CBP, ATO, Japan Post, 国税庁, Shopify Help, Stripe, PayPal and WooPayments docs (`SOURCES.md`). Marked **law** (as of 2026-10-19), **platform** or **practice**. Rules for foreign destinations change fast: re-check before advising a client. Japanese checkout: `japan-checkout.md`.

## Who pays duties: DAP or DDP

- **Fact:** Incoterms 2020 has 11 rules, including **DAP** (buyer pays import duties and taxes) and **DDP** (seller pays them). "DDU" was removed in Incoterms 2010 and replaced by DAP; carriers and shops still say DDU.
- **Practice:** say which one applies **before payment and in the order mail**. DAP: "Import duties and taxes may be charged on delivery by your customs authority; the carrier may add a fee." DDP: "Duties and taxes are included; nothing to pay on delivery."
- **Platform, Shopify:** collects estimated duties and import taxes at checkout (needs HS codes and a carrier that prints DDP labels; per country DDP or DAP; fee about 0.85 % with Shopify Payments). **WooCommerce** has no built-in duty calculation: use a landed-cost service (Zonos, Avalara or a carrier's) (practice).

## Destination rules (law, as of 2026-10-19)

- **EU:** VAT on consignments up to **€150** can be charged at checkout through IOSS (a non-EU seller needs an EU intermediary); otherwise VAT is collected at import. **New:** from **2026-07-01 to 2028-07-01** a flat **€3 customs duty per item type** applies to every B2C consignment up to €150 (5 T-shirts = €3; a T-shirt and a watch = €6). Product identifiers required from 2026-11-01; an extra EU handling fee is proposed. After 2028-07-01 normal duty from the first euro.
- **UK:** consignments up to **£135** sold directly to consumers: the seller charges UK VAT at checkout and must register; through a marketplace, the marketplace does it; above £135 VAT and duty at import.
- **USA:** the **$800 duty-free limit is suspended** for all countries since 2025-08-29 and indefinitely by CBP rules of 2026-06-24; every goods shipment pays duty. A law repealing it permanently from 2027-07-01 is reported (secondary).
- **Australia:** 10 % GST on imported goods up to A$1,000, charged by the overseas seller once Australian sales reach A$75,000 a year (simplified registration); above A$1,000 at the border.
- **Practice:** small shops below these thresholds can stay DAP and tell the buyer; above them register (IOSS intermediary, HMRC, ATO) or let Shopify or a landed-cost provider handle it.

## Shipping from Japan (Japan Post facts)

- **国際エアパケット** (renamed from 国際eパケットライト on 2026-06-01): up to 2 kg, tracked, mailbox delivery, labels only from 国際郵便マイページ, no cash or valuables. 国際eパケット ended in 2023.
- **小形包装物:** registered mail option ended 2025-12-31. EMS (speed, insurance) and 国際小包 continue.
- **USA:** goods mail stopped 2025-08-27 and restarted in steps; since **2026-10-15** accepted at almost all post offices, but every goods item up to US$2,500 needs advance registration with US customs through **Zonos or SafePackage**, a "DDP-" number on the label and **duty prepaid by the sender** (gifts ≤ US$100 and documents also registered). Above US$2,500 the importer pays.
- **Couriers** (practice): DHL Express, FedEx, UPS for speed, B2B and now often the US; they offer sender-paid duties.
- **Not allowed or restricted:** dangerous goods by any mode (sprays, perfume, nail polish, e-cigarettes, power banks, strong alcohol); lithium batteries only inside equipment and only to some countries; per-country bans (alcohol, tobacco, meat or plant products, even in instant noodles). A customs form always (via マイページ).
- **Addresses:** Japan Post asks for Roman letters and Arabic numerals in principle. Practice: Latin-only checks on the **international** checkout only; the sender block in English; leave the Japanese domestic form as it is.

## Export tax (law)

- **輸出免税:** exported goods carry 0 % 消費税 if records are kept for 7 years: the export permit for customs-cleared goods and for mail over ¥200,000; for mail up to ¥200,000 the post office receipt and a copy of the label (sender, items, quantity, value, recipient, date). Since **2026-10-01**: if paid in cash or by someone other than the buyer, also keep the destination's import clearance document.
- **Practice:** no 消費税 in the cart for non-Japanese addresses (zero-rate class); English invoice with HS code, value and origin "Japan".

## Currencies (platform)

- **Stripe** (Japanese account): shows and charges in 135+ currencies, pays out in the bank's currency; Adaptive Pricing adds a 2–4 % exchange margin to the customer's price (none to the shop); refunds are converted at the current rate; JCB, Diners, Discover in JPY only.
- **PayPal:** 25 currencies including JPY; set receiving preferences for currencies you do not hold, or payments stay pending.
- **WooPayments** Multi-Currency changes only what the customer sees and pays; the payout stays in the shop's currency.
- **Shopify Markets** local currencies: not verified this time.
- **Practice and law:** charge in the currency you display. Showing an estimate in one currency and charging another without saying so misleads buyers (景品表示法 有利誤認): either charge in the shown currency or state clearly that the charge is in JPY.
