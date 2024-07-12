---
title: 海奇固件解包
description:
categories:
 - tutorial
tags:
---

```
import os
from struct import *

def to_string(b):
    b = b.rstrip(b'\xff')
    b = b.rstrip(b'\x00')
    return b.decode()
    
with open('flash.bin', 'rb') as f:
    data = f.read()

offset = 0
length = len(data)

try:
    os.mkdir('tmp')
except:
    pass

sf = open('tmp/script.txt', 'w')

while offset < length:
    block_id = unpack('>I', data[offset:offset+4])[0]
    block_len = unpack('>I', data[offset+4:offset+8])[0]
    next_block_offset = unpack('>I', data[offset+8:offset+12])[0]
    block_name = to_string(data[offset+0x10:offset+0x20])
    block_ver = to_string(data[offset+0x20:offset+0x30])
    block_time = to_string(data[offset+0x30:offset+0x40])

    print('[File]')
    print('id=0x%08x' % block_id)
    if next_block_offset == 0:
        print('len=0x%X' % block_len)
    else:
        print('offset=0x%X' % next_block_offset)
        print('file=%s' % block_name)
        
    print('name="%s"' % block_name)
    print('ver="%s"' % block_ver)
    print('time="%s"' % block_time)
    
    sf.write('[File]\n')
    sf.write('id=0x%08x\n' % block_id)
    if next_block_offset == 0:
        sf.write('len=0x%X\n' % block_len)
    else:
        sf.write('offset=0x%X\n' % next_block_offset)
        sf.write('file=%s\n' % block_name)
        
    sf.write('name="%s"\n' % block_name)
    sf.write('ver="%s"\n' % block_ver)
    sf.write('time="%s"\n' % block_time)
    
    if next_block_offset == 0:
        break
    
    with open('tmp/' + block_name, 'wb') as f:
        f.write(data[offset+0x80:offset+next_block_offset-0x80])
    
    offset += next_block_offset
    
sf.write('[OutFile]\nout=modify.abs\n')
```