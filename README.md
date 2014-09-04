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

