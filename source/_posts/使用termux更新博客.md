---
title: 使用termux更新博客
date: 2024-01-12 15:17:00
tags: 网络技术
---
## 前言

Hexo 是一个用 Nodejs 编写的快速、简洁且高效的博客框架。Hexo 使用 Markdown 解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

下面介绍在Termux中安装个人hexo博客并结合cpolar工具实现远程访问。

# 1.安装 Hexo

Hexo 是用 Nodejs 编写的，所以安装的话先安装node.js,termux 也是封装了,一行命令安装:

```shell
pkg install nodejs
```

安装后使用npm命令来安装hexo：

```shell
npm install hexo-cli -g
```


安装完成后，查看一下版本信息,检验是否安装成功：

```shell
hexo -v
```
手动创建一个hexo目录:

```shell
mkdir hexo
```

进入目录

```shell
cd hexo
```

初始化Hexo环境

```shell
hexo init
```

初始好后生成静态文件:

```shell
hexo g
```


启动hexo

```shell
hexo s
```


