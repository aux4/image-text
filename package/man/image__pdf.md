#### Description

The `pdf` command generates a searchable PDF from one or more images using OCR. The output PDF contains the original images with an invisible text layer, making the text selectable and searchable in PDF viewers.

Supports multiple input images to create multi-page PDFs. Useful for archiving scanned documents, receipts, and paper forms.

#### Usage

```bash
aux4 image pdf <file> [--input <file2>] [--output <name>] [--lang <language>]
```

--input   Additional input images (repeatable). Combined with the positional arg to form a multi-page PDF.
--output  Output PDF path without the `.pdf` extension. If not provided, uses the first input filename (e.g., `scan.png` produces `scan.pdf`).
--lang    OCR language code (default: eng).

#### Example

Single image:

```bash
aux4 image pdf scan.png
```

```text
scan.pdf
```

Multi-page PDF from multiple images:

```bash
aux4 image pdf --input page1.png --input page2.png --input page3.png --output document
```

```text
document.pdf
```
