---
title: Typecho左右侧广告区域展示恋爱线时间
date: 2021-02-14 10:08:00
tags: [Typecho]
---
 
Typecho左右侧广告区域展示恋爱线时间
<!--more-->

该教程适用typecho动态博客框架，handsome主题，展示恋爱线时间，效果立于博客网页左侧右侧等区域，展示如下：
![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_Typecholoveline.jpg)

## 教程
typecho动态博客框架，handsome主题下，将下面代码粘贴到后台设置`主题-开发者设置-自定义 JavaScript`

```
<!--恋爱记时-->
function lovexhjSitetime() {
                window.setTimeout("lovexhjSitetime()", 1000);
                var seconds = 1000
                var minutes = seconds * 60
                var hours = minutes * 60
                var days = hours * 24
                var years = days * 365
                var today = new Date()
                var todayYear = today.getFullYear()
                var todayMonth = today.getMonth()+1
                var todayDate = today.getDate()
                var todayHour = today.getHours()
                var todayMinute = today.getMinutes()
                var todaySecond = today.getSeconds()
                // 时间设置
                var t1 = Date.UTC(2020, 04, 15, 15, 15, 00)
                var t2 = Date.UTC(todayYear, todayMonth, todayDate, todayHour, todayMinute, todaySecond)
                var diff = t2 - t1
                var diffYears = Math.floor(diff / years)
                var diffDays = Math.floor((diff / days) diffYears * 365)
                var diffHours = Math.floor((diff - (diffYears * 365 + diffDays) * days) / hours)
                var diffMinutes = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours) / minutes)
                var diffSeconds = Math.floor((diff - (diffYears * 365 + diffDays) * days - diffHours * hours -
                    diffMinutes * minutes) / seconds)
                document.getElementById("lovexhjSitetime").innerHTML = "我们相恋了" + diffYears + "年" + diffDays + "天" +
                    diffHours + "小时" + diffMinutes + "分钟" + diffSeconds + "秒啦"
            }
            lovexhjSitetime()
```

时间留言都可以自行设置
## 代码位置
以下代码粘贴到全局右侧广告位即可

```
<aside class="widget_text sidebar-widget widget_custom_html fadeInUp">
<div class="textwidget custom-html-widget">
<div id="lovexhj" style="width: 100%; height: 100px; text-align: center; font-size: 1rem;">         
<div id="lovexhjImage" style="width: 220px; margin: 0 auto;">
<!-- 左边的头像 -->
<img src="https://cdn.jsdelivr.net/gh/L-20021213/picture@latest/2020/09/18/ce811c68ff1b4eb9a5b6d2a784d07c31.png" alt="love" style="width: 60px; border-radius: 50%;">
<!-- 中间的图片 -->
<img src="https://cdn.jsdelivr.net/gh/L-20021213/picture@latest/2020/09/18/lovelogo%20.gif" alt="love" style="width: 60px; border-radius: 50%;">
<!-- 右边的头像 -->
<img src="https://cdn.jsdelivr.net/gh/L-20021213/picture@latest/2020/09/18/3db15cc33adda3afcdbc62e18fc8403f.png" alt="love" style="width: 60px; border-radius: 50%;">
</div>
<p id="lovexhjSitetime" style="font-size: 0.8rem;    margin-top: 16px;  background: linear-gradient(to right, red, blue);-webkit-background-clip: text;color: transparent;">我们相恋了104天14小时47分钟19秒啦</p>  </div>
</div>
</aside>
```
## 展示标题
侧边广告栏展示名字在云空间的`usr/themes/handsome/component/sidebar.php`文件中修改。


[参考文章](https://sianx.com/archives/371.html)

### [我的个人博客主页，欢迎访问](https://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)s