---
title: RustDesk服务器搭建
published: 2024-08-27T02:51:09+08:00
summary: "特别好用的远控"
cover:
  image: "https://t.alcy.cc/moe"
tags: [服务器,程序]
categories: '服务器'
draft: false 
lang: ''
---
> 注意现在这篇的参考价值很低
>
> 直接用host的网络连接方式更好


<i>RustDesk 是一款可以平替 TeamViewer 的开源软件，旨在提供安全便捷的自建方案。</i>
[官网](rustdesk.com)

# 自建服务器
## 拉取镜像
``` bash
sudo docker image pull rustdesk/rustdesk-server
```
## 开启hbbs
``` bash
docker run --name hbbs -p 26115:21115 -p 26116:21116 -p 26116:21116/udp -p 26118:21118 -v [你的自定义地址/hbbs]:/root -td rustdesk/rustdesk-server hbbs -r [你的地址（IP/域名）]:26116 -k [你的自定义key]
```
## 开启hbbr
``` bash
sudo docker run --name hbbr -p 26117:21117 -p 26119:21119 -v [你的自定义地址/hbbr]:/root -td rustdesk/rustdesk-server hbbr -k [你的自定义key]
```
# 命令解释
<li style="margin-left: 40px;font-size: 15px">替换路径和域名的地方加了个[]，是为了便于区分，替换的时候记得删除。</li>
<li style="margin-left: 40px;font-size: 15px">“-p 26115:21115” ： 26115 是docker宿主机（本机端口），21115 是RustDesk 的默认端口， 如果不修改默认端口 请使用“-p 21115:21115”，其他的端口映射类似</li>
<li style="margin-left: 40px;font-size: 15px">--name 是定义了 docker 实例的名称，可以方便引用</li>
<li style="margin-left: 40px;font-size: 15px">-v 是docker宿主机到容器内的文件映射</li>
<li style="margin-left: 40px;font-size: 15px">“rustdesk/rustdesk-server hbbr” 是带 hbbr或者hbbs 参数启动</li>
<li style="margin-left: 40px;font-size: 15px">-r [你的地址（IP/域名）]:26116  是 在你的指定端口监听 ，默认端口是 21116 </li>

# 开放端口
默认情况下，hbbs 监听21115(tcp), 21116(tcp/udp), 21118(tcp)，hbbr 监听21117(tcp), 21119(tcp)。务必在防火墙开启这几个端口， 请注意21116同时要开启TCP和UDP 。其中21115是hbbs用作NAT类型测试，21116/UDP是hbbs用作ID注册与心跳服务，21116/TCP是hbbs用作TCP打洞与连接服务，21117是hbbr用作中继服务, 21118和21119是为了支持网页客户端。如果您不需要网页客户端（21118，21119）支持，对应端口可以不开。

    <li style="margin-left: 40px;font-size: 15px">TCP( 21115, 21116, 21117, 21118, 21119 )</li>
    <li style="margin-left: 40px;font-size: 15px">UDP( 21116 )</li>
# 加密key
## 自定义key
前面的<b>开启hbbs</b>和<b>开启hbbr</b>中的`-k [你的自定义key]`就是了

你把这段删掉就是生成`默认key`，这个应该是随机的，建议还是自定义

## 获取默认key
``` bash
# 1.进入镜像
sudo docker exec -it hbbs bash 
# 2.获取key
cat ./id_ed25519.pub 
```

<li style="margin-left: 40px;font-size: 15px"><p style="color: #FF0000;">测试你的 hbbs和hbbr 端口，确保防火墙放行</p></li>

# 客户端下载地址
[https://rustdesk.com/zh/](https://rustdesk.com/zh/)
[https://github.com/rustdesk/rustdesk/releases](https://github.com/rustdesk/rustdesk/releases)
  <li style="margin-left: 40px;font-size: 15px">下载完成，需要安装才能配置自建的rustdesk服务器</li>
# 客户端的配置
修改了端口的配置如下，<b>如果使用默认端口 只需要在 ID服务器填上你的服务器地址</b>，图中以上文端口为例
![](/photos/rustdesk1.png)
在客户端两边均填写相同信息，便可以像TeamViewer一样访问了，可以使用下图中的配置的复制粘贴功能
![](/photos/rustdesk2.png)

参考链接[https://www.cnblogs.com/HeisenbergUncertainty/p/17908858.html](https://www.cnblogs.com/HeisenbergUncertainty/p/17908858.html)
