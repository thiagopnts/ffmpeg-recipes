## FFmpeg Recipes

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
