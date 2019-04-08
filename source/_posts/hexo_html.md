---
title: Hexo博客多样写作样式
date: 2018-04-03 10:59:59
tags: [Hexo]
toc: true
---

Hexo博客多样写作样式
<!--more-->

## 好玩的写作样式
多样的写作样式，可以增加文章的趣味性，避免网页看起来单调乏味。不过也不是越多越好，合理的搭配写作样式可以事半功倍，样式只是为了让文章更美观，更适合阅读，而过多的样式使文章网页看起来杂乱无章，付出与效果不成正比。我们使用 Markdown也是为了使文字效果更加美观，腾出时间在文字上。

### 主题自带样式 文本居中引用
效果：
{% cq %}
人生乃是一面镜子，
从镜子里认识自己，
我要称之为头等大事，
也只是我们追求的目的！
{% endcq %}

源码：
```
{% cq %}
人生乃是一面镜子，
从镜子里认识自己，
我要称之为头等大事，
也只是我们追求的目的！
{% endcq %}
```
更多 NexT 主题自带的标签样式，请点击：http://theme-next.iissnan.com/tag-plugins.html

11.02主题自带样式 note 标签
在主题配置文件_config.yml里有一个关于这个的配置，但官方文档没有提供 HTML 的使用方式，个人认为这种方式更简单，也不会产生一些奇怪的显示 bug……

<div class="note default"><p>default</p></div>
default

<div class="note primary"><p>primary</p></div>
primary

<div class="note success"><p>success</p></div>
success

<div class="note info"><p>info</p></div>
info

<div class="note warning"><p>warning</p></div>
warning

<div class="note danger"><p>danger</p></div>
danger

<div class="note danger no-icon"><p>danger no-icon</p></div>
danger no-icon

首先可以在主题配置文件中需要配置下，贴上我的：

# Note tag (bs-callout).
note:
  # 风格
  style: flat
  # 要不要图标
  icons: true
  # 圆角矩形
  border_radius: 3
  light_bg_offset:
里面的三种风格长啥样？开启图标长啥样？可以查看这个页面，更多的介绍也在这个页面，请自行查看。

11.03主题自带样式 label 标签
首先可以在主题配置文件中有配置，需要配置下，贴上我的:

# Label tag.
label: true
然后效果如下（@ 前面的是label的名字，后面的是要显示的文字）：

default
{% label default@default %}
primary
{% label primary@primary %}
success
{% label success@success %}
info
{% label info@info %}
warning
{% label warning@warning %}
danger
{% label danger@danger %}
11.03主题自带样式 tabs 标签
效果：

选项卡 1
选项卡 2
选项卡 3
这是选项卡 2

源码：

{% tabs 选项卡, 2 %}
<!-- tab -->
**这是选项卡 1** 呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈呵呵哈哈哈哈哈哈哈哈……
<!-- endtab -->
<!-- tab -->
**这是选项卡 2**
<!-- endtab -->
<!-- tab -->
**这是选项卡 3** 哇，你找到我了！φ(≧ω≦*)♪～
<!-- endtab -->
{% endtabs %}
首先可以在主题配置文件中有配置，需要配置下，贴上我的：

# Tabs tag.
tabs:
  enable: true
  transition:
    tabs: true
    labels: true
  border_radius: 0
然后上面源码中, 2表示一开始在第二个选项卡，非必须，若数值为-1则隐藏选项卡内容。更多用法请查看这个页面。

11.04主题自带样式 tabs 标签
源码：

{% btn https://www.baidu.com, 点击下载百度, download fa-lg fa-fw %}
效果：点击下载百度
关于按钮的更多使用可以前往这个页面查看。