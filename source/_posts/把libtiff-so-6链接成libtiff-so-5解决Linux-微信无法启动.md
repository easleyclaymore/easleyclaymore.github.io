---
title: 把libtiff.so.6链接成libtiff.so.5解决Linux 微信无法启动的问题
date: 2025-01-04 08:37:05
tags:
---
该方法来自Termux&Linux交流群的群主Seraph

```
root@localhost:~# find /usr/lib /usr/local/lib -name "libtiff.so.*"
/usr/lib/aarch64-linux-gnu/libtiff.so.6
/usr/lib/aarch64-linux-gnu/libtiff.so.6.0.1
root@localhost:~# ln -s /usr/lib/aarch64-linux-gnu/libtiff.so.6 /usr/lib/aarch64-linux-gnu/libtiff.so.5
```

以下是termux X11常用命令
```

#!/bin/bash
export DISPLAY=:0
termux-x11 :0 &>/dev/null &
sleep 1
openbox-session &
startxfce4 &>/dev/null &

proot-distro login ubuntu --shared-tmp -- sh -c 'export DISPLAY=:0 && qq --no-sandbox'
```

以下是termux VNC常用命令
```
vncserver -kill :1
env|grep DISPLAY

#!/bin/bash
vncserver :1 -localhost no -geometry 1600x720
wait
export DISPLAY=:1
xhost +
sleep 1
#openbox-session &
startxfce4 &>/dev/null &

proot-distro login ubuntu --shared-tmp -- sh -c 'export DISPLAY=:1 && qq --no-sandbox'
proot-distro login ubuntu --shared-tmp -- sh -c 'export DISPLAY=:1'

apt update && apt upgrade -y
```