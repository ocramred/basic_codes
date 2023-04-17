# BASIC CODES 
## FFMPEG - VIDEO CONVERSION

## VIDEO_2_FRAMES : Extract frames from video
`ffmpeg -i movie.mpg movie%d.jpg`

besseres Ergebnis, Umwandlung dauert länger, Files größer:  
`ffmpeg -i movie.mpg -f image2 -c:v png movie%d.jpg`

extract one Frame each minute:
$ ffmpeg -i movie.mpg -r 1 -filter:v  movie%d.jpg
$ ffmpeg -i movie.mpg -filter:v fps=fps=1/60 movie%d.jpg
$ ffmpeg -i <movie-file> -f image2 -c:v png -vf fps=fps=2 „./<PATHtoFRAMES/frame_%d05_name.jpg"

e.g.:
```
ffmpeg -i P1111725_day1_portrait_kopfschuetteln_.MOV -f image2 -c:v png -vf fps=fps=2 "./P1111725_day1_portrait_kopfschuetteln/P1111725_frames_%05d.png"
```


## FRAMES_2_VIDEO : single Frames into video  
`ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg`

from: https://ffmpeg.org/faq.html#How-do-I-encode-movie-to-single-pictures_003f



## SWITCH CONTAINER : convert video file
> to preserve the quality of your source video file, use '-qscale 0' parameter:  
`ffmpeg -i input.webm -qscale 0 output.mp4`


## VIDEO_ONLY : remove audio stream from video file
`ffmpeg -i input.mp4 -an output.mp4`  


# ImageMagick
## batch convert file format
mogrify -format jpg -quality 100 *.png
mogrify -gravity center -extent 1024x512 ./P1111740_portrait_kurz/*.png


## Re-size all images in folder and keep ratio (but keep minimal width)
`mogrify -resize „1024x512^“ *.jpg`

##  crop images to a specific size
`mogrify -gravity center -extent 1024x512 Images/20220213_myself/*.jpg`

> get Info: `mogrify -list gravity`  
> gravity choices: NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast.

