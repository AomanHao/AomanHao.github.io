---
title: 部署一言接口
date: 2021-01-03 10:08:00
tags: [Typecho]
---
 
部署一言接口
<!--more-->

## 开始部署
下载代码上传至你的网站目录，把解压出来的文件夹改名为hitokoto
然后访问https://域名及文件路径/hitokoto查看效果
示例：https://sunpma.com/other/hitokoto
主题一言接口修改方法：https://sunpma.com/670.html
下载路径：https://www.lanzous.com/i8a44ub
## 调用方法
### PHP调用方法
添加如下代码到页面头部
```
<?php $hitokoto = file_get_contents('https://sunpma.com/other/hitokoto/'); ?>
```
注意：
>需要把代码中的URL地址替换为你自己的URL
然后在需要显示“一言”的标签，插入如下代码：
```
<?php echo $hitokoto; ?>
```
### JS调用方法
添加如下代码到页面底部；
```
$.post("https://sunpma.com/other/hitokoto/", function(hitokoto) {
    $(".content").html(hitokoto);
});
```

注意
>需要把代码中的URL地址替换为你自己的URL
一言输出内容修改hitokoto.txt文件即可，一行一句
JS调用需要jquery.min.js一般主题都有，无需再引用
调用示例请看demo.php

## 其他一言接口服务
https://hitokoto.cn/api
https://api.ixiaowai.cn/api/ylapi.php
https://api.uixsj.cn/hitokoto/w.php
https://v1.jinrishici.com
Github：https://github.com/galnetwen/hitokoto


参考文章L:https://sunpma.com/669.html

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)