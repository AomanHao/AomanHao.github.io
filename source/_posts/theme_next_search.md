---
title: Hexo博客Next主题站内搜索模块相关，解决搜索无效、一直loading的问题
date: 2019-01-30 21:55:00
tags: [GitHub, Hexo, Next]
---


Hexo博客Next主题站内搜索模块相关，解决搜索无效、一直loading的问题

<!--more-->

## 站内搜索配置
设置方法：
首先安装`hexo-generator-searchdb`插件

```
npm install hexo-generator-searchdb --save
```

编辑博客根目录下的`博客本地目录/_config.yml`站点配置文件，新增以下内容到任意位置，`search`顶格放否则可能没效果：

```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```
[![klzbon.md.png](https://s2.ax1x.com/2019/01/30/klzbon.md.png)](https://imgchr.com/i/klzbon)

编辑`博客本地目录/themes/next/_config.yml` 主题配置文件，启用本地搜索功能,将`local_search:`下面的`enable:`的值，改成`true`，`local_search`顶格放置。

```
local_search:
  enable: true
  # if auto, trigger search by changing input
  # if manual, trigger search by pressing enter key or search button
  trigger: auto
  # show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # unescape html strings to the readable one
  unescape: false
```
[![k1pk7j.md.png](https://s2.ax1x.com/2019/01/30/k1pk7j.md.png)](https://imgchr.com/i/k1pk7j)

可以输入以下命令，先清理缓存，然后本地部署调试
```
hexo clean
hexo s
```
命令输入完成，提示：**Hexo is running at http://localhost:4000/**，可以把网址复制到浏览器上，查看本地生成的博客搜索功能

---
## 搜索无效、一直loading的问题

根据以上配置出的搜索框有可能出现无法加载，搜索无效，动画一直loading的问题，如下图：

[![klzjzT.md.jpg](https://s2.ax1x.com/2019/01/30/klzjzT.md.jpg)](https://imgchr.com/i/klzjzT)

按F12可以查看请求命令的状态，状态码`200`表示请求成功。但是搜索动画还是一直在转。

---
## 解决方案
为了解决以上问题，也是花了很多时间在寻找办法，找个几个办法，终于解决了我的问题。

[国光的博客地址](https://www.sqlsec.com/2017/12/hexosearch.html)

[Linchao的博客地址](https://linchao1002.github.io/linchao1002.github.io/2019/01/23/Next%20%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0%E7%AB%99%E5%86%85%E6%90%9C%E7%B4%A2%E5%8A%9F%E8%83%BD/)


现给出比较详细的解决方法，如果搜索不成功，可能是以下原因之一

### 1、搜索插件没有配置好

配置就按照文章前面配置的步骤走就行了

### 2、文章中包含特殊字符，文件编码时出错
一般情况下，博客部署到网上想要进行本地调试，输入以下命令
```
hexo clean
hexo s
```

[![klzLiq.md.png](https://s2.ax1x.com/2019/01/30/klzLiq.md.png)](https://imgchr.com/i/klzLiq)

报错先不用管，命令输入完成，提示：**Hexo is running at http://localhost:4000/**。可以把网址复制到浏览器上，查看本地生成的博客，体验跟网站版的差不多，不出所料搜索框的动画还是会一直loading。
![klzxQU.png](https://s2.ax1x.com/2019/01/30/klzxQU.png)

现在就要检查`search.xml` 文件，复制以下网址到浏览器，查看`search.xml`文件内容，是否报错。
```
localhost:4000/search.xml
```
效果图如下：
[![klzzyF.md.png](https://s2.ax1x.com/2019/01/30/klzzyF.md.png)](https://imgchr.com/i/klzzyF)

可以看到，有报错，报错内容就是说`search.xml` 文件有一些不能读取的内容，因为xml文件是有特殊符号不能使用。如果报错，浏览器右侧滑条拉到底，看看是哪里的文章出现问题。

效果图如下：
[![klzOJ0.md.png](https://s2.ax1x.com/2019/01/30/klzOJ0.md.png)](https://imgchr.com/i/klzOJ0)

从最后的文字中找到`一些信息`，打开博客根目录下的`search.xml`文件

[![klzXWV.png](https://s2.ax1x.com/2019/01/30/klzXWV.png)](https://imgchr.com/i/klzXWV)

打开`search.xml`文件，找到包含那`一些信息`的那篇文章，最好是能开MarkDown在线编辑，也可以把有问题的`.md`文件拿出来，重新部署博客。

修改完成后，照平时那样部署博客就行。如果还有错，继续排查。
