title: 服务搭建[一]--ghost安装
date: 2014/12/16 22:46:02
categories:
 - tryghost

tags:
 - devops 



---

&nbsp;&nbsp;&nbsp;&nbsp;首先这玩意还是蛮好用的,主要是我喜欢markdown, 国内有人搞了汉化,做了些改装. 主要得益于GHOST的MIT协议吧..:)

### 项目地址

>https://github.com/TryGhost/Ghost

### 安装流程

 1.安装nodejs

使用 nvm ：https://github.com/creationix/nvm

```language-bash
nvm install 0.12
```

 2.安装ghost
 >ghost中文版: [www.ghostchina.com]()
 
 3.配置config.js production mysql数据库,域名,邮箱
 
 4.安装pm2启动

```language-bash
sudo npm install pm2 -g
NODE_ENV=production pm2 start index.js 
pm2 list
```


### 项目推荐

gitbook [https://github.com/GitbookIO/gitbook]()

以及分支[https://github.com/codepiano/gitbook]()

很不错的文档生成工具, 至少我是这么认为 :)
 


### 网站挂载点

 * 数据库 aliyun         2019-06-29
 * 服务器 digitaocaen    2016-05-00
 * 评论框 多言            free
 * https  WoSign         2015-11-01



