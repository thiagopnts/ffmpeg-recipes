# FFmpeg Recipes

### Remove audio from video

```bash
$ ffmpeg -i [input file] -vcodec copy -an [output file]
```

### Extract part of a video

This will cut 5 seconds starting at 00:30 from the original video:
```bash
$ ffmpeg -i [input file] -ss 00:00:30 -t 00:00:05 -vcodec copy -acodec copy \
    -movflags faststart [output file]
```

### Convert a video to GIF
Ffmpeg 2.0 has improved support for GIFs. To convert a .mp4 to a .gif:
```bash
$ ffmpeg -i [input file] -vf scale=320:-1 -t 10 -r 10 output.gif
```
Where `-t 10` limits the output to 10 seconds. `-r 10` forces a frame rate of 10 fps.
The `scale=320:-1` is to set the width and height, here we pass -1 so ffmpeg picks the
best height for us.

### Convert MP4 to WebM
To convert you need to install ffmpeg with support for these codecs
On OSX:
```bash
$ brew install ffmpeg --with-libvpx --with-libvorbis
```
then you can use `libvorbis` and `libvpx` to convert your mp4 to webm:
```bash
$ ffmpeg -i [input file] -acodec libvorbis -vcodec libvpx [output file]
```
