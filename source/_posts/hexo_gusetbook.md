---
title: hexo博客Next主题留言板
date: 2020-03-25 21:39:40
tags: [Hexo, Next]
mathjax: true
---

hexo博客Next主题留言板

<!--more-->

留言让博客看起来更加的人性化
NexT 主题官网有给出添加标签页、分类页的方法，其实添加留言本的方式异曲同工。方式稍微会有一点不同。
### 一、添加留言本 page
进入到博客的根目录，运行命令：
```
hexo new page guestbook
```
生成`index.md`，在里面可以写一些留言板介绍内容等
```
博客根目录\source\guestbook\index.md
```
### 二、修改菜单目录
Next主题默认只有主页和和关于，如果要增加菜单，在themes/next/_config.yml中修改配置，
```
# ---------------------------------------------------------------
# Menu Settings
# ---------------------------------------------------------------
menu:
  home: / || home
  about: /about/ || user
  tags: /tags/ || tags #标签
  categories: /categories/ || th #分类
  archives: /archives/ || archive #归档
  guestbook: /guestbook/ || comment #留言
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat
```
其中留言页需要自己增加：
```
guestbook: /guestbook/ || comment #留言
```

### 效果预览

本地预览
```
hexo clean && hexo g && hexo s 
```

### 博客部署

博客部署
```
hexo clean && hexo g && hexo d 
```
推荐使用 `&&` 作为组合命令的串联符号

注：一定要严格清理缓存，这样不容易出现问题，即需要执行`hexo clean`

---

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


