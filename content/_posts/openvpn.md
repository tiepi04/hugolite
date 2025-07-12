---
title: OpenVPN服务器
published: 2024-01-25T14:10:52+08:00
summary: "VPN服务器搭建（保姆级的）"
cover:
  image: "https://api.likepoems.com/img/pc"
tags: [网络]
categories: '网络'
draft: false 
lang: ''
---

https://blog.csdn.net/zhangshenghang/article/details/135292267

### 拉取镜像

```bash
docker pull kylemanna/openvpn:2.4
```

### 创建配置文件

ip换成服务器的ip(网址)再加端口(如:udp://x.x.x.x:port)

```bash
docker run -v /opt/openvpn:/etc/openvpn --rm kylemanna/openvpn:2.4 ovpn_genconfig -u tcp://ip[:port]
```

### 生成密钥文件

```bash
docker run -v /opt/openvpn:/etc/openvpn --rm -it kylemanna/openvpn:2.4 ovpn_initpki
```

#### 输出结果

```
# 设置密码
Enter New CA Key Passphrase: 
Re-Enter New CA Key Passphrase: 
# 默认回车
Common Name (eg: your user, host, or server name) [Easy-RSA CA]:
# 输入刚刚设置的密码
Enter pass phrase for /etc/openvpn/pki/private/ca.key:
Enter pass phrase for /etc/openvpn/pki/private/ca.key:
```

完整执行步骤日志

```
[root@bigdata-101 ~]# docker run -v /opt/openvpn:/etc/openvpn --rm -it kylemanna/openvpn:2.4 ovpn_initpki

init-pki complete; you may now create a CA or requests.
Your newly created PKI dir is: /etc/openvpn/pki


Using SSL: openssl OpenSSL 1.1.1g  21 Apr 2020

Enter New CA Key Passphrase: 
Re-Enter New CA Key Passphrase: 
Generating RSA private key, 2048 bit long modulus (2 primes)
.............................................................................................................................................................................+++++
.................................+++++
e is 65537 (0x010001)
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Common Name (eg: your user, host, or server name) [Easy-RSA CA]:

CA creation complete and you may now import and sign cert requests.
Your new CA certificate file for publishing is at:
/etc/openvpn/pki/ca.crt


Using SSL: openssl OpenSSL 1.1.1g  21 Apr 2020
Generating DH parameters, 2048 bit long safe prime, generator 2
This is going to take a long time
.................................................................+....+....................+.........................................................................................................+....+.......................................................................................................................................................................+.....................................+...................+.......................+.....................................................................................................................................................................................................................................+............................................................................+...................................................................................................................+.....+.......................................................................................................................................................................................................................................+..................................................................................................................................................................................................+........+.............................................................................................................................+..............................+....................................................+..............................................................................................................................................................................+......................................................................................................+....................................................................................+.......................++*++*++*++*

DH parameters of size 2048 created at /etc/openvpn/pki/dh.pem


Using SSL: openssl OpenSSL 1.1.1g  21 Apr 2020
Generating a RSA private key
.............................................+++++
.....................+++++
writing new private key to '/etc/openvpn/pki/easy-rsa-73.bBJIMn/tmp.PBbHDh'
-----
Using configuration from /etc/openvpn/pki/easy-rsa-73.bBJIMn/tmp.lDdIgp
Enter pass phrase for /etc/openvpn/pki/private/ca.key:
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
commonName            :ASN.1 12:'公网IP'
Certificate is to be certified until Apr  2 07:03:45 2026 GMT (825 days)

Write out database with 1 new entries
Data Base Updated

Using SSL: openssl OpenSSL 1.1.1g  21 Apr 2020
Using configuration from /etc/openvpn/pki/easy-rsa-148.JkjcgL/tmp.Ahiido
Enter pass phrase for /etc/openvpn/pki/private/ca.key:

An updated CRL has been created.
CRL file: /etc/openvpn/pki/crl.pem
```

### 生成客户端证书
生成无密码的客户端
```bash
docker run -v /opt/openvpn:/etc/openvpn --rm -it kylemanna/openvpn:2.4 easyrsa build-client-full jast nopass
```

> jast 为客户端用户

```
[root@bigdata-101 ~]# docker run -v /opt/openvpn:/etc/openvpn --rm -it kylemanna/openvpn:2.4 easyrsa build-client-full jast nopass
Using SSL: openssl OpenSSL 1.1.1g  21 Apr 2020
Generating a RSA private key
.+++++
...................+++++
writing new private key to '/etc/openvpn/pki/easy-rsa-1.npkoBm/tmp.GjbIiO'
-----
Using configuration from /etc/openvpn/pki/easy-rsa-1.npkoBm/tmp.GAAMkb

Enter pass phrase for /etc/openvpn/pki/private/ca.key: # 输入刚刚创建的密码
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
commonName            :ASN.1 12:'jast'
Certificate is to be certified until Apr  2 07:06:25 2026 GMT (825 days)

Write out database with 1 new entries
Data Base Updated
```

#### 生成有密码的客户端

```
Using SSL: openssl OpenSSL 1.1.1g  21 Apr 2020
Generating a RSA private key
.........................................+++++
...............................................+++++
writing new private key to '/etc/openvpn/pki/easy-rsa-1.MEMpOp/tmp.gLiNaP'
Enter PEM pass phrase:  # 输入要设置的客户端的密码
Verifying - Enter PEM pass phrase:
-----
Using configuration from /etc/openvpn/pki/easy-rsa-1.MEMpOp/tmp.gCiMLA
Enter pass phrase for /etc/openvpn/pki/private/ca.key:  # 输入之前设置的证书密码
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
commonName            :ASN.1 12:'jast3'
Certificate is to be certified until Apr  2 07:24:36 2026 GMT (825 days)

Write out database with 1 new entries
Data Base Updated
```

### 导出证书

导出客户端认证文件到本地

> jast 为客户端名称

```bash
docker run -v /opt/openvpn:/etc/openvpn --rm kylemanna/openvpn:2.4 ovpn_getclient jast > /opt/jast.ovpn

```

### 启动VPN

```
docker run --name ov --restart=always --privileged=true -v /opt/openvpn:/etc/openvpn -d -p 1194:1194/tcp --cap-add=NET_ADMIN kylemanna/openvpn:2.4
```

> 如果公网访问VPN，公网的IP地址和端口要映射到当前容器所在服务器的1194端口

### 配置哪些流量走VPN

修改客户端文件`jast.ovpn`，在配置文件中添加

```
# 表示不接受服务器对于修改路由表的推送，而可以按照我们之后指定的规则去修改
route-nopull
# 这个参数设置了路由的度量值（metric），用于确定路由的优先级。路由的度量值越小，优先级越高。在有多个路由规则匹配的情况下，系统会选择度量值最小的路由。
route-metric 150
# 远程主机（remote_host）的流量通过本地网关（net_gateway）发送
route remote_host 255.255.255.255 net_gateway
# 172.19.0.0/16网段的流量通过本地网关发送
route 172.19.0.0 255.255.0.0 net_gateway
# 192.168.1.0/16网段的流量通过VPN网关（vpn_gateway）发送
route 192.168.1.0 255.255.0.0 vpn_gateway

```

注释掉这一行

> `redirect-gateway def1`作用是将默认网关重定向到 VPN 服务器上，所以要注释掉。

```
# edirect-gateway def1
```

客户端下载地址
Mac:https://tunnelblick.net/

Win7:https://swupdate.openvpn.org/community/releases/openvpn-install-2.4.8-I602-Win7.exe

Win10:https://swupdate.openvpn.org/community/releases/openvpn-install-2.4.8-I602-Win10.exe

参考
https://kui.li/675.html

https://kyo86.com/2022/10/08/openvpn/

https://blog.csdn.net/weizhen330/article/details/132244496

https://blog.csdn.net/qq_42761569/article/details/106538056

https://blog.csdn.net/zhangshenghang/article/details/135292267
