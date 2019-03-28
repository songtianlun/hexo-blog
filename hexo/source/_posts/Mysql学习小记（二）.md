---
title: Mysql学习小记（二）
date: 2019-03-24 11:11:15
tags:
 - mysql
 - 计算机二级
categories: 技术博文
author: 宋天伦
---

## 2019.3.24

## 2019计算机二级mysql-第二套模拟
* [x] 选择
* [x] 基本操纵
* [ ] 简单应用
* [ ] 综合应用


## 选择题笔记
1.CREATE DATABASE 和CREATE SCHEMA命令都是创建一个数据库
2.DROP DATABASE 删除一个数据库，将已创建的数据库文件从磁盘空间上清除，数据库中的所有数据也将被删除
3.ALTER DATABASE可以修改数据库的默认字符集和字符集的校对规则，影响数据库现有对象。
4.InnoDB存储引擎是事务安全的，支持外键
5.MyISAM存储引擎不支持事务处理应用
6.MEMORY存储引擎速度快，适合用于存储临时数据的临时表，不支持事务处理应用
7.CSV存储引擎操作的是一个标准的CSV报表文件，不支持事务处理
8.索引是为了提高数据库检索效率，可建立在一张表的一列或是多列，但会降低更新数据表的速度
9.当触发器涉及对表自身的更新操作时，只能使用BRFORE UPDATE触发器，而 AFTER UPDATE触发器触发器将不被允许。
10.在存储过程体中，使用DECLARE命令可以声明局部变量，用来存储存储过程体中的临时结果，基本语法为DELARE var_name type [DEFAULT value],var_name为局部变量名称
11.REVOKE命令可撤销用户权限，保留用户

## 基础操作
#### 列求和
>举例:
![](http://photo-frytea.test.upcdn.net/20190324114537.png)
使用如下语句:
```
select sum(price) as total from tb_commodity where origin='北京'and cname='电视机';
```
效果如下：
![](http://photo-frytea.test.upcdn.net/20190324114614.png)

#### 删除字段
>举例
![](http://photo-frytea.test.upcdn.net/20190324114758.png)
使用如下语句
```
alter table tb_commodity drop desc1;
```
效果如下:
![](http://photo-frytea.test.upcdn.net/20190324114857.png)

#### 为新用户指定某字段权限
>例
![](http://photo-frytea.test.upcdn.net/20190324120355.png)
使用如下代码
```
mysql> grant select(cno,cname)
    -> on tb_commodity
    -> to 'client@localhost'
    -> with grant option;
```
效果如下：![](http://photo-frytea.test.upcdn.net/20190324120445.png)