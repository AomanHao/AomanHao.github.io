---
title: Hexo博客Next主题bilibili视频Markdown引入文章
date: 2020-04-12 18:44:45
tags: [Hexo, Next]
---


Hexo博客Next主题bilibili视频Markdown引入文章
<!--more-->

## 问题及需求
B站视频无广告有弹幕，非常简洁，经常看B站视频，在文章引用B站的视频
![](https://cdn.jsdelivr.net/gh/hongcyu/image/images/20200307095024.png)

在不用插件的情况下用官方的iframe方式引入视频，默认的方式导入视频屏幕会很小

![](https://img-blog.nos-eastchina1.126.net/blog/blog_bilibili_1.png)

一般我们都是自己改width和height来修改大小，但是换成不同的设备就无法正常的显示了

## 视频大小优化
不能自动适配，试试下面的两种办法：`Next`版本`6.XX`可以，`7.xx`版本可以试试
### 优化方法一
div标签自适应与屏幕的大小，iframe以100%顶边撑开。

以next主题为例子：在`next\source\css\_custom\custom.styl`下底部添加以下css代码：
```

/*哔哩哔哩视频适配*/

.bilibili {
    position: relative;
    width: 100%;
}
@media only screen and (max-width: 767px) {
    .bilibili {height: 15em;max-width: 25em;}
}
@media only screen and (min-width: 768px) and (max-width: 991px) {
    .bilibili {height: 20em;max-width: 30em;}
}
@media only screen and (min-width: 992px) and (max-width: 1199px) {
    .bilibili {height: 30em;max-width: 40em;}
}
@media only screen and (min-width: 1200px) {
    .bilibili {height: 40em;max-width: 50em;}
}
```

插入视频时，加入标签块
```
<div class="bilibili">

</div>
```

写成如下形式即可：
```
<div class="bilibili">
    <iframe src="//player.bilibili.com/player.html?aid=14875394&cid=24237231&page=1&high_quality=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>
```

### 优化方法二
使用`@media`属性，对不同屏幕大小的设备，设置宽度和高度。
`@media`可以查询到设备的一下属性
>设备屏幕的高度
设备的方向（如移动设备横屏）
可视窗口的宽高
屏幕解析度

在`next\source\css\_custom\custom.styl`下底部添加以下css代码：
```

/*哔哩哔哩视频适配*/

.bilibili {
    position: relative;
    width: 100%;
}
@media only screen and (max-width: 767px) {
    .bilibili {height: 15em;max-width: 25em;}
}
@media only screen and (min-width: 768px) and (max-width: 991px) {
    .bilibili {height: 20em;max-width: 30em;}
}
@media only screen and (min-width: 992px) and (max-width: 1199px) {
    .bilibili {height: 30em;max-width: 40em;}
}
@media only screen and (min-width: 1200px) {
    .bilibili {height: 40em;max-width: 50em;}
}
```

插入视频时，加入标签块`class="bilibili"`到B站的iframe代码:

```
<iframe class="bilibili" src="//player.bilibili.com/player.html?aid=14875394&cid=24237231&page=1&high_quality=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
```
效果如下：
<iframe class="bilibili" src="//player.bilibili.com/player.html?aid=14875394&cid=24237231&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>

## 链接相关参数
B站链接的参数
```
player.bilibili.com/player.html?aid=81148317&cid=138878361&page=1
```

### 参数说明及举例使用
```
aid 视频ID 就是B站的av号
cid 应该是客户端的id,clientid的缩写（推测） 测试表示不填也不会有什么问题
page 第几个视频 也就是分P的 默认是1
as_wide 是否宽屏 1：宽屏 0：小屏
high_quality 视频质量 1：最高视频质量 0：最低视频质量
danmaku 是否开启弹幕 1：开启（默认） 0：关闭
```
举个例子：
B站默认视频质量是最低的，可以通过在`src`链接后面添加`&high_quality=1`来设置

```
src="//player.bilibili.com/player.html?aid=14875394&cid=24237231&page=1

改为
src="//player.bilibili.com/player.html?aid=14875394&cid=24237231&page=1&high_quality=1
```


[参考文章1](https://www.phenxso.com/archives/87.html)
[参考文章2](https://hongcyu.cn/posts/hexo-bilibili.html)

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


