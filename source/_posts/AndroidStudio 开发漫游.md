title: Mac 开发漫游
date: 2018/08/10 15:24:36
categories:

- AndroidStudio 开发漫游

tags:

-  android
-  develop 

---

# Android 语法



# 框架



# AndroidStudio 开发

## 新建项目

## 使用Gradle



# 关于网络翻墙

google 的镜像库很扯，各种 timeout，几个地方设置代理，SSR 的通道

* Proxifier 代理，设置 HTTPS 代理 0.0.0.0 1087 HTTPS

* Settings HTTPS Proxy

* gradle.properties 增加参数代理 google() response

  ```
  systemProp.https.proxyHost=0.0.0.0
  systemProp.https.proxyPort=1087
  systemProp.https.nonProxyHosts=*.nonproxyrepos.com|localhost
  ```

* http://pro.sr1.me/post/android-sdk-download-links 把platforms和 buildtool手动下载放入 studio 内部的Platform 和 build-tools文件夹刷新 sdk manager

# 参考

* https://gradle.org/