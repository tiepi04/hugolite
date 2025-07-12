---
title: ADB
published: 2023-10-19T22:32:07+08:00
summary: "ADB的常用指令"
cover:
  image: "https://rba.kanostar.top/adapt"
tags: [ADB]
categories: 'ADB'
draft: false 
lang: ''
---
### 设置屏幕息屏时间-1
永不息屏
``` bash
settings put system screen_off_timeout 2147483647
```
查看息屏时间
``` bash
settings put system screen_off_timeout
```
### 设置电池假装充电状态-2
``` bash
dumpsys battery set status 2
```
### 激活应用-3
键鼠映射软件:Panda Mouse pro
``` bash
sh /storage/emulated/0/.chaozhuo.gameassistant2/inject.sh
```
下载
[123云盘下载_版本1.5.0](https://www.123pan.com/s/wkn6Vv-ttpiH.html)
[蓝奏云下载_版本1.5.0](https://wwp.lanzoup.com/iQ62S1dug35e)提取码：38ev
### adb pull命令使用
把手机/sdcard/1里的文件下载到电脑D:\1文件夹里(/sdcard/1/文件名也行)
adb pull /sdcard/1 D:\1

主题https://theme-next.org/
彩色字https://benpaodewoniu.github.io/2020/01/27/hexo12/