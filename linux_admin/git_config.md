git设置用户名
git config --global user.name "yihongliang"
git config --global user.email "yihl.cn@163.com"


Git设置proxy  
git config --global http.proxy http://F1335745:PnC8XSf7@10.191.131.15:3128  
git config --global https.proxy https://F1335745:PnC8XSf7@10.191.131.15:3128  
git config --global --unset http.proxy  
git config --global --unset https.proxy  


查询--get  
git config --get --global http.proxy  
git config -l  

关闭SSL CERT verification:  
git config --global http.sslVerify false  

启用默认的SSL CERT verification:  
git config --global --unset http.sslVerify  


wget代理设置  
编辑文件为：/etc/wgetrc       
添加下面两行：  
http_proxy = IP:PORT    
ftp_proxy = IP:PORT  

系统环境代理设置  
编辑文件为/etc/profile，如果只想给自己的账户设置，则编辑~/.bashrc即可  
添加三行：  
# add proxy for network  
export http_proxy="http://child-prc.intel.com:913"  
export https_proxy="http://child-prc.intel.com:913"  
export ftp_proxy=$http_proxy  
然后source /etc/profile 或者source ~/.bashrc即可  


