---
title: macOS相关的知识汇总
date: 2021-07-29 23:25:49
tags:
---

# IT相关的小知识汇总
<div style="border:1px solid;margin:0px;padding:0px 0px 0px 15px">

<style type="text/css">
    .indent-background {
        text-indent:2em;
        background: red;
    }
</style>

<div class="indent-background" style="margin:10px">
生活赋予我们的一种巨大的和无限高贵的礼品，这就是青春：充满着力量，充满着期待、志愿，充满着求知和斗争的志向，充满着希望、信心的青春。
</div>

<div align="center" style="padding:10px">
<b><i>保尔·柯察金（Павел Корчагин, 英文：Pavel Korchagin）</i></b></div>
</div>

[TOC]



## 本地目录及导航
微信多开命令  
`nohup /Applications/WeChat.app/Contents/MacOS/WeChat > /dev/null 2>&1 &`

切进easleyclaymore站点目录
`cd /Users/alin/Sites/easleyclaymore.github.io`

切进mdbook站点目录
`cd /Users/alin/Sites/books`

calibre-web 
http://192.168.1.4:8085

jellyfin http://192.168.1.4:8096

qbittorrent http://192.168.1.4:8080

cockpit https://192.168.1.4:9090

微力同步 https://192.168.1.4:8886

portainer http://192.168.1.4:9001

resilio https://hub.docker.com/r/linuxserver/resilio-sync

nas  dokuwiki  http://192.168.1.4:9888/

平库网 https://www.panelook.cn/

表格 | 项目 | 密码
------- | ------ | ------
|FTP账号资料 | |
|用户 |moregood_top|
|密码 |Goodday...|
|数据库账号资料 | |
|数据库名 |moregood_top|
|用户 |moregood_top|
|密码 |Goodday...|
|访问站点 |http://moregood.top/index.php|

## macOS相关的知识
### 1、mdbook
#### mdbook安装方法
先安装rust `curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`   [rust官网](https://www.rust-lang.org/zh-CN/learn/get-started) ，再安装mdbook   `cargo install mdbook`   [mdbook说明文档](https://mdbook.budshome.com/cli/index.html)

#### 网站式电子书制作工具mdbook相关命令

1. 在finder中拖动文件夹到终端，使用`mdbook init`创建电子书
2.  使用 `mdbook build`把md文件输出成html格式的网站式电子书
3. `mdbook watch --open`可以生成网站并用浏览器打开预览，每次修改文件站点会即时触发构建。

#### 编辑Macos的环境变量

1. `echo 'export PATH=/Applications/mdbookapp:$PATH' >> ~/.bash_profile`  输入终端把madbook可执行文件加入环境变量
2. 也可以输入`nano ~/.bash_profile` 进入编辑模式，加一行 `export PATH=/Applications/mdbookapp/mdbook:$PATH`  。
3. 保存后的环境变量不会立即生效，需要执行   `source ~/.bash_profile`





## 一般通用IT知识
### 1、markdown指南
[md中文文档](https://markdown.budshome.com/)

### 2、Unix相关的命令行

#### 用tree查看目录结构及文件 


apt install -y tree

tree -f  #显示文件全路径

tree -P *.txt       #只显示文件目录和*.txt文件

如果需要保存目录结构及文件名到txt

tree -f > 总目录.txt


reset #清空terminal


#### 合并文件 

 cat *.txt > merge && rm *.txt     #假设有a 、b、c三个txt，合并之后，把a、c、b源文件删掉

#### 用脚本合并文件 

touch mergetxt.sh && nano mergetxt.sh   #创建并编辑一个脚本
  #! /bin/bash
  #这是一个合并txt的脚本   20200523
  cat *.txt > file && rm *.txt
  echo "done."

sh mergetxt.sh #执行脚本的方法一
chmod +x mergetxt.sh && ./mergetxt  #这是执行脚本的方法二

#### TXT编码转换 

单文件 iconv -f gbk -t utf8 PythonStudy.txt > Python.txt.utf8

多文件 apt install -y enca && enca -x utf-8 *  或者  enca -L zh_CN -x utf-8 *

####  文件名编码转换

由于如今用linux,原来在windows里的文件都是用GBK编码的。所以copy到linux下是乱码，文件内容能够用iconv来转 换可是好多中文的文件名仍旧乱码，找到个能够转换文件名编码的命令，就是convmv。

convmv命令细致参数

比如

convmv -f GBK -t UTF-8 *.mp3

不过这个命令不会直正的转换，你能够看到转换前后的比拟。假设要直正的转换要加上参数 –notest

convmv -f GBK -t UTF-8 –notest *.mp3

-f 参数是指出转换前的编码，-t 是转换后的编码。这个千万不要弄错了。不然能够仍旧乱码哦。尚有一个参数很有用。就是 -r 这个表示递归转换现在目录下的一切子目录。



#### 目录下所有文件递归转换

find default -type d -exec mkdir -p utf/{} \;
find default -type f -exec iconv -f GBK -t UTF-8 {} -o utf/{} \;
这两行命令将default目录下的文件由GBK编码转换为UTF-8编码，目录结构不变，转码后的文件保存在utf/default目录下。

对上面的命令进行解释：

-exec command: 执行命令, 具体介绍见后文. -ok command: 和-exec一样, 除了命令执行需要用户许可. -print: 打印文件名 -ls: 列出文件详细信息

简单地说, -exec或-ok, 将查询到的文件作为参数传递给后面的命令执行, 而参数的位置用{}标识, 即命令中, “{}”替换成find查找出来的文件名, 最后”\;”表示结束符.


