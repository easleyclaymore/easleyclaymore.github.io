---
title: 使用termux开启dokuwiki
date: 2022-06-22 08:49:48
tags: 网络技术
---
# 手机termux启动dokuwiki常用命令

1、先安装termux。 Termux 是运行在 Android 上的 terminal。不需要root，运行于手机内部存储。 自带了一个包管理器，可以安装许多现代化的开发和系统维护工具。

2、在 Termux 中执行如下命令
```
termux-change-repo
```
在图形界面引导下，使用自带方向键可上下移动。 第一步使用空格选择需要更换的仓库，之后在第二步选择 TUNA/BFSU 镜像源。确认无误后回车，镜像源会自动完成更换。

给sd卡存储权限，在 Termux 中执行如下命令
```
termux-setup-storage
```
3、安装php

在 Termux 中执行如下命令
```
pkg install php
```
4、进入到你放到手机存储里面的目录，比如我的dokuwiki放在sdcard/htdocs/dokuwiki

在 Termux 中执行如下命令：
```
cd storage/shared/htdocs/dokuwiki
```
5、然后在电脑浏览器里面输入手机的ip地址加端口就能访问dokuwiki了。 如果不知道手机的ip地址，可以输入如下命令查看：
```
ip add
```
如果ip add不能执行，要安装什么东西，你就用pkg install +包名字 去进行安装。

6、运行php自带的服务器

在 Termux 中执行如下命令：
```
nohup php -f index.php -S 0.0.0.0:8087 > /dev/null 2>&1 &
```
7、写个脚本并运行
```
touch dokuwiki.sh
nano dokuwiki.sh
chmod +x dokuwiki.sh
```
运行
nohup ./dokuwiki.sh > /dev/null 2>&1 &

