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
![EMMC寿命对照表](./Linux-1/EMMC.png)
所以你已经懂它的格式了吧
不懂我就给你看两张照片对比一下
看不到寿命或满血的情况
![看不到寿命的情况](./Linux-1/1.jpg)
能看到寿命的情况
![能看到寿命的情况](./Linux-1/2.jpg)

# 网络
## 设置网络(WiFi、USB网络、设置名称等)
``` bash
nmtui
```
设置后再`reboot`重启一下保存

## 查看ip
``` bash
ifconfig
```

## 查看端口占用
<i>比如查看80端口占用情况</i>
<li style="margin-left: 40px;font-size: 15px">第一种</li>
``` bash
netstat/ss -antulp | grep :端口号
```
<li style="margin-left: 40px;font-size: 15px">第二种</li>
``` bash
lsof -i tcp:80
```
<i>第二种没有占有就无内容输出(第一种没试过)</i>
<li style="margin-left: 40px;font-size: 15px">强制kill该进程</li>
``` bash
kill -9 PID
```

<i>以下是扩展操作</i>

详细的查看PID
``` bash
ps -aux | grep 进程PID
```
查看该PID所处目录(末尾加/会显示进程路径的内容，不加显示进程具体路径)
``` bash
ll /proc/进程PID/cwd
```

# 用户
## 改密码
``` bash
passwd
```

# 杀死进程(kill,pkill,killall)
## kill
kill PID
强制下线
kill -9 PID
批量精准操作(-9为强制操作，非必须)
kill -9 PID

## pkill
pkill 进程名
也可以加上-9
通过pkill -h获取帮助

## killall
killall和pkill差不多(好像-9前面不需要空格)
killall -h获得帮助

# 安全检查
## 主机自动记录所有登陆事件
``` bash
vim /var/log/secure
```
## 所有登陆失败记录
``` bash
lastb
```
## 所有登陆成功事件记录
``` bash
last
```

# 使用systemctl自启动服务
`systemctl`脚本存放在:`/usr/lib/systemd/`,有系统（`system`）和用户（`user`）之分,需要开机不登陆就能运行的程序，存在系统服务里
即：`/usr/lib/systemd/system`目录下.每一个服务以`.service`结尾，一般会分为3部分：`[Unit]`、`[Service]`和`[Install]`

<li style="margin-left: 40px;font-size: 15px">[Unit]</li>
<li style="margin-left: 40px;font-size: 15px">[Service]</li>
<li style="margin-left: 40px;font-size: 15px">[Install]</li>

<li style="margin-left: 40px;font-size: 15px">实例</li>
``` bash
[Unit]
Description=devzat

[Service]
Type=forking
WorkingDirectory=/home/tiepiserver/devzat/
ExecStart=/home/tiepiserver/devzat/devzat
Restart=always

[Install]
WantedBy=multi-user.target
```

参考链接
[https://www.cnblogs.com/hlooc/p/15183479.html](https://www.cnblogs.com/hlooc/p/15183479.html)
