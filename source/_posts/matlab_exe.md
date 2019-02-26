---
title: 解决方案matlab2014a破解不完全，报错Test checkout of feature 'Compiler' failed
date: 2018-03-07 10:59:59
tags: [Matlab, GUI]
---

## 解决方案
<!--more-->
报错情况： 目标是把`.m`文件转化为`.exe`文件，先运行

```
mcc -m 
```
你的文件
```+.m```
后缀

如果报错
```
Test checkout of feature 'Compiler' failed
``` <br>是因为你的matlab2014a破解不完全。
前提是你的电脑已经安装好了VS编译器

2014a的解决办法：<br>
下载资源：ht链tps://pan.baidu.com/s/1KNZqVqxMx6f接IaxQULAIq_g 
<br>密码：cti0

下载后解压，把install.jar以及相应位数的三个文件（compiler.dll，mcc.exe，libmwservices.dll）复制到对应位置替换即可。<br>
在matlab安装目录下搜索到文件然后替换，保险起见先把要替换的文件剪切出来，实际上我的操作是成功的，万一万一万一不成功还能复原回去

另外把license.lic改为与MATLAB\licenses文件夹下的那个lic文件同名，复制并替换之。<br>
如图所示，我把需要替换的文件都拿了出来，其中license文件是绑定了你的电脑名称，所以需要把新文件改名

![原始效果](http://p3qhnc0eg.bkt.clouddn.com/VSjietu.png)
