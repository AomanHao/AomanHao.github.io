---
title: Hexo主题Next配置（二）
date: 2019-01-20 11:55:00
tags: [GitHub, Hexo, Next]
---


Hexo主题Next配置（二）

<!--more-->

## 背景图片加载
### 原理
自动更换背景是修改添加背景的css样式实现

### 图片来源
https://source.unsplash.com/

### 修改背景样式
修改themes\next\source\css\ _custom\custom.styl文件，这个是Next故意留给用户自己个性化定制一些样式的文件，添加以下代码：
```
body {
    background:url(https://source.unsplash.com/random/1600x900);
    background-repeat: no-repeat;
    background-attachment:fixed;
    background-position:50% 50%;
    background-size:cover;
}
```
#### 参数细节
`url`可更换为自己喜欢的图片的地址。
`repeat：`是否重复出现
`attachment：`定义背景图片随滚动轴的移动方式
`position：`设置背景图像的起始位置。
`background-size:cover`为可能有助于大分辨率下背景图的显示

### 修改不透明度（可加可不加，看实际效果）
因为next主题的背景是纯透明的，这样子就造成背景图片的影响看不见文字，这对于博客来说肯定不行。

调整背景的不透明度可以更加美观，参数`opacity:`建议调整`0.8`至`0.95`之间。
修改`themes\next\source\css\ _custom\custom.styl`文件。在后面添加如下代码
```
.main-inner { 
    margin-top: 60px;
    padding: 60px 60px 60px 60px;
    background: #fff;
    opacity: 0.9;
    min-height: 500px;
}
```
其中：`background: #fff;` 白色
`opacity: 0.9;`为不透明度

注：效果还可以，但是博客备份在github上，网速限制加载的比较忙，建议博客放在国内的Coding上


---

### 侧边栏社交小图标设置

侧边栏默认只有
打开主题配置文件（_config.yml），搜索social_icons:,在fontawesome图标库（[网址](https://fontawesome.com/)）找自己喜欢的小图标，并将名字复制在如下位置配置文件

```
social:
  GitHub: https://github.com/yourname || github
  E-Mail: mailto:邮箱地址 || envelope
  Weibo: https://weibo.com/yourname || weibo
  CSDN: https://me.csdn.net/yourname || book
  #Google: https://plus.google.com/yourname || google
  #Twitter: https://twitter.com/yourname || twitter
  #FB Page: https://www.facebook.com/yourname || facebook
  #VK Group: https://vk.com/yourname || vk
  #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
  #YouTube: https://youtube.com/yourname || youtube
  #Instagram: https://instagram.com/yourname || instagram
  #Skype: skype:yourname?call|chat || skype

```

### 设置网站图标
#### 下载图标
[图标网站](https//www.easyicon.net/)

下载尺寸32 X 32的图标，文件名必须是favicon.ico。
#### 图标放在
2.将图标放在下一个/源极/图像文件夹目录下面。
#### 配置
3.配置主题目录中的配置文件（敲黑板，重点）

之前网上查到的方法如下:(并没有成功）