#### Description

The `text` command extracts text from an image using optical character recognition (OCR) powered by Tesseract. It reads the input image, runs OCR, and outputs the recognized text to stdout.

Supports all image formats that Tesseract accepts: PNG, JPEG, TIFF, BMP, GIF, and WebP.

For best results, use clean images with high contrast between text and background. Preprocessing with `aux4 image convert` or `aux4 image resize` can improve accuracy on low-resolution inputs.

#### Usage

```bash
aux4 image text <file> [--lang <language>] [--psm <mode>]
```

--lang  OCR language code (default: eng). Use `tesseract --list-langs` to see installed languages.
--psm   Page segmentation mode (default: 3). Controls how tesseract interprets the image layout:
  - 0: Orientation and script detection (OSD) only
  - 1: Automatic page segmentation with OSD
  - 2: Automatic page segmentation, but no OSD or OCR
  - 3: Fully automatic page segmentation, but no OSD (default)
  - 4: Assume a single column of text of variable sizes
  - 5: Assume a single uniform block of vertically aligned text
  - 6: Assume a single uniform block of text
  - 7: Treat the image as a single text line
  - 8: Treat the image as a single word
  - 9: Treat the image as a single word in a circle
  - 10: Treat the image as a single character
  - 11: Sparse text — find as much text as possible in no particular order
  - 12: Sparse text with OSD
  - 13: Raw line — treat the image as a single text line, no hacks

#### Example

```bash
aux4 image text receipt.png
```

```text
GROCERY STORE
123 Main Street
Milk        $3.99
Bread       $2.49
Total       $6.48
```

Extract a single line from a label:

```bash
aux4 image text label.png --psm 7
```

```text
SKU-12345-XL
```

Extract Spanish text:

```bash
aux4 image text carta.jpg --lang spa
```

```text
Estimado cliente,
Gracias por su compra.
```
