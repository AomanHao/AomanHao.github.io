---
title: 谷歌浏览器加载静态文件错误，请修改DNS配置
date: 2018-08-24 16:00:00
tags: [GitHub]
---
谷歌浏览器加载静态文件错误，请修改DNS配置
<!--more-->

![](https://img-blog.nos-eastchina1.126.net/niuke_error.png)

当我登陆CSDN/牛客网的时候，页面不能正常显示，只能显示纯文字，访问百度或者视频网站的时候是可以的
报错提示<h3>静态文件加载出错，请检查当前网络情况是否正常，或者按照下面步骤修改电脑的DNS等等</h3>
折腾了一晚上

---
### 修改DNS
![](https://img-blog.nos-eastchina1.126.net/changedns1.png)
[百度经验修改DNS](https://jingyan.baidu.com/article/2fb0ba40833b0a00f2ec5f28.html)


按照要求修改了dns，失败，仍然不能正常加载网页

---
### 修改hosts文件
[百度经验修改hosts文件](http://jingyan.baidu.com/article/425e69e6e479a2be15fc16e1.html?allowHTTP=1)

hosts属于系统文件，需要谨慎操作，需要很高的权限
![](https://img-blog.nos-eastchina1.126.net/hosts_error.png)


打开hosts文件，发现最后一行是`192.168.137.1 windows10.microdone.cn`
神秘代码有没有，寻找其出处，网友指出他是`银联网银插件`修改的
[代码解释链接](https://www.v2ex.com/t/273757)

解决方法：
卸载最近安装的 网银插件/控件
（我没有就不用卸载了）


然后按照百度经验修改`hosts`文件，保存后，发现过一会打开又出现了`192.168.137.1 windows10.microdone.cn`
这下怀疑中病毒了

### 使用360断网急救箱
![](https://img-blog.nos-eastchina1.126.net/360duanwnag.png)
诊断确实是 `hosts`文件出现异常

修复在检测，依然有问题

### 使用360系统急救箱
深度检测，删了一些文件（可能中毒）
重启电脑，依然`CSDN/牛客网`的时候，页面不能正常显示

---
### 谷歌浏览器插件问题

我鬼使神差的试试用微软自带的Eage浏览器登陆`CSDN/牛客网`，可以<font color=red size="10">正常显示</font>，惊了。我这一通操作，就是换个浏览器的题

仔细回想一下，之前安装的`谷歌访问助手`插件崩溃了，我就卸载了

1、卸载`谷歌浏览器`，重新安装
>失败，不能正常显示网页`CSDN/牛客网`

2、安装`谷歌访问助手`插件
>`CSDN/牛客网`可以正常显示了。

原因：怀疑是插件的上网代理搞鬼

---
## 解决方法：谷歌浏览器谷歌访问助手重新安装









