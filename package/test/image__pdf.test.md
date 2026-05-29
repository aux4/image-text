# image pdf

```beforeEach
magick -size 200x50 xc:white -pointsize 24 -gravity center -draw "text 0,0 'Page One'" page1.png
magick -size 200x50 xc:white -pointsize 24 -gravity center -draw "text 0,0 'Page Two'" page2.png
```

```afterEach
rm -f page1.png page2.png page1.pdf output.pdf multipage.pdf
```

## should generate a searchable PDF

```execute
aux4 image pdf page1.png
```

```expect:partial
page1.pdf
```

## should accept output parameter

```execute
aux4 image pdf page1.png --output output
```

```expect:partial
output.pdf
```

## should create multi-page PDF from multiple images

```execute
aux4 image pdf --input page1.png --input page2.png --output multipage
```

```expect:partial
multipage.pdf
```
