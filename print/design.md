# Print design: type, layout, flyer anatomy

Status: **verified 2026-10-20** where marked fact (JLReq, vendor guides, UD and CUD guidance, 総務省, Poynter, NN/g, Denso Wave); the rest is practice from Japanese design columns and our own defaults (`SOURCES.md`). Print production: `production.md`. Law: `law.md`. Web typography is different (`../design/japan.md`): print text is set in pt or Q, not px.

## Type sizes (Japanese, A4)

| Element | Size | Source |
|---|---|---|
| Catchphrase | 24–60 pt (vendor guide: キャッチ 40–60 pt on A4) | practice / vendor column |
| Section heading | 14–18 pt | practice |
| Lead | 10–11 pt | practice |
| Body | **10–11 pt** for flyers (vendor guide: 基準 10.5–11 pt); 9 pt is common in books (JLReq), 8 pt the book minimum; premium brochures may go to 9 pt | fact (JLReq, vendor guide) |
| **Seniors, low vision** | **12 pt general, 14 pt for older or low-vision readers** (総務省 and municipal UD guidelines) | fact |
| Captions, notes | 6–8 pt; **never below 6 pt** (ラクスル) | fact |
| Real-estate required notes | ≥ 7 pt; some warnings ≥ 16 pt (`law.md`) | fact |

The claim that "8.5–9 pt is the sweet spot and over 11 pt looks amateurish" has no source: choose by reader, not by fashion.

- **Line spacing (JLReq):** the gap between lines is half to one character (line pitch 1.5–2.0×); a full-character gap for lines longer than about 35 characters. Practice: body 1.6–1.8×.
- **Line length:** about 40 characters at most for horizontal Japanese (`../design/japan.md`).
- **Headlines:** `palt` (proportional metrics) on headlines only; body stays ベタ組み. Letter-spacing figures like "+2–6 %" have no source: kern by eye.
- **Numbers** (prices, phone, dates) in a Latin face sized to match the Japanese (practice).
- **UD fonts** (Morisawa BIZ UD, UD新ゴ, UD黎ミン) for public, school, clinic and senior audiences: Morisawa cites low-vision studies; BIZ UD's evidence is a company survey (practice).
- **Mincho / Gothic:** Mincho for refined headlines, Gothic for specs and small text (`../design/japan.md`).

## Grid and whitespace (practice)

- A modular grid that every photo edge and text block snaps to (JAGAT describes 版面 and grids; column counts are a house choice): A4 12 columns, one panel = one grid unit on a tri-fold.
- **Colour ratio** 70 / 25 / 5 (base / main / accent) is a common Japanese rule of thumb ("きっちり守る必要はない"); no source gives a whitespace percentage.
- **Two styles:** mass-retail chirashi (dense, red and yellow, price bursts, pop fonts) and premium flyers (generous whitespace, strict grid, Mincho headlines, one strong photo). Choose by audience and brand, not by taste.

## Eye flow

- Japanese ad columns use **Z** for horizontal layouts and **N** (right-top to left-bottom) for vertical text; no Japanese print eye-tracking backs either (NN/g's F-pattern is for web). What print eye-tracking does show (Poynter, 600 readers): **large photos and headlines are seen first**.
- **Practice:** one dominant photo and one headline; the reply action (QR, phone) in a fixed corner; a vertical Mincho catchphrase with horizontal body text works for premium Japanese brands (brand examples in circulating articles are unverified).

## Two-sided A4 flyer blueprint (practice)

**Front: stop and turn over**
1. Top: who it is for (「〇〇区でリフォームをお考えの方へ」), logo, one proof.
2. Middle: one large photo (about half the page) and the main promise.
3. Lower: three benefits.
4. Bottom band: the offer and 「詳しくは裏面へ」.

**Back: convince and act**
1. Services and **tax-inclusive prices** (law).
2. Proof: real voices and cases (labelled when rewarded; **none for clinics**, `law.md`), steps 1-2-3.
3. Map and company details: a **simplified drawn map** (nearest station, 2–3 landmarks); copying Google Maps or GSI maps has limits (`law.md`); walking times in real-estate ads follow the 80 m = 1 minute rule.
4. Action box: QR (15–20 mm, `production.md`) with a one-line reason to scan, phone number in large figures, hours, closed days, address.

A recent survey: people stop for **information relevant to them (44 %)** and **coupons (43 %)** (2026-07).

## Colour and accessibility (fact: CUDO, 総務省)

- About 1 in 20 men and 1 in 500 women have a colour-vision difference. Avoid red/green, red/black and white/yellow pairs; use orange-red (朱色) instead of pure red; never carry meaning by colour alone (add a label or shape). CUDO publishes a recommended 20-colour set.
- Contrast and size: body 12 pt for the general public, 14 pt for older readers in public material.

## Copy (practice)

- The 3-second rule: one message, a concrete number, the benefit first. Structures: 新PASONA (`../marketing/landing-pages.md`), AIDMA.
- Japanese claims law applies in full (`law.md`).

## Measuring response (fact and practice)

- Response rate = responses ÷ copies distributed. Typical: posting 0.01–0.3 %, QR scans 0.3–0.5 % (vendor columns).
- Give every medium its own trace: a QR with UTM (`utm_source=flyer&utm_medium=print&utm_campaign=<name>`), a coupon code brought to the shop, a dedicated phone number (call tracking). Report it like web campaigns (`../seo-geo/reporting.md`).
