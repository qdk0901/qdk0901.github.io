---
title: ffmpeg常用命令
description:
categories:
 - tutorial
tags:
---

- 播放yuv文件  
```
ffplay.exe -f rawvideo -pixel_format yuv420p -video_size 800x480 e:\dump.yuv
```