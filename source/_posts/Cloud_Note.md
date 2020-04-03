---
title: Chrome浏览器，有道云笔记的网页剪报需要多次登录且收藏失败报错
date: 2020-04-03 10:59:59
tags: [Chrome]
toc: true
---

Chrome浏览器，有道云笔记的网页剪报需要多次登录且收藏失败报错

<!--more-->

报错代码
```
{"canTryAgain":false,"scope":"SECURITY","error":"207","message":"Message[AUT
```


客服给出的方案，经测试有效
>新版的chrome浏览器，地址栏输入：


```
chrome://flags/#same-site-by-default-cookies
```
选择disabled，禁用此项，按下列图操作


![](https://imgconvert.csdnimg.cn/aHR0cDovL3RpZWJhcGljLmJhaWR1LmNvbS9mb3J1bS93JTNENTgwL3NpZ249ZGM5NGJjYTU4NzUyOTgyMjA1MzMzOWNiZTdjYjdiM2IvZmM4NTg2MGU3YmVjNTRlN2FjNjY5YTdjYWUzODliNTA0ZWMyNmEwMS5qcGc?x-oss-process=image/format,png)

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)

