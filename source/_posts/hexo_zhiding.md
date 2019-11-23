---
title: Hexo博客Next主题文章置顶相关
date: 2019-11-23 21:44:45
tags: [Hexo, Next, Github]
---

Hexo博客Next主题文章置顶相关
<!--more-->
## 置顶方法
### 一、修改库文件
### 二、插件配置
```
$ npm uninstall hexo-generator-index --save
$ npm install hexo-generator-index-pin-top --save
```

## 置顶标志
到目前为止，置顶功能已经可以实现了。所有相关博文到这边就结束了。

不过置顶的文章显示在最上面之后，如果没有明确的置顶标志，是不是感觉有点怪怪的呢？

设置置顶标志
打开：/blog/themes/next/layout/_macro 目录下的post.swig文件，定位到<div class="post-meta">标签下，插入如下代码：
```
          {% if post.top %}
            <i class="fa fa-thumb-tack"></i>
            <font color=7D26CD>置顶</font>
            <span class="post-meta-divider">|</span>
          {% endif %}
```

效果展示： 

---

[参考文章1](https://www.jianshu.com/p/42a4efcdf8d7)
[参考文章2](https://blog.csdn.net/qq_30930805/article/details/88890124)

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


