---
title: 私有vpn搭建工具集合及靠谱的vpn提供商
date: 2019-04-12 20:04:37
categories:
  - 技术博文
tags:
  - vpv
  - shadowsocks
  - ssr
  - outline
  - 泡芙云
author: 宋天伦
---

经过长时间的摸索及入坑之后，终于找到两种比较好的vpn上网方式，一种是自建站点，一种是使用服务商提供的，当然相比之下第一种更加靠谱，下面详细介绍一下：

## vps自建vpn方法

#### shadowsocks(ss)

传送门：[shadowsocks官网](https://shadowsocks.org/en/index.html)

针对这种方式，之前有写到一篇文章详细介绍：
- [vps使用Shadowsocks搭建vpn](https://frytea.com/2019/01/12/vps-shi-yong-shadowsocks-da-jian-vpn/)

文章中详细介绍了如何shasowsocks的搭建流程，同时在我的资源分享站点（[https://data.frytea.com](https://data.frytea.com)）中分享了需要用到的服务器端及pc端、移动端客户端软件：
- 安卓客户端：[下载](https://data.songtianlun.cn/vpn/shadowsocks--universal-4.6.5.apk)

- windows客户端：[下载](https://data.songtianlun.cn/vpn/Shadowsocks-4.1.3.1.zip)


#### SSR

ssr的安装教程及各种信息我找到一个资源相对较全的网站：
传送门：[ssr中文网](https://ssr.tools/)

在这里摘录几篇比较实用的文章：

首先搭建ssr需要使用到vps，于是就有了:
- [适合搭建SSR的国外VPS服务器推荐汇总](https://ssr.tools/55)

有了vps，下面开始搭建:
- [SSR一键安装脚本 (ShadowsocksR一键安装教程)](https://ssr.tools/31)

安装好之后，在需要科学上网的设备上安装客户端：
- [SSR各平台客户端下载汇总](https://ssr.tools/175)

而对于苹果用户，需要下载第三方提供的ssr客户端：
- [iphone/ipad等苹果设备IOS系统 免费SSR客户端推荐汇总](https://ssr.tools/122)
- [IOS 免费SSR客户端 Potatso Lite下载及使用教程（iphone/ipad可用）)](https://ssr.tools/125)

而在大陆区，相关vpn软件早就下架，此时需要申请一个美国apple id
而对于苹果用户，需要下载第三方提供的ssr客户端：
- [美国Apple ID申请注册教程 亲测可用 （美区Apple ID注册）](https://ssr.tools/104)


vpn和ss/ssr有一定区别，而对于ss和ssr来说，两者系出同门，难分伯仲，二者区别我也找了一篇文章来介绍，主要摘录如下：
>以前我们翻墙的时候最常用的就是vpn了，而2年前，ss被开源(ss出现一年后，开源社区的破娃小姐姐在ss的基础上发布了ssr)，现在已经是最流行的翻墙方案。

- [Vpn与ss/ssr的区别](https://deeponion.org/community/threads/vpnss-ssr.901/)

#### Outline

outline是谷歌推出的一整套系统，包括服务器端、可视化服务管理端及移动端整套，可以用来很方便直接的搭建自己的vpn，特点在于它带有一个可视化的管理软件，可以用来一键分享、授权vpn访问权限，当然，也是需要搭建在自己的vps上的，详细说明见官网，官网给出了很详细的安装流程。

- [官网传送门](https://getoutline.org/zh-CN/home)

#### 泡芙云
一直受到第三方vpn无良商人的毒害，如今终于找到一个比较靠谱的vpn提供商，那就是泡芙云，价格不贵，最便宜8元一个月就可以享受到100m的vpn服务，而且泡芙云网站为Puff Networks LLC(US)所有，受美国当地法律保护。

- [官网传送门](https://www.paofucloud.com/)

美中不足的地方在于这个网站必须翻墙才能上去，因此可以先使用蓝灯等比较廉价的vpn注册，再使用泡芙云提供的服务。

