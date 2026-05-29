# aux4/image-text

Extract text from images using OCR powered by [Tesseract](https://github.com/tesseract-ocr/tesseract).

This package extends the `aux4 image` command group with a `text` subcommand for optical character recognition. When installed alongside `aux4/image`, both packages share the same `image` profile and their commands merge seamlessly.

## Install

```bash
aux4 aux4 pkger install aux4/image-text
```

### Requirements

- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) (auto-installed if missing)

## Usage

```bash
aux4 image text <file> [--lang <language>] [--psm <mode>]
aux4 image pdf <file> [--input <file2> ...] [--output <name>] [--lang <language>]
```

## Commands

| Command | Description |
|---------|-------------|
| `aux4 image text` | Extract text from an image using OCR |
| `aux4 image pdf` | Generate a searchable PDF from one or more images |

## Options

### --lang

OCR language code (default: `eng`). Use `tesseract --list-langs` to see installed languages.

### --psm

Page segmentation mode (default: `3`). Controls how tesseract interprets the image layout:

| Mode | Description |
|------|-------------|
| 0 | Orientation and script detection (OSD) only |
| 1 | Automatic page segmentation with OSD |
| 2 | Automatic page segmentation, but no OSD or OCR |
| 3 | Fully automatic page segmentation, but no OSD (default) |
| 4 | Assume a single column of text of variable sizes |
| 5 | Assume a single uniform block of vertically aligned text |
| 6 | Assume a single uniform block of text |
| 7 | Treat the image as a single text line |
| 8 | Treat the image as a single word |
| 9 | Treat the image as a single word in a circle |
| 10 | Treat the image as a single character |
| 11 | Sparse text — find as much text as possible in no particular order |
| 12 | Sparse text with OSD |
| 13 | Raw line — treat the image as a single text line, no hacks |

## Examples

Extract text from a screenshot:

```bash
aux4 image text screenshot.png
```

Extract a single line from a label:

```bash
aux4 image text label.png --psm 7
```

Extract text in Spanish:

```bash
aux4 image text documento.png --lang spa
```

Generate a searchable PDF:

```bash
aux4 image pdf scan.png
aux4 image pdf scan.png --output archived-scan
```

Create a multi-page PDF from multiple images:

```bash
aux4 image pdf --input page1.png --input page2.png --input page3.png --output document
```

## Language Packs

Tesseract supports many languages. Install additional language packs:

```bash
# macOS
brew install tesseract-lang

# Ubuntu/Debian
apt install tesseract-ocr-spa tesseract-ocr-deu tesseract-ocr-fra
```

Common language codes: `eng` (English), `spa` (Spanish), `deu` (German), `fra` (French), `por` (Portuguese), `ita` (Italian), `jpn` (Japanese), `chi_sim` (Chinese Simplified).

## License

Apache-2.0
