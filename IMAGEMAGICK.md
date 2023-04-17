# ImageMagick
## CONVERT : single file editing
- [Tutorial](https://www.opensourcefeed.org/00-convert-png-to-jpg-imagemagick/) 

`convert ORIGINAL-IMAGE CONVERTED-IMAGE`

```bash
# bash: simple batch job
for image in *.png ; 
do 
    convert "$image" "${image%.*}.jpg" ;
done
```
```bash
# simple one liner
for image in *.png ;  do convert "$image" "${image%.*}.jpg" ; done
````
### convert transparent layer PNG to JPG
`convert original-image.png -background white -flatten -alpha off new-image.jpg`



## MOGRIFY :  Batch convert file
- inside the picture path  
`mogrify -format jpg -quality 100 *.png`
- move result in new folder  
`mogrify -format png -path ./converted *.jpg`


## Re-size all images in folder and keep ratio (but keep minimal width)
`mogrify -resize „1024x512^“ *.jpg`

## Crop images to a specific size
`mogrify -gravity center -extent 1024x512 Images/20220213_myself/*.jpg`

> get Info: `mogrify -list gravity`  
> gravity choices: NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast.


### COLORSPACE
- in den richtigen Farbraum konvertieren    
`convert input.tiff -colorspace cmyk -profile ECI_Offset_2009/ISOcoated_v2_300_eci.icc output_cmyk2.tiff` 

`magick -set colorspace CMYK` 

## UPSCALE:
convert -units PixelsPerInch image -resample 150 resultimage
## RESIZE:
- `convert INPUT  -adaptive-resize 80x80  OUTPUT`  
- `mogrify -adaptive-resize 200% -quality 100 -path ../biggest *.tif`