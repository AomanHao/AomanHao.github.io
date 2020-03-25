---
title: hexo博客Next主题留言板
date: 2020-03-25 21:39:40
tags: [Hexo，Next]
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

















### 二、留言本页面中添加多说访客代码
上一步中使用 `hexo` 命令新建了一个 `page`，进入到博客的`source`目录，里面会多了一个`gusetbook`文件夹，里面有一个`index.md`文件，打开该文件编辑：

<divclass="ds-recent-visitors"data-num-items="28"data-avatar-size="42"id="ds-recent-visitors">div>
这段代码加到index.md底部就行。
然后要登录自己多说的站点，进入设置->自定义CSS，添加：
#ds-reset .ds-avatar img,#ds-recent-visitors .ds-avatar img{width: 54px;height: 54px;/*設置圖像的長和寬，這裏要根據自己的評論框情況更改*/border-radius: 27px;/*設置圖像圓角效果,在這裏我直接設置了超過width/2的像素，即為圓形了*/-webkit-border-radius: 27px;/*圓角效果：兼容webkit瀏覽器*/-moz-border-radius: 27px;box-shadow: inset 0 -1px 0 #3333sf;/*設置圖像陰影效果*/-webkit-box-shadow: inset 0 -1px 0 #3333sf;}#ds-recent-visitors .ds-avatar{float: left}/*隱藏多說底部版權*/#ds-thread #ds-reset .ds-powered-by{display: none;}
三、菜单设置中添加留言本
找到NexT主题设置的_config.yml文件里面的menu项
menu:home: /  #about: /aboutarchives: /archives  tags: /tags  categories: /categories  guestbook: /guestbook
四、添加多语言文件的值
因为这里使用的是中文，找到languages文件夹里面的zh-Hans.yml文件，menu子项中添加留言：
menu:home: 首页  archives: 归档  categories: 分类  tags: 标签  about: 关于  search: 搜索  commonweal: 公益404  guestbook: 留言
附上个人博客对应博文地址：
http://lancelot_lewis.coding.me/2016/05/11/blog/hexo-guestbook/