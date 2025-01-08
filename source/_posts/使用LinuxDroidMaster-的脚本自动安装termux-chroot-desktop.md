---
title: 使用LinuxDroidMaster 的脚本自动安装termux chroot desktop
date: 2025-01-08 02:36:59
tags:
---
起初是用tmoe自动化安装，装来装去不明白，后来搜到了linuxDroidMaster用它的脚本安装成功了，它的脚本不能照抄，有些地方需要自己修改。


开机后需要安装的软件：
sudo apt install firefox-esr neofetch xfce4-goodies ibus ibus-libpinyin ufw locales 


微信lib补全
libatomic1 libxkbcommon-x11-0 libxcb-icccm4 libxcb-image0 libxcb-render-util0 libxcb-keysyms1

qq lib软连接
ln -s /usr/lib/aarch64-linux-gnu/libtiff.so.6 /usr/lib/aarch64-linux-gnu/libtiff.so.5

设置时区
sudo locale-gen zh_CN.UTF-8
sudo ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

编辑github的访问ip
自动：sudo sh -c 'sed -i "/# GitHub520 Host Start/Q" /etc/hosts && curl https://raw.hellogithub.com/hosts >> /etc/hosts'
手动：
sudo nano /etc/hosts
https://github.com/521xueweihan/GitHub520

