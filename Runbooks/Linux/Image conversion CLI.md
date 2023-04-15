# Image conversion CLI

> taken from #stackoverflow https://stackoverflow.com/questions/49591274/convert-webp-to-jpg

Using ImageMagick v7:

```
magick input.webp output.jpg
```

Using ImageMagick v6:

```
convert input.webp output.jpg
```

---

If you have lots to do, use `mogrify` instead. So, say you want to convert all the WEBP images in the current directory to JPEG:

```
magick mogrify -format JPEG *.webp
```

And if you want the converted files in a directory called `OUTPUT`, use:

```
mkdir OUTPUT
magick mogrify -format JPEG -path OUTPUT *.webp
```