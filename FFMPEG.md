# BASIC CODES 
## FFMPEG - VIDEO CONVERSION
---
## ☞ VIDEO_2_FRAMES : Extract frames from video
Basic Command:  
`ffmpeg -i movie.mpg movie%d.jpg`

better results, conversion needs more time, larger filesize:  
`ffmpeg -i movie.mpg -f image2 -c:v png movie%d.png`

extract one Frame each minute:  
`ffmpeg -i movie.mpg -r 1 -filter:v movie%d.jpg`  
`ffmpeg -i movie.mpg -filter:v fps=fps=1/60 movie%d.jpg`  
`ffmpeg -i MOVIE-FILE -f image2 -c:v png -vf fps=fps=2 „./<PATHtoFRAMES/frame_%d05_name.jpg"`  

## ☞ FRAMES_2_VIDEO : single Frames into video  
`ffmpeg -f image2 -i img%d.jpg OUTPUT-FILE`  
from: https://ffmpeg.org/faq.html#How-do-I-encode-movie-to-single-pictures_003f

## ☞ SWITCH CONTAINER : convert video file
> to preserve the quality of your source video file, use '-qscale 0' parameter:  
`ffmpeg -i input.webm -qscale 0 output.mp4`


## ☞ REMOVE_AUDIO : remove audio stream from video file
`ffmpeg -i input.mp4 -an output.mp4`
