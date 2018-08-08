title: 博客迁移
---
这里把原来tryghost的blog全部迁移到hexo上面来了，新的方案使用github+travisCI+hexo。
说一下整体过程

# 原因
1. tryghost版本太老，nodejs基于0.10.x的版本，dependence里面有很多包都有漏洞但是无法升级。
2. 新版本和老版本数据库不兼容。

# 过程
## 迁移过程
 1. export tryghost backup.json
 2. 把json通过java解析，用fastjson，velocity 库转换成md模版
 3. import hexo，然后hexo clean ，hexo g集成
## 部署过程
 1. github新建仓库zuoyun.me，设置blog-resouce 和master双分支
 2. 对master分支设置GitHub page 和 CNAME，域名重定向
 3. 对blog-resouce分支导入hexo和.travis.yml文件
 4. 生成github token在travis-ci里面配置对应的库，完成ci配置
 
#后记 
## travis.yml文件

```

```
## 引用
