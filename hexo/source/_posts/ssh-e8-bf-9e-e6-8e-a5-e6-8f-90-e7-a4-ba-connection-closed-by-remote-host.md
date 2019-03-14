---
title: ssh连接提示 "Connection closed by remote host"
url: 904.html
id: 904
categories:
  - 技术博文
date: 2019-02-21 12:23:58
tags:
---

最近在研究如何将博客放在github page中，搜索之后发现要使用hexo博客引擎，过程中使用到了ssh，我使用的阿里云轻量服务器出现了一些问题，最终成功，将过程中出现的问题及简单步骤记录如下：

#### 创建ssh key及获取ssh key

    $ cd ~/. ssh #检查本机已存在的ssh密钥

如果提示：No such file or directory 说明你是第一次使用git。

    $ ssh-keygen -t rsa -C "邮件地址"

最终会生成一个文件在用户目录下，打开用户目录，找到`.ssh\id_rsa.pub`文件，记事本打开并复制里面的内容，打开你的github主页，进入个人设置 -> SSH and GPG keys -> New SSH key：

之后测试是否连接成功

    $ ssh -T git@github.com

若出现问题，可以使用如下代码输出调试信息

    $ ssh -T -v git@github.com

#### ssh连接提示 "Connection closed by remote host"

我先是遇到了无响应的问题，解决方式是修改/etc/ssh/sshd_config文件中的port端口  
  
之后遇到的问题如题，解决方案依旧在上述文件中，修改如下字段  
# MaxSessions 10  
现去掉#，再将数值改大。

当然也可以通过代码查看ssh连接状态

    $ who

如果想要停止连接

    $ ps aux |grep sshd 

再使用获取到的people id停止

    $ kill -111