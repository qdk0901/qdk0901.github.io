---
title: 格式化分区
description:
categories:
 - tutorial
tags:
---

```
mkfs_jffs2() {                                                                                                                   
        local erase_block=$(/bin/cat /proc/mtd | /bin/grep "$(basename /dev/by-name/rootfs_data)" | /usr/bin/awk '{print $3}')    
        /bin/mkdir -p /tmp/jffs2.dir/tmp        
        mkfs.jffs2 -p -e 0x${erase_block} -d /tmp/jffs2.dir \
                -o /tmp/jffs2.img >/dev/null || return 1     
        /bin/dd if=/tmp/jffs2.img of=/dev/by-name/rootfs_data || return 1          
        /bin/rm -rf /tmp/jffs2.img /tmp/jffs2.dir                                                
}

mkfs_jffs2
```
