title: Server Gitlab
date: 2016/03/03 06:09:46
categories:
 - tryghost

tags:
 - manage 



---

## 官网

https://about.gitlab.com/gitlab-com/

## Ominibus 一键安装包
https://about.gitlab.com/downloads/# ubuntu1404
https://mirror.tuna.tsinghua.edu.cn/help/gitlab-ce/



## 安装
```language-bash
# 安装
rpm -i gitlab-7.7.2omnibus.5.4.2.ci-1.el6.x8664.rpm 
# 重置配置
gitlab-ctl reconfigure
# 备份文件目录/var/opt/gitlab/backups
gitlab-rake gitlab:backup:create 
# 修改备份文件目录
vim /etc/gitlab/gitlab.rb
   gitlabrails['backuppath'] = '/mnt/backups' 
# 恢复备份
gitlab-ctl stop
gitlab-rake gitlab:backup:restore BACKUP=1393513186
gitlab-ctl start
# 升级
gitlab-ctl upgrade
# 升级2
查看：https://about.gitlab.com/upgrade-to-package-repository/
```

## 修改邮箱收发
```language-bash
 gitlab_rails['gitlab_email_enabled'] = true
 gitlab_rails['gitlab_email_from'] = 'xxxxx@58gxb.com'
 gitlab_rails['gitlab_email_display_name'] = 'Gitlab Server '

 gitlab_rails['smtp_enable'] = true
 gitlab_rails['smtp_address'] = "smtp.mxhichina.com"
 gitlab_rails['smtp_port'] = 25
 gitlab_rails['smtp_user_name'] = "xxxxx@58gxb.com"
 gitlab_rails['smtp_password'] = "passwd"
 gitlab_rails['smtp_domain'] = "smtp.mxhichina.com"
 gitlab_rails['smtp_authentication'] = "plain"
 gitlab_rails['smtp_enable_starttls_auto'] = false
```

## Gitlab-CI
* 安装
参考：https://gitlab.com/gitlab-org/gitlab-ci-multi-runner/blob/master/docs/install/linux-repository.md
```language-bash
sudo yum install gitlab-ci-multi-runner
sudo gitlab-ci-multi-runner register
```
* .gitlab-ci.yml
```language-bash
job_name:
  script:
    - echo hello
  stage: test
  only:
    - master
  except:
    - develop
  tags:
    - demo
  allow_failure: true
```

## 相关概念
* 默认账号 root
* 版本控制
 * Files
 * Comments
 * MergeRequests
* CI 构建
 * Builds
 * Graph
* 项目管理
 * Milestones
 * Issues
* 文档
 * Wiki
 * Snippts
 * Labels








