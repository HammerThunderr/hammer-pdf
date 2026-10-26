# Hammer PDF

31 PDF tools in a single HTML file. Everything runs in the browser, so files are never uploaded to a server.

## Tools

| Group | Tools |
|---|---|
| Organize | Merge, Split, Remove pages, Extract pages, Organize (drag to reorder, rotate, delete), Scan to PDF |
| Optimize | Compress, Repair, OCR |
| Convert to PDF | JPG/PNG, Word (.docx), PowerPoint (.pptx), Excel (.xlsx/.xls/.csv/.ods), HTML |
| Convert from PDF | JPG/PNG, Word (.docx), PowerPoint (.pptx), Excel (.xlsx), PDF/A, Markdown |
| Edit | Rotate, Page numbers, Watermark (text or image), Crop, Edit (text, white-out, highlight, boxes), Fill forms |
| Security | Unlock, Protect (password), Sign (draw or type), Redact, Compare two versions |

Every tool has its own link, e.g. `index.html#merge`, `#pdf-to-word`, `#sign`.

## Deploy on GitHub Pages

1. Create a repo (e.g. `HammerThunderr/hammer-pdf`) and add `index.html` and this README.
2. Repo **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder `/ (root)`.
3. The site appears at `https://hammerthunderr.github.io/hammer-pdf/` after a minute or two.

There is no build step. Any static host (Netlify, Cloudflare Pages, Firebase Hosting) works the same way: upload `index.html`.

## Libraries

Loaded from cdnjs/jsDelivr on demand (only when a tool needs them), all pinned:

- pdf-lib 1.17.1: creating and modifying PDFs
- pdf.js 3.11.174: rendering pages and extracting text
- jsPDF 2.5.1: password protection
- JSZip 3.10.1: .docx output and ZIP downloads
- mammoth 1.6.0: reading .docx
- SheetJS 0.18.5: reading and writing spreadsheets
- html2canvas 1.4.1: laying out Word, Excel and HTML pages
- PptxGenJS 3.12.0: .pptx output
- tesseract.js 5.1.1: OCR (downloads a 10–20 MB language model on first use)

## Known limits (browser-only)

- **Word / Excel / HTML to PDF** render pages as images. Text is not selectable in the result, and complex Word layouts (columns, text boxes, headers/footers) are simplified.
- **PowerPoint to PDF** draws slide text, solid-fill shapes and pictures. Theme colours, charts, tables and SmartArt are not reproduced.
- **PDF to Word, Editable text** keeps headings, paragraphs and bullets but drops images. **Exact look** keeps the appearance but is not editable.
- **Compress Medium/Strong**, **Protect**, **Unlock** and redacted pages are rebuilt as images. Compress falls back to the lossless result if images would be bigger.
- **Protect** uses standard PDF password encryption from jsPDF. Fine for everyday use; not intended for high-security documents.
- **PDF/A** adds PDF/A-2b identification and XMP metadata but does not embed colour profiles or check fonts. Verify with veraPDF if certification matters.
- **Redact** rasterises only the pages you mark, so the hidden text is truly gone; other pages are untouched.
- Text you add (Edit, page numbers, watermark, forms) uses Helvetica, which covers Western European characters only.
- Old binary `.doc` and `.ppt` files must be saved as `.docx` / `.pptx` first.
