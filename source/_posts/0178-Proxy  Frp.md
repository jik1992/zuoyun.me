title: Proxy  Frp
date: 2016/12/15 11:52:07
categories:
 - tryghost

tags:
 - devops 



---

## 背景
透明代理，基于ssh建立隧道连接内网

## 使用

```language-bash
# 公网服务器
./frps -c frps.ini 
# 内网服务器，改配置指向公网ip
./frpc -c frpc_min.ini
# 公网服务器，进入内网网络
ssh -p 6000 root@127.0.0.1
```

注意，可以参考一下`特权模式`，客户端动态登录服务端，变相变成一个堡垒机做发布工作。

## 引用
https://github.com/fatedier/frp




