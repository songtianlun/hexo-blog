---
title: Mysql学习小记（一）
date: 2019-03-21 10:21:39
tags:
 - mysql
 - 计算机二级
categories: 技术博文
author: 宋天伦
---

## 2019.3.21

## 本节内容
* 向已有表插入数据
* 修改字段默认值
* 简单计数
* 创建视图
* 创建用户

## 基本操作

#### 向已有表中插入数据
固定语法：
```
inset into table_name() values();
```

例如：
![](http://photo-frytea.test.upcdn.net/20190321102403.png)

>来源2019年3月计算机二级mysql第一套练习

![](http://photo-frytea.test.upcdn.net/20190321102542.png)
使用如下语句
```
insert  into tb_dept(deptno,dname,manager,telephone)values('D4','公关部','Liming','010-82953306');
```
效果：
![](http://photo-frytea.test.upcdn.net/20190321103053.png)


#### 修改已有表字段默认值
思路：现把已有字段默认值删除，然后再修改；在修改时使用alter选中修改所在的表，在删除中选中所在的字段，使用删除默认值，再使用set设置默认值。

举例：
![](http://photo-frytea.test.upcdn.net/20190321102853.png)
使用如下语句:
```
alter table tb_employee alter column salary set default 3500;
```

#### 简单计数
思路：使用select语句进行查询；
使用count（）集合函数查询进行求和查人数的和；
使用as给查询起别名；
where后面跟查询条件。
>举例：
![](http://photo-frytea.test.upcdn.net/20190321103354.png)
使用如下语句：
```
select count(*)as '总人数' from tb_employee where deptno = (select deptno from tb_dept where dname='销售部');
```
效果：
![](http://photo-frytea.test.upcdn.net/20190321103446.png)

#### 视图创建
固定语法：
```
create view view_name as select from table_name where;
# as select 后面跟的是视图中展示的字段
# where后面跟的是查询条件
```

>举例
![](http://photo-frytea.test.upcdn.net/20190321104124.png)
使用如下代码：
```
create view v_emp as select eno,ename,age,salary from tb_employee where deptno = (select deptno from tb_dept where dname='采购部');
```

## 创建新用户
固定语法：
```
create user 'username'@'host'identified by 'password';
# identified by 可以省略
```
>举例：
![](http://photo-frytea.test.upcdn.net/20190321104351.png)
使用如下语句：
```
create user 'Yaoming'@'localhost'identified by 'abc123';
```

## 简单应用
#### 设计触发器
固定语句：
使用create trigger创建触发器
创建的触发器多为后触发器，使用for each row
置空使用set 列名 =''

>举例
![](http://photo-frytea.test.upcdn.net/20190321105226.png)

部分代码:
```
CREATE ________ tr_emp after DELETE
ON tb_dept 
FOR EACH ________
UPDATE tb_employee 
SET deptno='' 
WHERE deptno=________;
delete from tb_dep WHERE deptno='D2';
SELECT * FROM tb_employee;
```
>填空
第一空为：trigger
第二空为：row
第三空为：select deptno from tb_dept

完整程序如下：
```
CREATE trigger tr_emp after DELETE
ON tb_dept 
FOR EACH row
UPDATE tb_employee 
SET deptno='' 
WHERE deptno=(select deptno from tb_dept);
delete from tb_dep WHERE deptno='D2';
SELECT * FROM tb_employee;
```

#### 设计存储函数
套路：
根据不同的mysql用户，首先查看创建函数的功能是否开启
```
-- 查看是否开启创建函数的功能
show variables like '%func%';
-- 开启创建函数的功能
set global log_bin_trust_function_creators = 1;
 ```
 ![](http://photo-frytea.test.upcdn.net/20190321112429.png)
>举例：
![](http://photo-frytea.test.upcdn.net/20190321110019.png)
 部分程序：
 ```
 DELIMITER $$
CREATE FUNCTION fn_emp (dept CHAR(20)) 
RETURNS FLOAT 
DETERMINISTIC
BEGIN 
Declare sum_salary float;
SELECT sum(salary) ______ sum_salary 
FROM tb_employee INNER JOIN tb_dept 
______ tb_employee.deptno=tb_dept.deptno 
WHERE ___________
GROUP BY dname  ; 
return  sum_salary ;
END $$
DELIMITER ;
 ```

 ![](http://photo-frytea.test.upcdn.net/20190321112741.png)
完整程序
```
DELIMITER $$
CREATE FUNCTION fn_emp (dept CHAR(20)) 
RETURNS FLOAT 
DETERMINISTIC
BEGIN 
Declare sum_salary float;
SELECT sum(salary)  into sum_salary 
FROM tb_employee INNER JOIN tb_dept 
on tb_employee.deptno=tb_dept.deptno 
WHERE  dname=dept
GROUP BY dname  ; 
return  sum_salary ;
END $$
DELIMITER ;
```

