---
title: Hexo博客添加背景音乐和音乐歌单(举例网易云音乐)
date: 2018-03-08 10:59:59
tags: [Hexo, yilia, Music]
---
## 添加背景音乐
<!--more-->

### 1、 打开网易云音乐首页，然后搜索你要添加的背景音乐

		http://music.163.com/

![](http://p3qhnc0eg.bkt.clouddn.com/%E7%BD%91%E6%98%93%E4%BA%91_%E5%A4%96%E9%93%BE%E6%AD%8C%E6%9B%B2.png)

### 2、 搜索到歌曲点击生成外链播放器，进去下一个界面

![](http://p3qhnc0eg.bkt.clouddn.com/%E7%BD%91%E6%98%93%E4%BA%91_%E5%A4%96%E9%93%BE2.png)

### 3、 复制外链播放器的代码
打开yilia主题下的_partial文件夹下的left-col.ejs文件
		复制文件内容到最下端

![](http://p3qhnc0eg.bkt.clouddn.com/TIM%E6%88%AA%E5%9B%BE20180308212600.png)

红线内的iframe框为复制的外链播放器代码，如图红线内，把代码放在div框
		例如：

    <div style="position:absolute; bottom:120px left:auto; width:85%">
		<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=260 height=86 src="//music.163.com/outchain/player?type=2&id=422428548&auto=1&height=66"></iframe>
		</div>

这样就可以了

注：调节播放器大小，改变外链播放器的代码块，长度宽度即可
		width=260 height=86
