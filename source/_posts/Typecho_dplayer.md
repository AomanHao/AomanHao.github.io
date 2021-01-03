---
title: Typecho使用DPlayer视频播放插件
date: 2021-01-03 10:08:00
tags: [Typecho]
---
 
DPlayer-Typecho视频播放插件
<!--more-->


[插件下载](https://github.com/MoePlayer/DPlayer-Typecho)
该插件适用于自己上传道云端的视频，在博客文章里播放
## 使用方式
下载后将插件解压到/usr/plugins目录中并将文件夹名改为DPlayer，然后到后台中启用它即可。

### 默认不自动播放，弹幕开启
```
[dplayer url="http://xxx.com/xxx.mp4" pic="http://xxx.com/xxx.jpg"/]
```
### 关闭弹幕
```
[dplayer url="http://xxx.com/xxx.mp4" pic="http://xxx.com/xxx.jpg" danmu="false"/]
```
### 开启自动播放
```
[dplayer url="http://xxx.com/xxx.mp4" pic="http://xxx.com/xxx.jpg" autoplay="true"/]
```
### 添加额外弹幕源(例：bilibili弹幕)
```
[dplayer url="http://xxx.com/xxx.mp4" pic="http://xxx.com/xxx.jpg" autoplay="true" addition="https://api.prprpr.me/dplayer/bilibili?aid=7286894"/]
```

## 作者修复
### 1. Pjax页面切换？
重新加载播放器回调函数
```
loadDPlayer();
```


### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)