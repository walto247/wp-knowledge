# Print: flyers (チラシ), leaflets and pamphlets

Status: **verified 2026-10-20** against JIS/ISO paper sizes, the data guides of ラクスル, グラフィック, プリントパック and プリントネット, Japan Color, W3C (css-page-3, JLReq), Puppeteer/Playwright, Vivliostyle and Prince docs, Denso Wave, 国税庁, 消費者庁, 厚生労働省, 不動産公正取引協議会, Google Geo Guidelines, 国土地理院, 個人情報保護委員会 and Supreme Court rulings (`SOURCES.md`). Marked **fact** (with a source) or **practice** (our house default). Web design rules stay in `../design/`.

## Files

| File | What |
|---|---|
| `production.md` | Sizes, bleed and safe zones, folds and panel widths, booklets, colour (CMYK, ink limit, black), resolution, fonts, PDF/X, paper, QR codes, proofs |
| `design.md` | Type sizes and spacing, grids and whitespace, the two styles (retail vs premium), eye flow, front/back blueprint, maps, accessibility, copy, measuring response |
| `html-to-pdf.md` | How a code agent builds print files from HTML/CSS: what Chromium can and cannot do, the CMYK/PDF/X routes, crop marks, Japanese typography |
| `tri-fold.md` | A4 巻き三つ折り blueprint: 97/100/100 panel order for 左開き and 右開き, reading order, panel-by-panel content, fold rules, paper |
| `law.md` | Law for printed ads: 総額表示, 景表法, 医療広告, 不動産 rules, 特商法, personal data on reply forms, maps, photos, posting |

## Words (fact, industry usage)

- **チラシ / フライヤー:** one unfolded sheet, one or two sides.
- **リーフレット:** one sheet **folded** (二つ折り, 巻き三つ折り, Z折り), not bound.
- **パンフレット:** a **bound** small booklet (usually 中綴じ, 8 pages and more). Usage is loose: many vendors call a folded sheet a "三つ折りパンフレット". Ask the client which product they mean.
- **冊子:** booklet (UNESCO: 5–48 pages; 49+ is a book). **カタログ:** named by use (a product list), not a format.
- **会社案内:** a company profile, usually a folded leaflet or a 中綴じ booklet.

## The five rules that matter most

1. Build at **trim size + 3 mm bleed** on every side; keep text **at least 3 mm inside the trim** (vendor minimum; our default 10 mm).
2. **CMYK**, total ink **≤ 300 %**, small text and thin lines in **K100 only**; images **350 dpi** at printed size.
3. A browser (Chromium, Puppeteer, Playwright) makes **RGB PDFs only**: either send RGB to a vendor that converts, or use Vivliostyle / Prince for CMYK and PDF/X-1a (`html-to-pdf.md`).
4. Every printed price is **tax-inclusive** (総額表示); clinic and real-estate flyers have their own strict rules (`law.md`).
5. Order a proof (校正) before a large run, and count the response (QR with UTM, coupon code, dedicated phone).
