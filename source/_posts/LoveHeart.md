---
title: 爱礼（爱的礼物——谐音爱你），送给你对象的爱的礼物
date: 2019-06-22 11:55:00
tags: [GitHub]
---


爱礼

<!--more-->


项目制作给我的女朋友，可以写一些恋爱情话，记录恋爱时间线，恋爱时间等。

原始项目由`hackerzhou`发起，作者预览网址失效，项目地址如下:
[项目地址](https://github.com/hackerzhou/Love)

我在原始项目上改了改，项目地址如下：
[我的项目地址](https://github.com/AomanHao/loveheart)

项目效果预览网址如下：
[效果预览](https://aomanhao.github.io/LoveHeart/)

项目放在我的主域名下的子域名内，主域名对应`Github Page`的主仓库`ID.github.io`。

---
## 指导
### 复制项目文件

[我的git项目地址](https://github.com/AomanHao/loveheart)
点到我的github，fork这个项目到自己仓库，然后点击setting设置


![](https://img-blog.nos-eastchina1.126.net/blog/blog_love_web1.png)
### 开启项目的github pages
设置页面往下拉， github pages部分，选择一个主题，开启功能，根据显示域名就能访问爱礼页面了
![](https://img-blog.nos-eastchina1.126.net/blog/blog_love_web3.png)


### 设置域名绑定

还是在github pages部分，绑定自有域名方便访问
![](https://img-blog.nos-eastchina1.126.net/blog/blog_love_web.png)

## 修改

打开i项目的index.html，以下部分根据自己需求修改吧

```
<!-- BGM区域 -->
<!-- 文字区域 -->
//起始时间 
<!-- 附加信息-->

```
修改完成，直接在浏览器预览index.html内容即可

## 主题配置

主题`blog\theme\next\config.yml`文件中`menu:`下补充一个栏目，然后直接写的项目地址
```
menu:
  home: / || home
  archives: /archives/ || archive #归档
  tags: /tags/ || tags  #标签
  #categories: /categories/ || th #分类
  相册: /photos/ || camera-retro #相册
  爱礼: http://www.aomanhao.top/LoveHeart/ || heart #恋爱线

```

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)
