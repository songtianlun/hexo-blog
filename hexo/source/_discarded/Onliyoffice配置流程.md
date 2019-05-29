title: Onliyoffice配置流程
url: 686.html
id: 686
categories:
  - 未分类
date: 2019-03-01 23:30:34
tags:
---

Onlyoffice是一类协同办公软件，可以和nextcloud绑定实现在线文档修改等。话不多说，我们开始配置吧。

配置教程我在网上找到了两种，分别可以用于不同的Linux系统

[使用Docker部署ONLYOFFICE Document Server](https://www.orgleaf.com/2588.html)  
[为Nextcloud安装ONLYOFFICE Document Server](https://www.orgleaf.com/2542.html)

其中第一篇可用于CentOS/RedHat一类的系统，第二篇可用于Ubuntu/Debian系统上正确部署ONLYOFFICE Document Server。

由于我的服务器是Centos系统，因此采用了第一种方式安装。

### 第一步：安装Docker

#### CentOS/RedHat/Fedora

使用yum命令安装Docker:

    yum install docker -y

启动Docker服务：

    systemctl start docker

#### Debian/Ubuntu

使用apt命令安装Docker：

    sudo apt-get install docker.io

Docker服务会自动启动。

也可以使用宝塔面板一键安装Docker。

第二步：拉取ONLYOFFICE Document Server 的Docker镜像

    sudo docker pull onlyoffice/documentserver

![](https://blog.songtianlun.cn/wp-content/uploads/2019/01/image-58.png)

### 第三步：启动Docker容器

启动Document Server镜像，并映射80端口至本地。

    sudo docker run -i -t -d -p 80:80 onlyoffice/documentserver

将Document Server映射至其它端口

    sudo docker run -i -t -d -p 9000:80 onlyoffice/documentserver

80端口常常已经被apach等web服务器占用，因此可以映射到其他的端口。

![](https://blog.songtianlun.cn/wp-content/uploads/2019/01/image-59.png)

第四步：访问OnlyOffice

使用ip/域名+断开后即可访问到安装好的服务啦！

访问之前记得在相应的部分放通端口哟！

![](https://blog.songtianlun.cn/wp-content/uploads/2019/01/image-61-1024x289.png)

刚开始的时候可能会看到502 警告，这时候稍等一下再刷新浏览器。

![](https://blog.songtianlun.cn/wp-content/uploads/2019/01/image-60-1024x300.png)