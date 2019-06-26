---
title: Valine评论插件因为LeanCloud国内域名解析问题无法正常使用的解决方法
date: 2019-06-23 19:55:00
tags: [GitHub]
---


Valine评论插件无法正常使用的解决方法

<!--more-->

近日，LeanCloud 国内域名解析存在问题，valine评论插件的评论内容都储存在LeanCloud，使用valine评论插件的个人博客的评论及阅读数会显示失败。


关于 LeanCloud 国内域名解析问题的情况更新（6 月 21 日)
[声明地址](https://blog.avoscloud.com/6841)

Valine评论插件的GitHub，关于此问题的issues区
[issues地址](https://github.com/xCss/Valine/issues/188)


因为LeanCloud域名解析出现问题，其提供的资源也无法指向，有小伙伴分享了新的资源连接，然后替换掉即可。

替换资源的文件路径`blog路径/theme/next/_config.yml`，编辑`_config.yml`，替换如下
```
# valine
  # See: https://github.com/xCss/Valine
  # Example:
leancloud: http://pirogue.org/js/av-min.js
```
替换效果如下:
![](https://img-blog.nos-eastchina1.126.net/blog/leancloud_link.jpg)

然后平常一样部署博客就可以

---
感谢提供资源的小伙伴，[他的门户](http://pirogue.org)