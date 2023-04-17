# ImageMagick
## Batch convert file format
mogrify -format jpg -quality 100 *.png
mogrify -gravity center -extent 1024x512 ./P1111740_portrait_kurz/*.png


## Re-size all images in folder and keep ratio (but keep minimal width)
`mogrify -resize „1024x512^“ *.jpg`

## Crop images to a specific size
`mogrify -gravity center -extent 1024x512 Images/20220213_myself/*.jpg`

> get Info: `mogrify -list gravity`  
> gravity choices: NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast.