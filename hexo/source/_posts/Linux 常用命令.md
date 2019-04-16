---
title: Linux 常用命令
url: 568.html
id: 568
categories:
  - 技术博文
date: 2019-01-14 20:32:31
tags: linux
---

# (Centos)
--------

## 端口占用查询

    netstat -apn
### Centos查看端口占用情况命令
>比如查看80端口占用情况使用如下命令：

`lsof -i tcp:80`
### 列出所有端口

`netstat -ntlp`

### 程序归属（master为例）

    locate  master | grep '/master$'

#### 初始化（新安装命令生效）

    sudo updatedb

## 进程管理

### 查进程

    ps命令查找与进程相关的PID号：
        ps a 显示现行终端机下的所有程序，包括其他用户的程序。
        ps -A 显示所有程序。
        ps c 列出程序时，显示每个程序真正的指令名称，而不包含路径，参数或常驻服务的标示。
        ps -e 此参数的效果和指定"A"参数相同。
        ps e 列出程序时，显示每个程序所使用的环境变量。
        ps f 用ASCII字符显示树状结构，表达程序间的相互关系。
        ps -H 显示树状结构，表示程序间的相互关系。
        ps -N 显示所有的程序，除了执行ps指令终端机下的程序之外。
        ps s 采用程序信号的格式显示程序状况。
        ps S 列出程序时，包括已中断的子程序资料。
        ps -t<终端机编号> 指定终端机编号，并列出属于该终端机的程序的状况。
        ps u 以用户为主的格式来显示程序状况。
        ps x 显示所有程序，不以终端机来区分。
    

### 杀进程

    使用kill命令结束进程：kill xxx
     例：kill －9 324
       Linux下还提供了一个killall命令，可以直接使用进程的名字而不是进程标识号，例如：# killall -9 NAME

## Docker

### Docker stop停止/remove删除所有容器

```
    $ docker ps // 查看所有正在运行容器
    $ docker stop containerId // containerId 是容器的ID
    
    $ docker ps -a // 查看所有容器
    $ docker ps -a -q // 查看所有容器ID
    
    $ docker stop $(docker ps -a -q) //  stop停止所有容器
    $ docker  rm $(docker ps -a -q) //   remove删除所有容器

```

### 批量删除Docker中已经停止的容器

```
方法一： 

#显示所有的容器，过滤出Exited状态的容器，取出这些容器的ID， 

sudo docker ps -a|grep Exited|awk '{print $1}' 

#查询所有的容器，过滤出Exited状态的容器，列出容器ID，删除这些容器 

sudo docker rm \`docker ps -a|grep Exited|awk '{print $1}'\` 

方法二： #删除所有未运行的容器（已经运行的删除不了，未运行的就一起被删除了） 

sudo docker rm $(sudo docker ps -a -q) 

方法三： #根据容器的状态，删除Exited状态的容器 

sudo docker rm $(sudo docker ps -qf status=exited) 

方法四： 

#Docker 1.13版本以后，可以使用 

docker containers prune 命令，删除孤立的容器。 

sudo docker container prune #删除所有镜像 

sudo docker rmi $(docker images -q)
```

## 实用指令

### 统计当前目录下所有文件及文件夹大小

```
    du -h --max-depth=1
```

### 创建任意网站镜像

```
wget -mk -w 20 http://www.example.com/

//命令行中的20代表间隔20秒下载一个文件，这样可以避免网站的访问过于频繁。你可以调小点，但当你是备份别人的站时，还是为别人的服务器考虑下吧。
```

## 问题解决
### git "ssh-add ~/.ssh/id_rsa" Could not open a connection to your authentication agent问题解决
使用git，添加私钥时发生如下错误

```ssh-add ~/.ssh/id_rsa```
输出错误： ```Could not open a connection to your authentication agent```

解决此问题的方法是执行下
```eval `ssh-agent -s```
然后再次执行ssh-add ~/.ssh/id_rsa就可以顺利执行了