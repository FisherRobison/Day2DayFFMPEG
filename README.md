# Day2DayFFMPEG


# MXF to MP4
#### ffmpeg -i input.mxf -vcodec libx264 output.mp4

# Reduce File to 720x480
#### ffmpeg -i input.avi -s 720x480 -c:a copy output.mkv

# Split File Into 5 Minute Chunks
#### ffmpeg -i FILENAME -y -f segment -segment_time 300 -segment_start_number 1 -vcodec libx264 -vprofile high -preset slow -threads 2 -acodec libfdk_aac -ac 2 -af ‘volume=3.0’ -reset_timestamps 1 -map 0:0 -map 0:1 FILENAME%03d.mp4

# AAC to MP3
#### ffmpeg -i audio.aac -acodec libmp3lame audio.mp3


# Fix Scale Issues
## Setdar is key
#### for i in *.mpg; do ffmpeg -i "$i"-vf setdar=16/9  "${i%.*}.mp4"; done;


# 1 FPS
#### ffmpeg -i file.mp4 -r 1 -q:v 1 -s 1280x720 -aspect 16:9 -filter_complex "scale=iw*sar:ih, pad=max(iw\,ih*(16/9)):ow/(16/9):(ow-iw)/2:(oh-ih)/2:black" frame_%03d.jpg
