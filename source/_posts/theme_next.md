---
title: Hexo主题Next配置
date: 2019-01-20 11:55:00
tags: [GitHub, Hexo, Next]
---


Hexo主题Next配置

<!--more-->
### 新建404界面
在站点根目录下，输入`hexo new page 404`，在默认`Hexo站点下/source/404/index.md`
打开新建的404界面，编辑属于自己的404界面，可以显示腾讯公益404界面，代码如下：

```
<!DOCTYPE HTML>
<html>
<head>
  <meta http-equiv="content-type" content="text/html;charset=utf-8;"/>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="robots" content="all" />
  <meta name="robots" content="index,follow"/>
  <link rel="stylesheet" type="text/css" href="https://qzone.qq.com/gy/404/style/404style.css">
</head>
<body>
  <script type="text/plain" src="http://www.qq.com/404/search_children.js"
          charset="utf-8" homePageUrl="/"
          homePageName="回到我的主页">
  </script>
  <script src="https://qzone.qq.com/gy/404/data.js" charset="utf-8"></script>
  <script src="https://qzone.qq.com/gy/404/page.js" charset="utf-8"></script>
</body>
</html>
```

### 静态资源压缩

静态资源压缩

在站点目录下安装插件：

```
$ npm install gulp -g
```

```
npm install gulp-minify-css --save
npm install gulp-uglify --save
npm install gulp-htmlmin --save
npm install gulp-htmlclean --save
npm install gulp-imagemin --save
```

在Hexo站点下添加`gulpfile.js`文件，文件内容如下：
```
var gulp = require('gulp');
var minifycss = require('gulp-minify-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
var imagemin = require('gulp-imagemin');
// 压缩css文件
gulp.task('minify-css', function() {
  return gulp.src('./public/**/*.css')
  .pipe(minifycss())
  .pipe(gulp.dest('./public'));
});
// 压缩html文件
gulp.task('minify-html', function() {
  return gulp.src('./public/**/*.html')
  .pipe(htmlclean())
  .pipe(htmlmin({
    removeComments: true,
    minifyJS: true,
    minifyCSS: true,
    minifyURLs: true,
  }))
  .pipe(gulp.dest('./public'))
});
// 压缩js文件
gulp.task('minify-js', function() {
    return gulp.src(['./public/**/.js','!./public/js/**/*min.js'])
        .pipe(uglify())
        .pipe(gulp.dest('./public'));
});
// 压缩 public/demo 目录内图片
gulp.task('minify-images', function() {
    gulp.src('./public/demo/**/*.*')
        .pipe(imagemin({
           optimizationLevel: 5, //类型：Number  默认：3  取值范围：0-7（优化等级）
           progressive: true, //类型：Boolean 默认：false 无损压缩jpg图片
           interlaced: false, //类型：Boolean 默认：false 隔行扫描gif进行渲染
           multipass: false, //类型：Boolean 默认：false 多次优化svg直到完全优化
        }))
        .pipe(gulp.dest('./public/uploads'));
});
// 默认任务
gulp.task('default', [
  'minify-html','minify-css','minify-js','minify-images'
]);
```
需要只在每次执行generate命令后执行gulp就可以实现对静态资源的压缩，完成压缩后执行deploy命令同步到服务器：

```
hexo g
gulp
hexo d

```

---

### 隐藏网页底部powered By Hexo / 强力驱动
打开`themes/next/layout/_partials/footer.swig`,使用`<!--`与`-->`隐藏之间的代码即可，或者直接删除。位置如图：
![hexo](http://upload-images.jianshu.io/upload_images/5308475-8e8340c7a0489bce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
### 各版块透明度修改
#### 内容板块透明
根博客目录`themes\next\source\css\_schemes\Pisces\_layout.styl`文件`.content-wrap`标签下`background: white`修改为：
```
background: rgba(255,255,255,0.7); //0.7是透明度
```
#### 菜单栏背景
根博客目录`themes\next\source\css\_schemes\Pisces\_layout.styl`文件`.header-inner`标签下`background: white`修改为：
```
background: rgba(255,255,255,0.7); //0.7是透明度
```
#### 站点概况背景
根博客目录`themes\next\source\css\_schemes\Pisces\_sidebar.styl`文件`.sidebar-inner`标签下`background: white`修改为：
```
background: rgba(255,255,255,0.7); //0.7是透明度
```

修改然后根博客目录`themes\next\source\css\_schemes\Pisces\_layout.styl`文件`.sidebar`标签下`background: $body-bg-color`修改为：
```
background: rgba(255,255,255,0.7); //0.7是透明度
```

---
### 网站底部字数统计

具体方法实现


切换到根目录下，然后运行如下代码
```
npm install hexo-wordcount --save
```

然后在`/themes/next/layout/_partials/footer.swig`文件尾部加上：
```
<div class="theme-info">
  <div class="powered-by"></div>
  <span class="post-count">博客全站共{{ totalcount(site) }}字</span>
</div>
```
---

### 添加侧栏推荐阅读

编辑主题配置文件，如下配置即可：
```
# Blog rolls
links_icon: link
links_title: 推荐阅读
#links_layout: block
links_layout: inline
links:
  Swift 4: https://developer.apple.com/swift/
  Objective-C: https://developer.apple.com/documentation/objectivec
```

---

### 博文置顶

修改`hexo-generator-index`插件，把`node_modules/hexo-generator-index/lib/generator.js`中代码替换为：
```
'use strict';
var pagination = require('hexo-pagination');
module.exports = function(locals){
  var config = this.config;
  var posts = locals.posts;
    posts.data = posts.data.sort(function(a, b) {
        if(a.top && b.top) { // 两篇文章top都有定义
            if(a.top == b.top) return b.date - a.date; // 若top值一样则按照文章日期降序排
            else return b.top - a.top; // 否则按照top值降序排
        }
        else if(a.top && !b.top) { // 以下是只有一篇文章top有定义，那么将有top的排在前面（这里用异或操作居然不行233）
            return -1;
        }
        else if(!a.top && b.top) {
            return 1;
        }
        else return b.date - a.date; // 都没定义按照文章日期降序排
    });
  var paginationDir = config.pagination_dir || 'page';
  return pagination('', posts, {
    perPage: config.index_generator.per_page,
    layout: ['index', 'archive'],
    format: paginationDir + '/%d/',
    data: {
      __index: true
    }
  });
};

```
文章添加Top值，值越大，越靠前：
```
---
title: Hexo-NexT主题配置
date: 2018-01-20 20:41:08
categories: Hexo
tags:
- Hexo
- NexT
top: 100
---
```

---
### 网页底部信息隐藏
网页底默认最新一次使用，需要取消`since`注释，设定年份

```
footer:
  # Specify the date when the site was setup.
  # If not defined, current year will be used.
  since: 2017

  # Icon between year and copyright info.
  icon:
    # Icon name in fontawesome, see: https://fontawesome.com/v4.7.0/icons/
    # `heart` is recommended with animation in red (#ff0000).
    name: user #设置图标，想修改图标从https://fontawesome.com/v4.7.0/icons获取
    # If you want to animate the icon, set it to true.
    animated: false
    # Change the color of icon, using Hex Code.
    color: "#808080"

  # If not defined, `author` from Hexo main config will be used.
  copyright:  by AomanHao  #版权
  ```

---
### 显示文章阅读进度百分比
设置方法：
打开`themes/next/_config.yml`主题配置文件,找到`# Scroll percent label in b2t button`将`scrollpercent:`的值,改成`true`

```
# Scroll percent label in b2t button
  scrollpercent: true
```
---
### 浏览页面的时候显示当前浏览进度
如果想把top按钮放在侧边栏,打开`themes/next`下的`_config.yml`,搜索关键字`b2t`,把`false`改为`true`

```
# Back to top in sidebar
 b2t: true
    
 # Scroll percent label in b2t button
 scrollpercent: true
```
---

### 加入valine在线评论
设置效果：

设置方法：
首先要先去[LeanCloud](https://leancloud.cn/)注册一个帐号.然后再创建一个应用.

拿到`appid`和`appkey`之后，打开`themes/next/_config.yml`主题配置文件，查找`valine`，填入`appid `和 `appkey`
我的配置:

```
# You can get your appid and appkey from https://leancloud.cn
# More info available at https://valine.js.org
valine:
  enable: true # When enable is set to be true, leancloud_visitors is recommended to be closed for the re-initialization problem within different leancloud adk version.
  appid: 
  appkey: 
  notify: true # mail notifier, See: https://github.com/xCss/Valine/wiki
  verify: true # Verification code
  placeholder: 欢迎交流讨论... # comment box placeholder
  avatar: mm # gravatar style
  guest_info: nick,mail,link # custom comment header
  pageSize: 10 # pagination size
  visitor: false # leancloud-counter-security is not supported for now. When visitor is set to be true, appid and appkey are recommended to be the same as leancloud_visitors' for counter compatibility. Article reading statistic https://valine.js.org/visitor.html
  comment_count: true # if false, comment count will only be displayed in post page, not in home page

```

---
## Hexo添加阅读次数
`next` 集成了 `leancloud` 。可以在`leancloud`进行账号注册。
创建一个新的应用。点击应用进入。
创建名称为`Counter`的`Class`，名称必须为`Counter`

[![k1gdSK.md.png](https://s2.ax1x.com/2019/01/31/k1gdSK.md.png)](https://imgchr.com/i/k1gdSK)

点击设置 > 应用Key 复制App ID 和 App Key
[![k1gUW6.md.png](https://s2.ax1x.com/2019/01/31/k1gUW6.md.png)](https://imgchr.com/i/k1gUW6)

修改配置文件
在主题`themes`目录下有第三方提供的主题配置文件`\themes\next_config.yml`
打开主题配置文件 添加`app_id` 和`app_key`:
```
# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.文章热度
leancloud_visitors:
  enable: true
  app_id: 
  app_key: 
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: false
  betterPerformance: false
```
修改统计设置
打开主题配置文件 定位到 `post_wordcount`
```
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true
  min2read: true
  totalcount: false
  separated_meta: true
```
Web安全性
为了保证应用的统计计数功能仅应用于自己的博客，你可以在应用 > 设置 > 安全中心的Web安全域名中加入自己的博客域名，保证数据的调用安全。

[![k1gwQO.md.png](https://s2.ax1x.com/2019/01/31/k1gwQO.md.png)](https://imgchr.com/i/k1gwQO)

---


## 显示文章热度

首先要先去[LeanCloud](https://leancloud.cn/)注册一个帐号.然后再创建一个应用.

设置方法：
`next`主题集成`leanCloud`，打开`themes/next/layout/_macro/post.swig`,准备添加`℃`


```
          {# LeanCloud PageView #}
          {% if theme.leancloud_visitors.enable or (theme.valine.enable and theme.valine.appid and theme.valine.appkey and theme.valine.visitor) %}
            <span id="{{ url_for(post.path) }}" class="leancloud_visitors" data-flag-title="{{ post.title }}">
              <span class="post-meta-divider">|</span>
              <span class="post-meta-item-icon">
                <i class="fa fa-eye"></i>
              </span>
              {% if theme.post_meta.item_text %}
                <span class="post-meta-item-text">{{ __('post.views') + __('symbol.colon') }}</span>
              {% endif %}
                <span class="leancloud-visitors-count"></span>
              <span>℃</span>
            </span>
          {% endif %}
```
插入摄氏度到倒数第三句，如下：
```
<span>℃</span>
```

打开，`themes/next/languages/zh-CN.yml`,将`views`后的文字描述改为热度.
```
views: 热度
```
有的版本不一样，打开，`themes/next/languages/zh-Hans.yml`，将以下

```
visitors: 热度
```

然后打开`themes/next/_config.yml`找到`leancloud_visitors`,将`enable:`改成`true`,再填上自己`LeanCloud`的`app_id`和`app_key`。
```
# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.文章热度
leancloud_visitors:
  enable: true
  app_id: 你自己的id
  app_key: 你自己的key
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true
  betterPerformance: false
```

---
### 添加网站已运行时间

在`themes/layout/_parrials/footer.swing`后添加

```
<span id="timeDate">载入天数...</span><span id="times">载入时分秒...</span>
<script>
    var now = new Date(); 
    function createtime() { 
        var grt= new Date("11/27/2017 12:00:00");//在此处修改你的建站时间
        now.setTime(now.getTime()+250); 
        days = (now - grt ) / 1000 / 60 / 60 / 24; dnum = Math.floor(days); 
        hours = (now - grt ) / 1000 / 60 / 60 - (24 * dnum); hnum = Math.floor(hours); 
        if(String(hnum).length ==1 ){hnum = "0" + hnum;} minutes = (now - grt ) / 1000 /60 - (24 * 60 * dnum) - (60 * hnum); 
        mnum = Math.floor(minutes); if(String(mnum).length ==1 ){mnum = "0" + mnum;} 
        seconds = (now - grt ) / 1000 - (24 * 60 * 60 * dnum) - (60 * 60 * hnum) - (60 * mnum); 
        snum = Math.round(seconds); if(String(snum).length ==1 ){snum = "0" + snum;} 
        document.getElementById("timeDate").innerHTML = " Runing "+dnum+" D "; 
        document.getElementById("times").innerHTML = hnum + " H " + mnum + " M " + snum + " S"; 
    } 
setInterval("createtime()",250);
</script>

```

---

### 添加头像
打开`themes/next下的_config.yml`文件，搜索 `Avatar`关键字，修改url的参数
```
avatar:
  # in theme directory(source/images): /images/avatar.gif
  # in site  directory(source/uploads): /uploads/avatar.gif
  # You can also use other linking images.
  url: /images/avatar.gif
  # If true, the avatar would be dispalyed in circle.
  rounded: true
  # The value of opacity should be choose from 0 to 1 to set the opacity of the avatar.
  opacity: 1
  # If true, the avatar would be rotated with the cursor.
  rotated: false

```
url链接默认是`themes/next/source/images`下的`avatar.gif`文件,有两种方法修改连接

1、本地连接，不建议用比较大的图片（大于1M文件），加载图片需要时间
```
url: /images/avatar.gif

或者

url: /images/xx.jpg等类型图片
```
2、图床外链，建议使用
```
url: http://example.com/avatar.png
```

### 添加站内搜索
设置效果：

设置方法：
安装`hexo-generator-searchdb`插件
```
npm install hexo-generator-searchdb --save
```
编辑`_config.yml`站点配置文件，新增以下内容到任意位置：
```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
  ```
编辑`themes/next/_config.yml `主题配置文件，启用本地搜索功能,将`local_search:`下面的`enable:`的值，改成`true`

```
# Local search
local_search:
  enable: true
```

### 底部跳动图标实现
注意点：需要到`next\layout_partials下的footer.swig`文件中，在你所需要调动的图标所对应的span中增加对应的ID
去到主体的`css`文件（`next\source\css_variables\custom.styl `，增加以下代码即可

```
//底部爱心小图标跳动
keyframes heartAnimate {
    0%,100%{transform:scale(1);}
    10%,30%{transform:scale(0.9);}
    20%,40%,60%,80%{transform:scale(1.1);}
    50%,70%{transform:scale(1.1);}
}

//图标所对应的span中的ID
#heart {
    animation: heartAnimate 1.33s ease-in-out infinite;
}
.with-love {
    color: rgb(255, 113, 113);
}
```

## 实现统计功能

具体实现方法:在根目录下安装 `hexo-wordcount`,运行：
```
npm install hexo-wordcount --save
```
然后在主题的配置文件中，配置如下：
```
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true
  min2read: true
```