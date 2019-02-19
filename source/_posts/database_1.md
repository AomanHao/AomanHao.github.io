---
title: 数据库Mysql_3_4
date: 2018-03-04 10:59:59
tags: [Mysql, Java]
---
mysql常用命令
<!--more-->
##  一、 mysql常用命令
### 1.1 管理

    CREATE DATABASE Aoman_OS -- 创建数据库
	USE  Aoman_OS -- 使用数据库
	DROP DATABASE Aoman_OS  -- 删除数据库

### 1.2 数据库内容
	CREATE TABLE employee(  -- 创建数据库表格
	id INT,NAME VARCHAR(20),gender VARCHAR(2),title VARCHAR(10),email VARCHAR(20)
	);
	SELECT * FROM employee -- 查看数据库表格

### 2.1 增加数据库内容
	INSERT INTO employee VALUES(1,'依依','女','程序员鼓励师','123@163.com');
	INSERT INTO employee VALUES(2,'尔尔','男','程序开发工程师','124@163.com');
	INSERT INTO employee VALUES(3,'散散','男','程序维护工程师','125@163.com');

### 2.2 插入部分数据
		INSERT INTO employee (id,NAME) VALUES (4,'思思');

### 2.3 修改数据
	UPDATE employee SET gender='女',title='文秘' WHERE id =4;

### 2.4 删除表中所有数据
	DELETE	 * FROM employee

### 2.5 删除数据表
	DROP FROM employee

### 3.1 查询
	SELECT id AS '1' FROM employee
	SELECT id AS '1' ，NAME AS '尔尔' FROM employee

### 3.2 不重复的查询
	SELECT DISTINCT email FROM employee

### 3.3 条件查询
	SELECT * FROM employee WHERE id=1 OR NAME = '思思' ; -- or 并集
	SELECT * FROM employee WHERE id=1 AND NAME = '思思' ; -- and 交集

### 3.4 判断查询
	大于 > ,小于 < ,等于 = 
	不等于 ！= 或者 <>， 在什么之间 between 1 and 2，
	非空 isnot null 或者 不等于 ''

### 3.5 模糊查询
	SELECT * FROM studet WHERE NAME LIKE '思%'
	%代替任何字符，任何长度的字符
	-仅仅代替一个字符


### 3.6 asc 升序 desc 降序
	默认情况下:是按照插入顺序进行排序
	SELECT * FROM student ORDER BY id ASC ;
	需求:servlet成绩是一个降序排序
	SELECT * FROM student ORDER BY servlet DESC ;

## 二、小练习

	CREATE TABLE student2(
		id INT,
		NAME VARCHAR(20),
		chinese FLOAT,
		english FLOAT,
		math FLOAT
	);

	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(1,'张小明',89,78,90);
	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(2,'李进',67,53,95);
	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(3,'王五',87,78,77);
	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(4,'李一',88,98,92);
	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(5,'李来财',82,84,67);
	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(6,'张进宝',55,85,45);
	INSERT INTO student2(id,NAME,chinese,english,math) VALUES(7,'黄蓉',75,65,30)


#### 查询操作练习(在学生表数据基础上：student.sql)
-- 	查询表中所有学生的信息。

	SELECT * FROM student2 ;
-- 查询表中所有学生的姓名和对应的英语成绩。

	SELECT  NAME ,english FROM student2
-- 	使用别名表示学生分数。

	SELECT id AS '编号',NAME AS '姓名',chinese AS '语文',english AS '英语',math AS '数学' FROM student2 ;

-- 	查询姓名为李一的学生成绩

	SELECT * FROM student2 WHERE NAME = '李一';

-- 	查询英语成绩大于等于90分的同学

	SELECT * FROM student2 WHERE english >=90

-- 	查询总分大于200分的所有同学

	SELECT * FROM student2 WHERE (chinese+english+math)>200;

-- 	查询所有姓李的学生英语成绩。

	SELECT NAME,english FROM student2 WHERE NAME LIKE '李%'

-- 	查询英语>80或者总分>200的同学

	SELECT * FROM student2 WHERE english >80 OR (chinese+english+math)>200;
