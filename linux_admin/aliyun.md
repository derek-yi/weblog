## 第一步：备份原来的源文件
cd /etc/apt/  
然后会显示下面的源文件sources.list 
输入命令 sudo cp sources.list sources.list.bak 
就是将sources.list备份到sources.list.bak

## 第二步：替换源
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse  
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse  
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse  
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse  
deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse  
#### 源码(optional)  
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse  
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse  
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse  
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse  
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse  
替换并保存 sudo gedit sources.list打开文件，替换成阿里云文件即可

> 其他版本替换代号即可  
> https://baike.baidu.com/item/ubuntu/155795?fr=aladdin  
> http://mirrors.aliyun.com/ubuntu/ubuntu/ubuntu/ubuntu/dists/  

## 第三步：更新源和软件
sudo apt-get update 更新源  
sudo apt-get upgrade 更新软件 

