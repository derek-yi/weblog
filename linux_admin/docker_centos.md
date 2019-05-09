## pull docker.centos  
docker pull centos:7.2.1511  

## 运行镜像  
docker  run --network host --privileged -v /opt/home:/opt/home -ti 9aec5c5fe4ba /bin/bash  

## docker.centos 配置代理  
vi /etc/yum.conf  
proxy=http://xxx.com:8080/  

## 修改alias  
[root@CTU1000124604 /]# vi /root/.bashrc  
[root@CTU1000124604 /]# alias cp=cp  
[root@CTU1000124604 /]# alias mv=mv  
[root@CTU1000124604 /]# alias rm=rm  

## 安装软件  
yum install rsync  
yum install bzip2  
yum install patch  
yum install dos2unix  
yum install gcc  
yum install make  

## 错误处理  
1. /lib/ld-linux.so.2: bad ELF interpreter: No such file or directory  
> yum install glibc.i686  
2. libstdc++.so.6: cannot open shared object file: No such file or directory  
> yum install libstdc++.so.6  

## 删除已停止的容器、dangling 镜像、未被容器引用的 network 和构建过程中的 cache  
docker system prune   

## 保存docker修改  
docker ps  
docker commit f7c8f6d1f454 m2k:a001  
