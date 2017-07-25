# Day2DayFFMPEG

#Reduce File to 720x480
ffmpeg -i input.avi -s 720x480 -c:a copy output.mkv

#Split File into 10 Minute Chunks
ffmpeg -i fff.avi -acodec copy -f segment -segment_time 600 -vcodec copy -reset_timestamps 1 -map 0 fff%d.avi
