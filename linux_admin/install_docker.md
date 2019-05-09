## 更新现有的包列表  
sudo apt-get update  

## 安装一些允许通过HTTPS才能使用的软件包  
sudo apt install apt-transport-https ca-certificates curl software-properties-common  

## 将官方Docker存储库的GPG密钥添加到您的系统  
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -  

## 将Docker存储库添加到APT源  
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"  
sudo apt update  

## 确保您要从Docker repo安装而不是默认的Ubuntu repo  
apt-cache policy docker-ce  

## 安装Docker  
sudo apt install docker-ce  

## 检查Docker是否正在运行  
sudo systemctl status docker  

## 在不输入Sudo情况下执行Docker（可选）,将用户名添加到docker组中  
sudo usermod -aG docker ${USER}  
su - ${USER}  
> 查看添加结果：id -nG  




