---
title: Mysql学习小记（四）
date: 2019-03-25 15:43:32
tags:
 - mysql
 - 计算机二级
categories: 技术博文
author: 宋天伦
---

## 2019.3.25

## 2019计算机二级mysql-第四套模拟
* [x] 选择
* [x] 基本操纵
* [x] 简单应用
* [x] 综合应用

## 选择题笔记
* 树是简单的非线性结构，故二叉树为非线性结构
* 循环队列的队头和队尾指针都会随着入队和出队发生变化
* 结构化程序设计思想包括：自顶向下、逐步求精、模块化、限制使用goto语句
* 数据库系统三级模式之间的两级映像分别为外模式/模式映像、模式/内模式映像。
* MODIFY用来修改表中的列属性；ALTER TABLE 用于修改表结构。
* 可更新的视图在创建时必须包含主键
* Mysql中，创建索引的方法有三种，CREATE TABLE、ALTER TABLE、CREATE INDEX.
* 使用UNION语句可将多个SELECT语句组合到一个数据集；合并时，多个SELECT对于的字段数和类型必须相同；只能使用一条ODER BY 或 LIMI子句，且它们必须置于最后一条SELECT语句之后。
* 触发器是由数据表上的特定事件所触发，可由INSERT\DELETE\UPDATE触发，不带有参数，不可建立在视图上。
* 事件是基于特定时间周期触发来执行某些任务，用于维护系统数据的实时性，删除事件的语句是DROP ENENT。
* 在INSERT触发器代码内可引用一个名为NEW的虚拟表来访问被插入的行。
* 使用二进制日志文件的主要目的就是在数据恢复时能够最大可能地更新数据库


## 基本操作
#### 创建表
>举例
![](http://photo-frytea.test.upcdn.net/20190325163220.png)
```
mysql> create table Dep1(
    -> deptno int primary key,
    -> dname varchar(20),
    -> higherdepton int default null,
    -> CONSTRAINT fk_higher FOREIGN KEY(deptno) REFERENCES Dept2(deptno));
```
![](http://photo-frytea.test.upcdn.net/20190325164246.png)


