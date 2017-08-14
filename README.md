# Day2DayFFMPEG


# MXF to MP4
#### ffmpeg -i input.mxf -vcodec libx264 output.mp4

# Reduce File to 720x480
#### ffmpeg -i input.avi -s 720x480 -c:a copy output.mkv

# Split File Into 5 Minute Chunks
#### ffmpeg -i fff.avi -acodec copy -f segment -segment_time 300 -vcodec copy -reset_timestamps 1 -map 0 fff%d.avi

# AAC to MP3
#### ffmpeg -i audio.aac -acodec libmp3lame audio.mp3
