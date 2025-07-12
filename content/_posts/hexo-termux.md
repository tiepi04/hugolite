---
title: Termux上的hexo
published: 2023-11-25T13:52:12+08:00
summary: "Termux上搭建hexo"
cover:
  image: "https://api.mtyqx.cn/api/random.php"
tags: [博客,Termux]
categories: '博客'
draft: false 
lang: ''
---
这个我忘了是干什么的了

sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list

pkg update

pkg install nodejs-lts
pkg install git
pkg install vim

mkdir hexo
chmod 777 hexo
cd hexo

npm install hexo-cli -g
hexo init

hexo g
hexo s 

主题
git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly

vim themes/butterfly/_config.yml

vim编辑器: 
输入i才能编辑
按下esc 再输入:wq保存退出npm install hexo-renderer-pug hexo-renderer-stylus --save