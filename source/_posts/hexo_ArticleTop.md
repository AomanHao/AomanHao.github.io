---
title: Hexo博客Next主题文章置顶相关
date: 2019-11-23 21:44:45
tags: [Hexo, Next, GitHub]
---

Hexo博客Next主题文章置顶相关
<!--more-->
我需要写一些文章做推荐相关，需要文章置顶功能
[博客效果](http://www.aomanhao.top/)
## 置顶方法配置
### 一、修改库文件

#### 原理
在Hexo生成首页HTML时，将top值高的文章排在前面，达到置顶功能。
#### 修改方法
修改`Hexo`文件夹下的`node_modules/hexo-generator-index/lib/generator.js`，在生成文章之前进行文章top值排序。

需添加的代码：
```
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
```
其中涉及Javascript的比较函数：
```
cmp(var a, var b) {
    return  a - b; // 升序，降序的话就 b - a
}
```
修改完成后，只需要在front-matter中设置需要置顶文章的top值，将会根据top值大小来选择置顶顺序top值越大越靠前。需要注意的是，这个文件不是主题的一部分，也不是Git管理的，备份的时候比较容易忽略。
#### 修改内容
以下是最终的`generator.js`内容，可以直接复制替换`node_modules/hexo-generator-index/lib/generator.js`的内容
```
'use strict';

var pagination = require('hexo-pagination');

module.exports = function(locals) {
  var config = this.config;
  var posts = locals.posts.sort(config.index_generator.order_by);

  posts.data = posts.data.sort(function(a, b) {
      if(a.top && b.top) {
          if(a.top == b.top) return b.date - a.date;
          else return b.top - a.top;
      }
      else if(a.top && !b.top) {
          return -1;
      }
      else if(!a.top && b.top) {
          return 1;
      }
      else return b.date - a.date;
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


### 二、插件配置
```
$ npm uninstall hexo-generator-index --save
$ npm install hexo-generator-index-pin-top --save
```
## 置顶文章配置
然后在需要置顶的文章的Front-matter中加上`top: true`或者top数字`top: 1`：

```
title: 置顶
date: 2019-09-09 09:09:09
top: true
top: 1
```
按照数字大小依次往下置顶排序
## 置顶标志
置顶的文章会显示在主页最上面，没有明确的置顶标志，我们需要键入置顶标志。

### 设置置顶标志
打开：`/blog/themes/next/layout/_macro`目录下的`post.swig`文件，定位到`<div class="post-meta">`标签下，插入如下代码：
```
          {% if post.top %}
            <i class="fa fa-thumb-tack"></i>
            <font color=7D26CD>置顶</font>
            <span class="post-meta-divider">|</span>
          {% endif %}
```

效果展示： 
```
        <div class="post-meta">
          <span class="post-time">
在此之下插入代码，包含在 span块内        
          {% if post.top %}
            <i class="fa fa-thumb-tack"></i>
            <font color=7D26CD>置顶</font>
            <span class="post-meta-divider">|</span>
          {% endif %}
```
---

[参考文章1](https://www.jianshu.com/p/42a4efcdf8d7)
[参考文章2](https://blog.csdn.net/qq_30930805/article/details/88890124)

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


