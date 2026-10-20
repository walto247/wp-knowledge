# Agency Standard Operating Procedure: Client File Intake

All incoming client files must be placed, unchanged, into the project's untracked `tmp/intake/raw/` folder; everything produced from them goes into `tmp/intake/extracted/` (workspace house rule 7). Agents must follow these format-specific protocols to minimize token usage, avoid manual owner labor, and prevent git repo bloat.

## 1. Spreadsheets (.xlsx, .xls, .csv)
* **Data-Only Tables:** Parse on disk using Python (`pandas` or `openpyxl`). Never dump hundreds of raw rows into the chat window. Extract only target columns (URLs, slugs, IDs, text strings).
* **Visual Spreadsheets (Screenshots, Image Grids, Layout Mappings):** Extract embedded images to `tmp/intake/extracted/`. Build `tmp/review.html` matching each image thumbnail to its row text/cell context. Launch `tmp/review.html` in the host browser for visual approval.

## 2. Word Documents (.docx, .doc)
* **Universal Clean Text Extraction:** Extract document text using Python (`python-docx`) or Pandoc into clean, portable plain text or standard Markdown.
* Do NOT format into CMS-specific proprietary blocks (e.g., Gutenberg comments) unless explicitly requested.
* Preserve standard hierarchy: `# Heading 1`, `## Heading 2`, bullet lists, bold text, and hyperlinks.
* Extract any embedded photos directly into `tmp/intake/extracted/`.

## 3. Presentations & Slide Decks (.pptx, .key, Google Slides PDF)
* **Text Extraction:** Extract slide title, body copy, and speaker notes slide-by-slide (`Slide 1: ...`, `Slide 2: ...`) into a single plain text file `tmp/intake/extracted/slides-text.txt`.
* **Image & Layout Extraction:** Extract embedded pictures using `python-pptx` to `tmp/intake/extracted/`. Compile slide images and extracted text into `tmp/review.html` and launch the browser preview.

## 4. PDFs (.pdf - Briefs, Brand Guidelines, Invoices)
* **Text & Specs:** Extract text using `pdfplumber` or `pypdf` directly into `tmp/intake/extracted/pdf-extracted.txt`.
* **Visual / Design Guides:** Rasterize pages to images (`pdftoppm -png` or `pdf2image`) in `tmp/intake/extracted/pdf-pages/` and present them via `tmp/review.html`.

## 5. Image Assets (.jpg, .png, .webp, .svg, .gif)
* **Inspection:** Check dimensions, file sizes, and aspect ratios via Python `Pillow` or ImageMagick.
* **Format Conversion:** Under workspace house rules, convert web imagery to `.webp` into `tmp/intake/extracted/` while keeping originals in `tmp/intake/raw/`.
* **Approval Dashboard:** Never output a table of filenames. Generate `tmp/review.html` displaying actual image thumbnails, dimensions, target destination, and status. Launch the browser preview.

## 6. Code & Bug Reports
* **Search First:** Never ask the owner for line numbers or file paths. Use `grep`, `find`, or AST search tools to locate errors or functions.
* **Context Limit:** Display only the relevant 10–20 line snippet with line numbers. Do not output entire 500-line files into the chat.

## 7. Archives (.zip, .tar.gz)
* **Isolation:** Keep the archive itself in `tmp/intake/raw/` and always extract it into a dedicated subfolder: `tmp/intake/extracted/<archive-name>/`.
* **Safety:** Inspect archive contents before unzipping to avoid directory bomb explosions or tracking hidden system files (`__MACOSX`, `.DS_Store`).

## 8. Audio & Video Memos (.mp3, .m4a, .mov, .mp4)
* Never commit media files to Git.
* Inspect duration and specs with `ffprobe`.
* Extract audio tracks or run local transcription (Whisper), saving output to `tmp/intake/extracted/transcript.txt`.
