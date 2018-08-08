title: API Gateway Caddy
date: 2017/11/20 02:32:20
categories:

 - devops 


tags:

- tryghost

---

###官网
https://caddyserver.com/docs
https://segmentfault.com/a/1190000008722666

没什么好讲的，很简单, 默认自动认证HTTPS。

写一个Caddyfile就可以使用
```language-bash
yd.index.tech84.com {
 gzip
 root   /var/www/html/
 fastcgi / 127.0.0.1:9000 php
}
db.zuoyun.me {
   gzip
   proxy / 0.0.0.0:8080 {
   }
}
dav.zuoyun.me {
    filemanager /   {
      allowCommands true
      allowEdit true
      allowNew true
      allow_publish true
      commands git svn
      locale en
    }
}
```
chmod -x caddy
caddy -service install  -conf /root/caddy/Caddyfile
caddy -service start
 




