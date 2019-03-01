---
title: Hexo博客cnzz网站访问量统计
date: 2018-03-08 10:59:59
tags: [Hexo, yilia, Next]
toc: true
---
cnzz网站访问量统计
<!--more-->

使用友盟第三方的统计插件，网址：`http://www.umeng.com/`
进入网站先注册账号然后根据下列图片进入添加站点。
![](https://img-blog.nos-eastchina1.126.net/blog_cnzz11.png)


![](https://img-blog.nos-eastchina1.126.net/blog_cnzz12.png)

![](https://img-blog.nos-eastchina1.126.net/blog_cnzz13.png)


添加站点，自己搭建的博客，需要统计访问量的网站(这里加入我的博客网站)，然后点击统计代码进入代码页



![](https://img-blog.nos-eastchina1.126.net/blog_cnzz14.png)


代码页有很多样式，我的是红框的演示，纯文字统计，简洁大方，选择其他样式也可以

![](https://img-blog.nos-eastchina1.126.net/blog_cnzz15.png)
选择样式，复制样式代码到`..\themes\yilia\layout\_partial`下的
`footer.ejs`中加入如下代码块`<div>`和`</div>`即可


![](https://img-blog.nos-eastchina1.126.net/blog_cnzz16.png)


```
<div>
    里面是从CNZZ复制的代码
  </div>
```
代码块`<div>`和`</div>`一定要在`<footer>`和`</fotter>`之间


