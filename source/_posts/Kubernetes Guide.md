title: Kubernete Guide
date: 2020/12/11 17:58:25
categories:

 - ops

tags:

 - kubernete 
 - minikube
 - k3s 
 - docker
 - rancher

---

# Introduction

## Installation

```
# install docker by https://docs.docker.com/engine/install/centos/
sudo systemctl start docker
# config aliyun mirror 
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://9wakipqn.mirror.aliyuncs.com"]
}
EOF
# install rancher
# 
```

## Docker Private Registry

```shell
docker run -d \
    -p 5000:5000 \
    -v /opt/data/registry:/var/lib/registry \
    registry

docker login 127.0.0.1:5000
docker build -f x.dockerfile -t python:3.7-alpine
docker tag python:3.7-alpine registry.container.sandseasoft.com/python:master
docker push registry.container.sandseasoft.com/python:master
```

## Kubernate Principle 

* ingress
* service
* pods

## Usage

```
#minikube by macos
brew install minikube
minikube stop
minikube delete
minikube start --driver=hyperkit/ minikube start --vm-driver=none 
minikube addons enable ingress
minikube service dashboard --url
#test NodePort
kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0
kubectl expose deployment web --type=NodePort --port=8080
minikube service web --url

#kubectl 
kubectl get pods
kubectl get service
kubectl get ingress
kubectl port-forward service/web 10001:8080
kubectl get secrets
kubectl describe service
kubectl describe ingress
kubectl describe pods
kubectl delete services my-service

```

## yaml configuration

```
kind: Service
apiVersion: v1
metadata:
  name: my-service
spec:
  type: NodePort 
  selector:
    app: tomcat
  ports:
    - port: 80 // 供集群中其它container访问端口
      targetPort: 8020 //转向后端pod中container暴露的端口
      nodePort: 9000 //节点暴露的端口
---
apiVersion: v1
kind: ReplicationController
metadata:
  name: tomcat
  namespace: default
spec:
  replicas: 1
  selector:
    app: tomcat
  template:
    metadata:
      name: tomcat
      labels:
        app: tomcat
    spec:
      volumes:
      - name: "config"
        hostPath:
          path: "/data/xxx"
      containers:
      - name: forme
        image: forme:k8s
        resources:
          limits:
            alpha.kubernetes.io/nvidia-gpu: 1
            cpu: 8
            memory: 4Gi
        ports:
        - containerPort: 8020 //该container监控的端口
        volumeMounts:
        - name: "config"
          mountPath: "/home/docker/code"
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /$1
spec:
  rules:
    - host: hello-world.info
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: web
                port:
                  number: 8080

```



# Quates

* https://rancher.com/docs/rancher/v2.x/en/installation/other-installation-methods/single-node-docker/
* https://yeasy.gitbook.io/docker_practice/
* https://sysadmins.co.za/https-using-letsencrypt-and-traefik-with-k3s/
* https://kubernetes.io/zh/docs/home/
* https://kubernetes.io/zh/docs/tasks/configure-pod-container/pull-image-private-registry/
* https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/