title: CloudIDE-Cloud9/Che
date: 2015/11/18 05:44:36
categories:

 - tools 


tags:

- tryghost

---

#Cloud9
##项目库
https://github.com/c9/core
https://codeanywhere.com/
https://koding.com/

##简介
调试 nodejs 十分方便，内部包括:

 * picture edit
 * code
 * debug
 * terminal


##安装
```language
nvm install 0.12
git clone git://github.com/c9/core.git c9sdk
cd c9sdk
scripts/install-sdk.sh

node server.js -a demo:demo --listen 8181 -w /root/workspace
```

##Docker安装
https://hub.docker.com/r/kdelfour/cloud9-docker/
https://github.com/creationix/nvm
```language-bash
nvm install 5.0
nvm alias default 5.0
```

#Eclipse Che
http://www.eclipse.org/che/
https://hub.docker.com/r/codenvy/che/

run
```language-bash
docker run --net=host
           --name che
           --restart always
           -p 9001:8080
           -v /var/run/docker.sock:/var/run/docker.sock 
           -v /home/user/che/lib:/home/user/che/lib-copy 
           -v /home/user/che/workspaces:/home/user/che/workspaces 
           -v /home/user/che/storage:/home/user/che/storage
           -v /local:/container
           -v /home/my_assembly:/home/user/che           
           -e CHE_LOCAL_CONF_DIR=/container
           -e DOCKER_MACHINE_HOST=172.17.0.1
           codenvy/che 
```

PS: 镜像拉不到用 ```dao pull xxx```








