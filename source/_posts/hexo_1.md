---
title: hexo-github博客首页菜单中文乱码两种解决方案
date: 2018-02-06 23:22:06
tags: [GitHub, Hexo]
---

hexo-github博客首页菜单中文乱码两种解决方案
<!--more-->
## 方案一：

菜单设置成中文显示，编辑博客根目录下的`_config.yml`文件

![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/6280966-ba05e4d7b005b886.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/704/format/webp)


设置`language`字段如下:
```
language: zh-Hans
```
或者
```
language: zh-CN
```
![这里写图片描述](https://upload-images.jianshu.io/upload_images/6280966-9d29614e5ae7bf3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/573/format/webp)
<<<<<<< HEAD
=======

>>>>>>> 18775685f6f00718757e97d762a03862d8046aa8

取决于你的主题theme目录下的language目录下有`zh-Hans.yml`还是`zh-CN.yml`![这里写图片描述](https://upload-images.jianshu.io/upload_images/6280966-5ba1bdb068d647a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/676/format/webp)

<<<<<<< HEAD
取决于你的主题theme目录下的language目录下有`zh-Hans.yml`还是`zh-CN.yml`![这里写图片描述](https://upload-images.jianshu.io/upload_images/6280966-5ba1bdb068d647a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/676/format/webp)


=======






>>>>>>> 18775685f6f00718757e97d762a03862d8046aa8
## 方案二：

根目录下的配置文件是_config.yml文件

<<<<<<< HEAD
=======

>>>>>>> 18775685f6f00718757e97d762a03862d8046aa8
![在这里插入图片描述](https://upload-images.jianshu.io/upload_images/6280966-7bd69c77ce45ca98.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/704/format/webp)
我们需要打开此文件，然后编辑文字。

但是保存之后的格式可能跟文件本身的格式编码不一样，所以会出现乱码问题。

推荐用`sublime`，`VScode`，`atom`等文本编辑器打开，这三款开源软件写代码也很便利。
此处用atom文本编辑器打开编辑，保存后不会出现乱码问题了

最后效果如下：
![这里写图片描述](https://upload-images.jianshu.io/upload_images/6280966-e7aa62b4bfa64413.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/573/format/webp)
