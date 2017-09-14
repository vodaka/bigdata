# 1 Hadoop cluster deployment
## 1.1 packages
- jdk : .rpm or .tar.gz
- hadoop: apache hadoop
## 1.2 install
- jdk: .rpm format,   # rpm -ivh
> if use the rpm package to install jdk , the default JAVA\_HOME is /usr/java/default/

>  $ vi /etc/profile

> $ source /etc/profile
##  1.3 master 免密码登录
- 在master上

   \# ssh-keg-gen -t rsa

   \# sudo ssh-copy-id -i /root/.ssh/id_rsa.pub $MASTER_NODE_IP
    
