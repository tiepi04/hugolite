---
title: Hexo的安装
published: 2023-11-24T22:34:24+08:00
summary: "搭建hexo"
cover:
  image: "https://img.paulzzh.com/touhou/random"
tags: [博客]
categories: '博客'
draft: false 
lang: ''
---
hexo g 创建静态文件
hexo s 启动
hexo clean 清除缓存
hexo d 推送文件
hexo new "My New Post" 创建新文章

# 安装nodejs和git
安装nodejs
``` bash
#Linux安装nodejs
curl -sL https://deb.nodesource.com/setup_10.x|sudo -E bash -
sudo apt install nodejs
```
检测安装
``` bash
#检测nodejs和npm
nodejs -v
npm -v
```
安装git
``` bash
#安装git
sudo apt install git -y
```

npm换源
``` bash
#npm换淘宝源
sudo npm install -g cnpm --registry=https://registry.npm.taobao.org
```
# 安装hexo
``` bash
sudo cnpm install -g hexo-cli
```
# 配置hexo
``` bash
cd /
mkdir hexo
chmod 7777 hexo
cd hexo
#初始化
hexo init
```
# 主题
## 找主题
[hexo主题官网](http://hexo.io/themes)
尽量选择移动端和电脑端都有的主题

点进去后底部右下方有它的github官网

进入后点"Clone with HTTPS",复制那个https链接
``` bash
#hexo换成你自己的hexo目录
cd /hexo
#添加"themes/主题名"方便管理
git clone 网址 themes/主题名
```
## 改配置文件
``` bash
cd /hexo
vim _config.yml
```
输入"/"打开查找模式后输入themes，后车

输入"i"启动输入模式

把"themes: "后边的改成"你的主题名"，如"landscape"

输入"ALT+:wq"保存并退出
# 推送(hexo d)
``` bash
#清理缓存
hexo clean
#生成静态文件
hexo g
#测试一下
hexo s
#安装推送插件
cnpm install hexo-deployer-git --save
#发布到远程仓库
hexo d
```

在配置文件最后设置需要同步的仓库，可以设置多个
``` bash
deploy:
    type: git
    repo: 
        github: your github repo url
        gitee: your gitee repo url
        coding: your coding repo url
```
## 添加ssh公钥(推送方便)
获取方法
``` bash
#不一定要用你的邮箱(为了方便用邮箱)
ssh-keygen -t rsa -C '你的邮箱'
```

位置
``` bash
cd
cd .ssh
#id.rsa.pub就是公钥(把里面内容复制下来)
ls

```
例：
``` bash
deploy:
  type: git
  repo: https://github.com/用户名/用户名.github.io
  branch: main
```

