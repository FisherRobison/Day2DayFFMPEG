# Day2DayFFMPEG


# MXF to MP4
#### ffmpeg -i input.mxf -vcodec libx264 output.mp4

# Reduce File to 720x480
#### ffmpeg -i input.avi -s 720x480 -c:a copy output.mkv

# Split File Into 5 Minute Chunks
#### ffmpeg -i FILENAME -y -f segment -segment_time 300 -segment_start_number 1 -vcodec libx264 -vprofile high -preset slow -threads 2 -acodec libfdk_aac -ac 2 -reset_timestamps 1 -map 0:0 -map 0:1 FILENAME%03d.mp4

# AAC to MP3
#### ffmpeg -i audio.aac -acodec libmp3lame audio.mp3


# Fix Scale Issues
## Setdar is key
#### for i in *.mpg; do ffmpeg -i "$i"-vf setdar=16/9  "${i%.*}.mp4"; done;


# 1 FPS
#### ffmpeg -i file.mp4 -r 1 -q:v 1 -s 1280x720 -aspect 16:9 -filter_complex "scale=iw*sar:ih, pad=max(iw\,ih*(16/9)):ow/(16/9):(ow-iw)/2:(oh-ih)/2:black" frame_%03d.jpg


# Packages 
#### brew install ffmpeg --with-faac --with-fdk-aac --with-ffplay --with-fontconfig --with-freetype --with-frei0r --with-libass --with-libbluray --with-libcaca --with-libquvi --with-libsoxr --with-libssh --with-libvidstab --with-libvorbis --with-libvpx --with-opencore-amr --with-openjpeg --with-openssl --with-opus --with-rtmpdump --with-schroedinger --with-speex --with-theora --with-tools --with-webp --with-x265 --with-zeromq

# JPG to MP4
#### ffmpeg -r 60 -f image2 -s 1920x1080 -i pic%04d.png -vcodec libx264 -crf 25  -pix_fmt yuv420p test.mp4
