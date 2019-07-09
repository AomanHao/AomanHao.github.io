---
title: Hexo博客Yilia主题首页菜单中文乱码两种解决方案
date: 2018-02-06 23:22:06
tags: [GitHub, Hexo]
---

hexo-github博客首页菜单中文乱码两种解决方案
<!--more-->
## 方案一：

菜单设置成中文显示，编辑博客根目录下的`_config.yml`文件

![在这里插入图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MjgwOTY2LWJhMDVlNGQ3YjAwNWI4ODYucG5n)


设置`language`字段如下:
```
language: zh-Hans
```
或者
```
language: zh-CN
```
![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MjgwOTY2LTlkMjk2MTRlNWFlN2JmM2UucG5n)


取决于你的主题theme目录下的language目录下有`zh-Hans.yml`还是`zh-CN.yml`![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MjgwOTY2LTViYTFiZGIwNjhkNjQ3YTAucG5n)

## 方案二：

根目录下的配置文件是_config.yml文件


![在这里插入图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MjgwOTY2LTdiZDY5Yzc3Y2U0NWNhOTgucG5n)
我们需要打开此文件，然后编辑文字。

但是保存之后的格式可能跟文件本身的格式编码不一样，所以会出现乱码问题。

推荐用`sublime`，`VScode`，`atom`等文本编辑器打开，这三款开源软件写代码也很便利。
此处用atom文本编辑器打开编辑，保存后不会出现乱码问题了

最后效果如下：
![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly91cGxvYWQtaW1hZ2VzLmppYW5zaHUuaW8vdXBsb2FkX2ltYWdlcy82MjgwOTY2LWU3YWE2MmI0YmZhNjQ0MTMucG5n)

希望能帮助到各位！
[我的个人博客文章地址，欢迎访问](http://www.aomanhao.top/2018/02/06/hexo_1/)

[我的CSDN文章地址，欢迎访问](https://blog.csdn.net/Aoman_Hao/article/details/79275570)

[我的简书文章地址，欢迎访问](https://www.jianshu.com/p/81027eb27a39)

[我的GitHub主页，欢迎访问](https://github.com/AomanHao)