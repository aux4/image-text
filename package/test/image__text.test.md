# image text

```beforeEach
magick -size 200x50 xc:white -pointsize 24 -gravity center -draw "text 0,0 'Hello World'" hello.png
```

```afterEach
rm -f hello.png
```

## should extract text from an image

```execute
aux4 image text hello.png
```

```expect:partial
Hello World
```

## should accept lang parameter

```execute
aux4 image text hello.png --lang eng
```

```expect:partial
Hello World
```

## should accept psm parameter

```execute
aux4 image text hello.png --psm 7
```

```expect:partial
Hello World
```
