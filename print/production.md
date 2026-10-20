# Print production: sizes, folds, colour, files

Status: **verified 2026-10-20** (`SOURCES.md`). Vendor numbers are from ラクスル, グラフィック, プリントパック and プリントネット; always open the chosen vendor's template for the job.

## Sizes (fact)

| Size | Trim (mm) | With 3 mm bleed (mm) | Typical use |
|---|---|---|---|
| A4 | 210 × 297 | 216 × 303 | standard flyer, handout |
| A5 / A6 | 148 × 210 / 105 × 148 | 154 × 216 / 111 × 154 | small flyer, postcard |
| JIS B5 | 182 × 257 | 188 × 263 | small shop insert |
| JIS B4 | 257 × 364 | 263 × 370 | **most common 新聞折込** (inserted flat) |
| JIS B3 | 364 × 515 | 370 × 521 | 折込, folded in half to B4 |
| US Letter | 215.9 × 279.4 | 221.9 × 285.4 | English-market handouts |

- Japan uses **JIS B**, larger than ISO B (ISO B4 = 250 × 353). Prince's `B4` keyword is ISO: write `257mm 364mm`.
- 新聞折込: B4 flat is standard; B3 is folded to B4, B2 folded in four; A4/B5 are usually priced as B4 (practice; confirm with the 折込会社, there is no public national table).

## Bleed, safe zone, tolerances

- **Bleed (塗り足し): 3 mm** on all four sides (all four vendors). Backgrounds and photos run to the bleed edge.
- **Safe zone:** vendors ask text **≥ 3 mm** inside the trim (グラフィック 2–3 mm); cutting shifts about 1–2 mm. **Practice:** 10 mm for flyers, 15 mm premium, 18 mm luxury.
- Export exactly trim + 6 mm: プリントパック stops a job when the size is off by more than 1.0 mm.
- No thin even border near the trim (a 1–2 mm shift shows); if one is used, make it ≥ 3 mm wide.
- Rounded-corner products: submit square artwork with square bleed.

## Folds and panel widths (fact, ラクスル table)

| Fold | A4 panels (mm) | Notes |
|---|---|---|
| 二つ折り | 2 × 148.5 (A4) · A3 → A4: 2 × 210 | keep text off the crease (practice: ≥ 7–10 mm) |
| **巻き三つ折り** (roll fold) | **97 / 100 / 100** | the panel that folds inside is 2–3 mm narrower so it lies flat; A3: 138/141/141, A5: 68/71/71 |
| 外三つ折り / Z折り | 99 / 99 / 99 | equal panels |
| DM折り, 観音折り | per vendor (プリントパック B5–A2) | use the vendor's template |

- Build at the open (展開) size on the vendor's template; which folds are allowed depends on paper weight. Ask for **スジ入れ** (scoring) on heavy paper (practice: 135 kg and up).

## Booklets (中綴じ)

- Pages in **multiples of 4** (プリントパック: 8–64; cover counts as 4). Blank pages count.
- Keep text ≥ 3 mm from the binding and the trim (vendor minimum; practice: ≥ 10 mm at the gutter). Inner pages are trimmed more at the fore-edge (creep, about 1 mm per 16 pages).
- Build as single pages or spreads as the vendor asks; spreads need an operator check at ラクスル.

## Colour (fact)

- **CMYK.** Standard profiles: **Japan Color 2001 Coated** (Adobe's Japanese default, TAC 350 %) and **Japan Color 2011 Coated** (ISO 12647-2 paper type 1, used by グラフィック's conversion service). Uncoated 2001: 310 %.
- **Total ink:** ラクスル asks ≤ 300 % and reduces data above 350 %; グラフィック ≤ 350 % coated, ≤ 300 % matte/上質; プリントパック: above 300 % may not dry. **Our cap: 300 %.**
- **Rich black** for large black areas: C50 M40 Y40 K100 (ラクスル) or C60 M40 Y40 K100 (グラフィック); not C30M30Y30. Never 4-colour solid (C100M100Y100K100) or "registration" colour.
- **Small text and thin lines: K100 only.** RGB black (0,0,0) becomes 4-colour black and blurs. K100 is overprinted by the vendor's RIP; a large K100 box over a photo lets the photo show through: use rich black there.
- **White with overprint disappears**; white cannot be printed as ink on standard products. Do not set overprint attributes in data.
- Bright RGB greens, blues and fluorescent colours look duller in CMYK. Brand spot colours: Japanese printers use **DIC** numbers; PANTONE is often not accepted.

## Images, lines, type minimums (fact)

- Photos **350–400 dpi** at placed size (posters ~200 dpi); 1-bit line art **1,200 dpi**; greyscale 600 dpi.
- **Lines ≥ 0.3 pt (0.1 mm)** (ラクスル; グラフィック ≥ 0.25 pt); thinner lines fade or are widened by the data check. Reversed (white) lines ≥ 0.5 pt (practice).
- **Text ≥ 6 pt** (ラクスル); reversed text ≥ 7 pt in a bold weight (practice).
- Units: 1 Q (級) = 0.25 mm; 1 pt = 0.3528 mm; 14 Q ≈ 10 pt.

## Files

- Fonts **embedded** (PDF) or **outlined** (Illustrator, ラクスル asks for outlines; プリントパック "in principle").
- **PDF/X-1a** is the common denominator in Japan (グラフィック preset; プリントネット accepts only X-1a); X-4 where the vendor's workflow handles transparency. プリントパック wants PDF 1.4 with trim marks, no RGB.
- ラクスル and グラフィック convert RGB data to CMYK (ラクスル free, グラフィック paid, Japan Color 2011): the colour changes; the customer approves.
- Do not edit the PDF in Acrobat after export; two-sided flyer = one 2-page PDF.

## Paper (fact and practice)

- Weight: 連量 (kg per 1,000 四六判 sheets) ≈ g/m² × 0.86. コート 73 kg ≈ 85 g/m², 90 kg ≈ 105, 110 kg ≈ 128, 135 kg ≈ 157.
- Typical (ラクスル): flyer **90 kg** coat; 新聞折込 58–73 kg; premium flyer 110 kg; brochures and pamphlets 110–135 kg; 中綴じ cover 90–220 kg. PP lamination on 110 kg+ covers.

## QR codes (fact: Denso Wave)

- Quiet zone **4 modules** on every side; each module ≥ 4 printer dots; error correction M is standard; print "as large as possible".
- Size = (modules + 8) × module size. A short URL (version 3–4) at 0.5 mm modules ≈ 15–18 mm with its quiet zone. **Practice:** symbol 15 mm minimum, 20 mm ideal, K100 on white, never on rich black or a photo. ラクスル: ≥ 1.5 cm.

## Proofs (校正)

- 本機校正 (on the press, on the real paper) for brand colours or large runs; 簡易 / デジタル本紙校正 otherwise. Terms: 校了 (approved), 責了 (approved with fixes the printer makes), 念校 (one more check).
