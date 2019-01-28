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

```$ npm install gulp -g```

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
!(http://upload-images.jianshu.io/upload_images/5308475-8e8340c7a0489bce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)[hexo]

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

### 加入valine在线评论
设置效果：

设置方法：
首先要先去LeanCloud注册一个帐号.然后再创建一个应用.