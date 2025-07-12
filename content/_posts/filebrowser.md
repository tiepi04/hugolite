---
title: filebrowser的使用
published: 2023-10-02T08:38:04+08:00
summary: "Go语言的轻便文件管理器"
cover:
  image: "https://rpic.origz.com/api.php?category=pixiv"
tags: [文件管理]
categories: '文件管理'
draft: false 
lang: ''
---
## Linux下的使用教程
filebrowser是一个独立的文件管理工具，它使用go语言，不需要依赖直接./filebrowser即可运行，为了方便使用该篇文章叫你如何开机启动它。

### 查看架构-1
``` bash
arch
```

### 下载filebrowser-2
github官网地址
``` 
https://github.com/filebrowser/filebrowser
```
### 下载-3
在Releases中找到合适的安装包
``` bash
cd /
mkdir filebrowser
cd filebrowser
```
``` bash
wget 下载地址
```
### 解压-4
``` bash
tar -zxvf 文件名
```
删除(可选)
``` bash
rm -rf 文件名
```
### 安装-5
设置权限(chmod),端口号(port),账号密码(已设置为root)
这段无需更改
``` bash
chmod 777 filebrowser
./filebrowser -d filebrowser.db config init
./filebrowser -d filebrowser.db config set --address 0.0.0.0

```
设置端口号
``` bash
./filebrowser -d filebrowser.db config set --port 10000
```
设置账号
``` bash
./filebrowser -d filebrowser.db users add root root --perm.admin
```
设置挂载点
``` bash
./filebrowser -d filebrowser.db config set --root /
```
### 启动-6
``` bash
/filebrowser/filebrowser -d /filebrowser/filebrowser.db --disable-preview-resize --disable-type-detection-by-header --cache-dir /filebrowser/cache
```
### 添加开机启动-7
编辑rc.local
``` bash
vim /etc/rc.local
```
添加这段命令(建议添加在中间，其他我没试过)
``` bash
/filebrowser/filebrowser -d /filebrowser/filebrowser.db --disable-preview-resize --disable-type-detection-by-header --cache-dir /filebrowser/cache&
```
重启
``` bash
reboot
```
### 实际测试-8
访问网址: [localhost:10000](https://localhost:10000)
账号和密码
$ root
$ root
