---
title:  Matlab2014a vs2015编译器解决方法
date: 2018-03-07 11:59:59
tags: [Matlab, GUI]
---
## 准备工作
<!--more-->
前提：
电脑已经安装
1、Matlab版本2014a
2、VS版本2015

目标：
结合Matlab和VS2015，实现Matlab的GUI文件和.m文件转化为.exe文件，然后可以单独运行.exe文件

首先在Matlab命令行输入
```
mbuild -setup
```
报错红色，显示没有选择项，此处没有截图不直观
我猜测可能是matlab2014a的破解不完全

------------------------------
## 解决方案

下载资源链接：https://pan.b链aidu.com/s/1hoDxMKFU2l-3ZhTObFetCw 

密码：vdlq

然后替换文件

附件下面的将`mexopts/`下的`msvc2015.xml`和`msvcpp2015.xml`<br>
复制到`Matlab`目录下的`bin/win64/mexopts`下就可以了



首先在Matlab命令行输入
```
mbuild -setup
```
![原始效果](https://img-blog.nos-eastchina1.126.net/VS2015_1.png)

然后输入
```
mex -setup
```
![原始效果](https://img-blog.nos-eastchina1.126.net/VS2015_2.png)

选项都选择C++的就哦了
