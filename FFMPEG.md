### get Information about Mediafile
`ffprobe INPUT-FILE`


# BASIC CODES 
## FFMPEG - VIDEO CONVERSION
---
## ☞ VIDEO_2_FRAMES : Extract frames from video
Basic Command:  
`ffmpeg -i movie.mpg path/movie%d.jpg`

better results, conversion needs more time, larger filesize:  
`ffmpeg -i movie.mpg -f image2 -c:v png movie%d.png`

extract one Frame each minute:  
`ffmpeg -i movie.mpg -r 1 -filter:v movie%d.jpg`  
`ffmpeg -i movie.mpg -filter:v fps=fps=1/60 movie%d.jpg`  
`ffmpeg -i MOVIE-FILE -f image2 -c:v png -vf fps=fps=2 „./<PATHtoFRAMES/frame_%d05_name.jpg"`  

extract every 4th frame
(Change the fps=1/60 to fps=1/30 to capture a image every 30 seconds. Similarly if you want to capture a image every 5 seconds then change fps=1/60 to fps=1/5)

`ffmpeg -i file.mp4 -vf fps=1 %d.jpg`
`ffmpeg -i file.mp4 -vf fps=1/60 frame%06d.jpg`

## Frames in kleinerem Format ausgeben
`ffmpeg -i <videofile> -vf scale=XxY -r n`


## ☞ SWITCH CONTAINER : convert video file
> `-qscale` sets the compression level. The lower the qscale value, the bet­ter the qual­ity. The avail­able qscale val­ues range from 1 (high­est qual­ity) to 31 (low­est qual­ity)
> to preserve the quality of your source video file, use '-qscale 0' parameter:  
> Alternative as mentioned in the comments, which re-encodes with best quality (-qscale 0):
`ffmpeg -i input.webm -qscale 0 output.mp4`
or  
`ffmpeg -i input.mov -q:v 0 output.mp4`



## ☞ REMOVE_AUDIO : remove audio stream from video file
`ffmpeg -i input.mp4 -an output.mp4`

- keep video codec
`ffmpeg -i INPUT-FILE -vcodec copy -an OUTPUT-FILE`

## ☞ FRAMES_2_VIDEO : single Frames into video  
`ffmpeg -f image2 -i img%d.jpg OUTPUT-FILE`  
from: https://ffmpeg.org/faq.html#How-do-I-encode-movie-to-single-pictures_003f   


## change fps
`ffmpeg -i INPUT-FILE -filter:v fps=fps=25 OUTPUT-FILE`


ffmpeg-converting-mov-files-to-mp4
https://stackoverflow.com/questions/12026381/ffmpeg-converting-mov-files-to-mp4
