---
title: Termux的使用
published: 2023-10-19T14:58:37+08:00
summary: "常用的一些指令"
cover:
  image: "https://api.rls.ovh/horizontal"
tags: [程序,Termux]
categories: '程序'
draft: false 
lang: ''
---
# 一.准备
## 下载
[123云盘下载_版本0.118.0](https://www.123pan.com/s/wkn6Vv-AVpiH.html)提取码：7qQk
[蓝奏云下载_版本0.118.0](https://wwp.lanzoup.com/iDBWX1dugbpc)提取码：acmx
### 换源
``` bash
termux-change-repo in turmux-tools
```
然后更新一下
``` bash
pkg update && pkg upgrade
```

### 权限
提供存储权限(为了访问/storage/emulated/0/)
``` bash
termux-setup-storage
```
运行后再运行一次
输入y后空格
重启
访问测试
``` bash
/storage/emulated/0/
```
### 安装ssh方便远程管理
1.安装
``` bash
pkg install openssh
```
2.查看用户名
``` bash
whoami
```
3.设置密码(输入的时候看不见，输好后回车就行)
``` bash
passwd
```
4.查看ip
``` bash
ip a
```
5.连接
``` bash
ssh 用户名@你查看的ip -p 8022 
```
6.启动
``` bash
sshd
```
# 二.比较常用的需要termux:api
api包安装(可选)
``` bash
pkg install termux-api
```
1.获取有关音频功能的信息
``` bash
termux-audio-info
```
2.获取电池状态
``` bash
termux-battery-status
```
# 三.安装Linux
脚步输入后按提示走就行
``` bash
bash -c "$(curl -L https://gitee.com//mo2/linux/raw//2/2)"
```