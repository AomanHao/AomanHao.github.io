---
title: 数据库Mysql_约束
date: 2018-03-04 12:59:59
tags: [Mysql, Java]
---
数据库约束 
<!--more-->
## 数据库约束
### 1.1 默认值约束(default)
### 1.2 非空约束( not null )
### 1.3 唯一约束(unique)

	CREATE TABLE test(
	id INT  UNIQUE ,-- 唯一
	NAME VARCHAR(20) NOT NULL, -- 非空
	gender VARCHAR(2) DEFAULT '男' -- 默认值约束
	);

### 1.4 主键约束(primary key 作用:非空+唯一约束)
### 1.5 自增长约束(auto_increment)
	CREATE TABLE test2(
		id INT  PRIMARY KEY AUTO_INCREMENT,-- 非空+唯一约束+自增长约束
		NAME VARCHAR(20) ,
		gender VARCHAR(2) ,
	);

### 1.6 外键约束(属于数据库中表的设计)
### 1.6.1 外键约束:约束两个或者两个以上的表的数据，一般情况有两种表(主表,副表)
	DROP TABLE employee2
	DELETE FROM employee2

	SELECT * FROM employee2
	SELECT * FROM dept

### 1.6.2 员工表
	CREATE TABLE employee2(
		id INT PRIMARY KEY AUTO_INCREMENT,
		NAME VARCHAR(20),
		deptId INT,
		-- 添加外键约束
		CONSTRAINT employee_dept_fk FOREIGN KEY (deptId) REFERENCES dept(id)
	--     声明		 外键名称	外键	被约束的字段  关联     部门表中id的字段
	);

	INSERT INTO employee2 (NAME,deptId) VALUES('张三',1) ;
	INSERT INTO employee2 (NAME,deptId) VALUES('李四',2) ;
	INSERT INTO employee2 (NAME,deptId) VALUES('王五',1) ;
	INSERT INTO employee2 (NAME,deptId) VALUES('陈六',1) ;

可以设计一个独立的表-部门表 专门用来存储部门名称,来解决数据冗余的问题
### 1.6.3 部门表(主表,约束别人的表)

	CREATE TABLE dept(
		id INT PRIMARY KEY AUTO_INCREMENT ,
		NAME VARCHAR(20) -- 部门名称
	);

#### 插入几个部门名称
	INSERT INTO dept (NAME) VALUES ('软件开发部') ;
	INSERT INTO dept (NAME) VALUES ('软件维护部') ;


#### 给员工表中插入数据
	INSERT INTO employee2 (NAME,deptId) VALUES('王五',1) ;
	INSERT INTO employee2 (NAME,deptId) VALUES('陈六',1) ;
	INSERT INTO employee2 (NAME,deptId) VALUES('李四',2) ;

#### 给部门表添加数据
	INSERT INTO dept (id,NAME) VALUES(3,'硬件开发部');
#### 修改数据
	UPDATE employee2 SET deptId = 3 WHERE id = 3;

#### 删除数据
	DELETE FROM employee2 WHERE id =2;

### 1.7 补充
--常遇到字段类型:
#### 1)char(20) vs varchar(20)

> char(20):是一个固定长度的字符串,存储字符串内容,一定是20个字符串。<br>
varchar(20):可变的字符串长度,实际存储的时候是根据当前实际的字符串长度

DROP TABLE test ;
#### 2) int 和int(4)

> int:默认的长度11位,再存储数值类型的时候,存储实际长度<br>
int(4):固定长度
