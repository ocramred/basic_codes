# ImageMagick
---
- [ImageMagick](#imagemagick)
  - [BASIC MEDIA INFO](#basic-media-info)
    - [Identify](#identify)
  - [CONVERT : single file editing](#convert--single-file-editing)
    - [convert transparent layer PNG to JPG](#convert-transparent-layer-png-to-jpg)
  - [MOGRIFY :  Batch convert file](#mogrify---batch-convert-file)
  - [RE-SIZE](#re-size)
    - [Re-Size Image in percentage](#re-size-image-in-percentage)
    - [Re-Size Image with given dimensions](#re-size-image-with-given-dimensions)
    - [Re-Size Image with given dimensions](#re-size-image-with-given-dimensions-1)
    - [Re-size all images in folder and keep ratio (but keep minimal width)](#re-size-all-images-in-folder-and-keep-ratio-but-keep-minimal-width)
    - [adaptive Resize](#adaptive-resize)
  - [CROP](#crop)
    - [Crop images to a specific size](#crop-images-to-a-specific-size)
    - [Crop images from an specific area](#crop-images-from-an-specific-area)
  - [TRANSFORM](#transform)
    - [Rotate image](#rotate-image)
    - [Mirror picture in a folder and rename](#mirror-picture-in-a-folder-and-rename)
  - [GIF: create gif from images in folder](#gif-create-gif-from-images-in-folder)
  - [COLORSPACE](#colorspace)
  - [Resolution](#resolution)
    - [Upscale:](#upscale)

---
## BASIC MEDIA INFO
### Identify
```bash
$ identitfy INPUTFILE
```

## CONVERT : single file editing
- [Tutorial](https://www.opensourcefeed.org/00-convert-png-to-jpg-imagemagick/) 

```bash
$ convert INPUT-IMAGE OUTPUT-IMAGE
```

```bash
# bash: simple batch job
for image in *.png ; 
do 
    convert "$image" "${image%.*}.jpg" ;
done
```
```bash
# simple one liner
$ for image in *.png ;  do convert "$image" "${image%.*}.jpg" ; done
```
### convert transparent layer PNG to JPG
```bash
$ convert original-image.png -background white -flatten -alpha off new-image.jpg
```


## MOGRIFY :  Batch convert file
> inside the picture path

```bash
$ mogrify -format jpg -quality 100 *.png
```
> move result in new folder  

```bash
$ mogrify -format png -path ./converted *.jpg
```

## RE-SIZE
### Re-Size Image in percentage
`$ convert -resize 50% INPUTFILE OUTPUTFILE`
### Re-Size Image with given dimensions
> keep original Ratio
```bash
$ convert INPUTFILE -resize 64x64 OUTPUTFILE
```
### Re-Size Image with given dimensions
>force given dimensions. could result in distortion  
```bash
$ convert INPUTFILE -resize 64x64! OUTPUTFILE
```
### Re-size all images in folder and keep ratio (but keep minimal width)
```bash 
$ mogrify -resize „1024x512^“ *.jpg
```
### adaptive Resize
```bash
$ convert INPUT  -adaptive-resize 80x80  OUTPUT
```
```bash
$ mogrify -adaptive-resize 200% -quality 100 -path ../biggest *.tif
```


## CROP
### Crop images to a specific size
`$ mogrify -gravity center -extent 1024x512 *.jpg`

> get Info: `$ mogrify -list gravity`  
> gravity choices: NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast.

### Crop images from an specific area
`$ convert -crop 50x50+100+100 INPUTFILE OUTPUTFILE`
> creates an 50x50 px Image starting from 100px 100px in the left upper corner


## TRANSFORM
### Rotate image
`$ convert INPUTFILE -rotate 90 OUTPUTFILE`
- rotate images in a folder and rename:
```bash
for file in *.jpg; do convert $file -rotate 90 rotated-file; done
```

### Mirror picture in a folder and rename
- vertical
```bash
for file in *.jpg; do convert $file -flip flipped-$file; done
```
- horizontal
```bash
for file in *.jpg; do convert $file -flop flopped-$file; done
```

## GIF: create gif from images in folder
```bash
$ convert -delay 20 -loop 0 *.jpg -scale heightxwidth myimage.gif
```


## COLORSPACE
- in den richtigen Farbraum konvertieren  
`magick -set colorspace CMYK` 

```bash 
$ convert input.tiff -colorspace cmyk -profile ECI_Offset_2009/ISOcoated_v2_300_eci.icc output_cmyk2.tiff  
```
## Resolution
### Upscale:
```bash
convert -units PixelsPerInch INPUTFILE -resample 150 OUTPUTFILE
```
