title: 服务搭建[二]--https/spdy 搭建
date: 2014/12/17 01:47:47
categories:
 - tryghost

tags:
 - devops 



---


#### 1. 获取证书

> [WoSign](https://www.wosign.com/) 免费

#### 2. 配置nginx 1.4( >1.4 支持spdy)
digitalocean下的nginx.conf配置如下

```
server {
    listen 80 default_server;   #  监听 80端口
    listen [::]:80 default_server ipv6only=on;
    server_name jik92.com; 
    rewrite ^(.*)$  https://$server_name$1 permanent; # 全部转发https
    root /usr/share/nginx/html;
    index index.html index.htm;
    client_max_body_size 10G;
}    
server{
    listen              443 ssl spdy;                              
    ssl                 on;
    ssl_certificate     /root/ssh/1_jik92.com_bundle.crt;# 配置密钥
    ssl_certificate_key /root/ssh/2_jik92.com.key;

    location / {
        proxy_pass http://localhost:2368;                         # 转发ghost默认端口
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_buffering off;
    }
 }
```

#### 3. 重启nginx
```
nginx -s reload
```

#### 4. enjoy it!
检测spdy开启 [http://spdycheck.org/# jik92.com](http://spdycheck.org/# jik92.com)

![](https://dn-zuoyun.qbox.me/image/3/80/add4152e8660166bdab252e0c6528.jpg)



