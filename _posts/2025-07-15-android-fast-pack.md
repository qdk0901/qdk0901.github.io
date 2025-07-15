---
title: android快速打包
description:
categories:
 - tutorial
tags:
---

- 快速打包system和super
```
DIR=`pwd`
PATH=$PATH:$DIR/out/host/linux-x86/bin
TARGET=$DIR/out/target/product/apollo-p2
PACKAGING_PATH=$TARGET/obj/PACKAGING/

echo "start fast pack"

build_image $TARGET/system $PACKAGING_PATH/systemimage_intermediates/system_image_info.txt $TARGET/system.img $TARGET
build_super_image -v $PACKAGING_PATH/superimage_debug_intermediates/misc_info.txt $TARGET/super.img
#$DIR/build/tools/releasetools/build_super_image.py -v $PACKAGING_PATH/superimage_debug_intermediates/misc_info.txt $TARGET/super.img
echo "done"
```