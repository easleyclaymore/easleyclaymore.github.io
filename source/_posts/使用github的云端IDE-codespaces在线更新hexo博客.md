---
title: 使用github的云端IDE codespaces在线更新hexo博客
date: 2024-11-07 12:55:35
tags:
---
之前苦于hexo更新繁琐，博客建好后一直懒得写了。
久而久之，连hexo基本命令都忘了。
今日在知乎咨询如何在线更新hexo博客，结果有大神指导github能开启云端ide，此烦恼顿消。
写这篇做测试。

# 先将博客源文件传到GitHub
先cd进相关目录
```
git init
```
初始化完成会出一大堆提示，这时使用：
```
git config --global --add safe.directory git仓库目录
```
这个命令是用来将一个安全目录添加到全局的 Git 配置中
```
git remote add origin git@github.com:easleyclaymore/maozedonganthology.git
```
命令将本地项目关联到远程Git仓库
```
git checkout --orphan book
```
新建名叫book的分支
```
git add .
git commit -m "b"
git push origin book
```
# 在codespaces开新博文后提交
遇到的问题：
用hexo d提交新的博文时出现：
```shell
>git@github.com: Permission denied (publickey).
>fatal: Could not read from remote repository.
>Please make sure you have the correct access rights
```
没有提交权限，需要向帐户添加新的 SSH 密钥
先算出新的密钥：
```
ssh-keygen -t ed25519 -C "myears@qq.com"
```
再复制密钥
```
cat ~/.ssh/id_ed25519.pub
```
最后在 GitHub 任意页面的右上角，单击个人资料照片，然后单击 “设置”****。

在边栏的“访问”部分中，单击 “SSH 和 GPG 密钥”。

单击“新建 SSH 密钥”或“添加 SSH 密钥” 。

在 "Title"（标题）字段中，为新密钥添加描述性标签。 例如，如果使用的是个人笔记本电脑，则可以将此密钥称为“个人笔记本电脑”。

选择密钥类型（身份验证或签名）。 有关提交签名的详细信息，请参阅“关于提交签名验证”。

在“密钥”字段中，粘贴公钥。

单击“添加 SSH 密钥”。

参考文献：
https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

弄完这些可以顺利的hexo g