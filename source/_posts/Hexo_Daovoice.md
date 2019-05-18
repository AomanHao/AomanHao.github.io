---
title: Hexo博客Next主题DaoVoice实现在线联系
date: 2019-05-03 10:59:59
tags: [Hexo, GitHub]
toc: true
---

Hexo博客Next主题DaoVoice实现在线联系
<!--more-->
## 注册登录DaoVoice
注册登录地址如下:
http://www.daovoice.io/

官网进行注册,需要邀请码: b6dbddb6 复制粘贴就可以了~!
或者通过下面链接进入：

复制粘贴代码
修改的`hexo`的文件路劲如下: `博客/themes/next/layout/_partials/head/head.swig` 添加下面的代码:

```
{% if theme.daovoice %}
 <script>(function(i,s,o,g,r,a,m){i["DaoVoiceObject"]=r;i[r]=i[r]||function(){(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;a.charset="utf-8";m.parentNode.insertBefore(a,m)})(window,document,"script",('https:' == document.location.protocol ? 'https:' : 'http:') + "//widget.daovoice.io/widget/b6dbddb6.js","daovoice")
 daovoice('init', {
  app_id: "你获取的appid"
});
daovoice('update');
 </script>
{% endif %}

```
1

## 修改主题配置文件
在Next主题的配置文件`博客/themes/next/_config.yml`末尾中添加用户ID:
```
daovoice: true
daovoice_app_id: 我们注册获取的id

```

## 修改聊天图标等设置
应用设置--聊天设置，然后定制欢迎辞，设置聊天窗口样式等
2
## 部署Daovoice
清理缓存，生成缓存，部署服务
```
hexo clean && hexo g && hexo s
```
登陆本地服务：`http://localhost:4000/`，可以看到Daovoice已经成功运行。

3
DaoVoice官网会提示，服务接入成功
4

![](https://img-blog.nos-eastchina1.126.net/blog/Hexo_Daovoice1.png)
![](https://img-blog.nos-eastchina1.126.net/blog/Hexo_Daovoice2.png)
![](https://img-blog.nos-eastchina1.126.net/blog/Hexo_Daovoice3.png)
![](https://img-blog.nos-eastchina1.126.net/blog/Hexo_Daovoice4.png)

