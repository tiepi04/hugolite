---
title: Linux的使用
published: 2023-10-03T01:49:07+08:00
summary: "Linux上我常忘的点"
cover:
  image: "https://img.paulzzh.com/touhou/random"
tags: [系统,Linux]
categories: '系统'
draft: false 
lang: ''
---
<i>这篇关于Linux。(废话dog)</i>
生成封面用的工具是<b>neofetch</b>
# ssh连接工具
1.<b>finalshell</b>
仅有电脑版，但功能强大
[点击前往123pan下载](https://www.123pan.com/s/A6cA-2rHJh)
2.<b>Juicessh</b>
安卓上比较好用的

# 内存
## 查看剩余内存
``` bash
df -h
```
## 查看剩余寿命(固态)
``` bash
cat /sys/class/mmc_host/mmc0/mmc0:0001/life_time
```
0X04 用了40%的寿命
0X08 用了80%的寿命
0X00 看不到寿命
·如图
![EMMC寿命对照表](/photos/EMMC.png)
所以你已经懂它的格式了吧
不懂我就给你看两张照片对比一下
看不到寿命或满血的情况
![看不到寿命的情况](/photos/1.jpg)
能看到寿命的情况
![能看到寿命的情况](/photos/2.jpg)

# 网络
## 设置网络(WiFi、USB网络、设置名称等)
``` bash
nmtui
```
设置后再`reboot`重启一下才有用

## 查看ip
``` bash
ifconfig
```
