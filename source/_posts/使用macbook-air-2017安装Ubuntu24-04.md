---
title: 使用macbook air 2017安装Ubuntu24.04
date: 2024-12-02 06:21:42
tags:
---
记录下安装过程和使用心得。
1、把下载好的Ubuntu24.04镜像放入用ventoy制作的u盘内，插入MacBook，重新启动，按option进入引导选择界面，选择Ubuntu并按照引导安装。
2、进入初装的Ubuntu，设置中国源， sudo apt update && sudo apt upgrade -y ,更新完毕，发下驱动都装好了，蓝牙、wifi、摄像头、触控板、键盘上的快捷键均可以正常使用。

整个安装过程很顺利，十来分钟搞完，开箱即用，一点也不折腾，驱动什么的也没为难我，真的意外，这么顺利还是Linux吗？ 士别三日当刮目相看，发展到2024年Linux进步太大了。

使用心得：
1、Ubuntu默认的gnome桌面难用得很，把gnome替换成kde舒服多了。这里我绕了路，应该直接安装kubuntu的。
2、微信和QQ如今有了Linux版，其他常用软件也有Linux版了，Linux如今用起来很爽了。
3、游戏，折腾过lutris之类的启动器问题很多基本不能用；最后发现用steam是最好的选择，steam会自动设置好游戏环境，昨天玩了两三小时，很稳。