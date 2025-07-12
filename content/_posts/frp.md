---
title: frp服务器的搭建
published: 2024-08-27T12:05:46+08:00
summary: "我用来替代VPN服务器的东西"
cover:
  image: "https://rpic.origz.com/api.php?category=pixiv"
tags: [网络]
categories: '网络'
draft: false 
lang: ''
---
<i>frp可以通过有公网IP的的服务器将内网的主机暴露给互联网，从而实现通过外网能直接访问到内网主机；frp有服务端和客户端，服务端需要装在有公网ip的服务器上，客户端装在内网主机上。</i>

# 简单图解
<img src="show.png" alt="介绍" style="zoom:30%;" />

# 实例
## 下载frp
找到相应架构的文件
[https://github.com/fatedier/frp](https://github.com/fatedier/frp)
## 解压
``` bash
tar -txvf 文件名
```

解压如下：
<img src="jieya.png" alt="解压" style="zoom:50%;" />

## 执行命令
### 文件权限更改
``` bash
# 服务器端给执行文件添加权限
sudo chmod 777 frps
```
``` bash
# 客户端给执行文件添加权限
sudo chmod 777 frpc
```

### 配置文件修改
<li style="margin-left: 40px;font-size: 15px">服务端配置文件修改</li>

``` bash
# 打开服务端配置文件
vim frps.toml

# 我的填写内容如下：
bindPort = 7000

# 这是frp服务器端口，自行更换，更多功能看官方介绍
```

启动frps：
``` bash
# 前台启动
./frps -c ./frps.toml

# 后台启动
./frps -c ./frps.toml &

```
 
<li style="margin-left: 40px;font-size: 15px">客户端配置文件修改</li>
``` bash
# 打开客户端配置文件
vim frpc.toml

# 我的填写内容如下：
serverPort = 7000   # 服务端运行端口
[[proxies]]
name = "test-tcp"
type = "tcp"
localIP = "127.0.0.1"   # 本地ip
localPort = 22  # 想转发的(本地)端口
remotePort = 6000   # 转发到(服务器的)此端口
```

<li style="margin-left: 40px;font-size: 15px">安卓客户端app</li>
1 FRP_1.2.0.apk<a href="FRP_1.2.0.apk">点击下载</a>

2 Frpc_0.39.1.1.apk<a href="Frpc_0.39.1.1.apk">点击下载</a>
<i>配置在前面，复制更改一下即可</i>

# 参考：
[https://blog.csdn.net/qq_36981760/article/details/115713179](https://blog.csdn.net/qq_36981760/article/details/115713179)
