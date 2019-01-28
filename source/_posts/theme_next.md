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
![http://upload-images.jianshu.io/upload_images/5308475-8e8340c7a0489bce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240](hexo)

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