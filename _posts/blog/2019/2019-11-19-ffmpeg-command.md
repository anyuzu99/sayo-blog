---
layout: post
title: ffmpeg command
tags: [media, tip, podcast]
comment: true
---

use ffmpeg to convert audio and video.

## basic

install (macos)
- no config
  - `brew install ffmpeg` 
- with config
  - `brew tap homebrew-ffmpeg/ffmpeg`
  - `brew install homebrew-ffmpeg/ffmpeg/ffmpeg [config]`

general
- `ffmpeg -i [input] [config (option)] [output]`

## config (option) + output

aac
- config with `--with-fdk-aac`
  - `-c:a libfdk_aac -profile:a aac_he_v2 -vbr (2, 3) -movflags +faststart [output.m4a]`
- no config
  - `-vbr (2, 3) -movflags +faststart [output.m4a]`

opus
- `-c:a libopus (-b:a 32k) [output.opus]`

hevc
- `-c:v libx265 (-crf 28 -c:a libfdk_aac -profile:a aac_he_v2) [output.mp4]`

av1
- `-c:v libaom-av1 (-crf 30 -b:v 0) -strict experimental [output.mkv]`

## reference

- [high quality audio](https://trac.ffmpeg.org/wiki/Encode/HighQualityAudio)
- [aac](https://trac.ffmpeg.org/wiki/Encode/AAC)
- [h 265](https://trac.ffmpeg.org/wiki/Encode/H.265)

