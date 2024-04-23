---
title: ats解密加密流
description:
categories:
 - tutorial
tags:
---

pair-setup/pair-verify加密的流如果需要在ats里能解码，可以向ff02::01端口4444发送如下内容的一个包
ats收到后就会自动解码对应连接的数据

```
<dict>
	<key>LocalIPAddress</key>
	<string>本机ipv6地址</string>
	<key>LocalPort</key>
	<integer>本机ipv6端口</integer>
	<key>LocalSendsWithReadKey</key>
	<integer>0</integer>
	<key>ReadKey</key>
	<data>
	pair-verify派生得到的read key
	</data>
	<key>RemoteIPAddress</key>
	<string>对端ipv6地址</string>
	<key>RemotePort</key>
	<integer>对端端口</integer>
	<key>WriteKey</key>
	<data>
	pair-verify派生得到的write key
	</data>
	<key>StreamType</key>
	<string>Ctrl</string>
	<key>SessionType</key>
	<string>CP</string>
</dict>
```