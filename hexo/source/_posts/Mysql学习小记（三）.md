---
title: Mysql学习小记（三）
date: 2019-03-24 16:02:47
tags:
 - mysql
 - 计算机二级
categories: 技术博文
author: 宋天伦
---

## 2019.3.24

## 2019计算机二级mysql-第三套模拟
* [x] 选择
* [x] 基本操纵
* [ ] 简单应用
* [ ] 综合应用

## 选择题笔记
* 栈支持子程序调用，符合栈的特点
* 二叉树中叶子节点的计算公式：n0=n2+1
>n0 是叶子节点的个数
n2 是度为2的结点的个数

* 冒泡排序，简单选择排序，直接插入排序在最坏情况下需比较n（n-1）/2次，而堆排序在最坏的情况下需要比较nlog<sub>2</sub>n

* 数据库应用系统中的核心问题是数据库的设计
* E-R模型中的实体和联系均可以表示为关系
* 数据库的三级模式中，外模式可以有多个，而内模式和模式只能有一个
* AUTO_INCREMENT列不能直接填充数字1


## 简单应用

#### 新建字段
>举例
![](http://photo-frytea.test.upcdn.net/20190324170215.png)
使用如下代码：
```
alter table tb_student add ssex char(1) default 'M'
```
效果如下
![](http://photo-frytea.test.upcdn.net/20190324170407.png)

#### 修改记录
>举例：![](http://photo-frytea.test.upcdn.net/20190324170447.png)
```
update tb_student set smajor='计算机' where sno=100;
```
![](http://photo-frytea.test.upcdn.net/20190324170548.png)

#### 创建视图+计算
![](http://photo-frytea.test.upcdn.net/20190324170834.png)
```
create view v_avg(cname,canerage) as select cname,avg(grade) from tb_score group by cname;
```
![](http://photo-frytea.test.upcdn.net/20190324170946.png)

#### 创建索引
![](http://photo-frytea.test.upcdn.net/20190324171029.png)
```
alter table tb_student add unique index idx_stu(sno);
```
* 使用alter选择表
* 使用add添加唯一索引值
* sno为添加索引的字段
![](http://photo-frytea.test.upcdn.net/20190324171106.png)