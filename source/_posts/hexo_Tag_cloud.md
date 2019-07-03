---
title: Hexo博客建立标签云及效果展示
date: 2019-04-20 10:59:59
tags: [Hexo, Next]
toc: true
---

Hexo博客建立标签云及效果展示

<!--more-->

## `hexo-tag-cloud`插件介绍
`hexo-tag-cloud`插件是作者写的一个Hexo博客的标签云插件，旨在直观的展示标签的种类，美观大方且非常优雅。

插件地址：
[插件的GitHub地址](https://github.com/MikeCoder/hexo-tag-cloud)

插件说明：
[说明地址](https://github.com/MikeCoder/hexo-tag-cloud/blob/master/README.ZH.md)


标签云效果展示：
[我的博客主页](http://www.aomanhao.top/)

[插件作者提供的效果预览](https://mikecoder.github.io/archives/)

## 安装插件

进入到 `hexo` 的根目录，在 `package.json` 中添加依赖: `"hexo-tag-cloud": "2.0.*"` 操作如下：

### 使用命令行进行安装 
```
npm install hexo-tag-cloud@^2.0.* --save 
```
### Git clone 下载
使用命令行安装插件包的过程中可能会出现问题，安装失败，安装不完全。可以直接克隆插件到博客的插件文件夹`blog/node_modules`里。或者克隆到桌面，复制到博客的插件文件夹`blog/node_modules`里。
![](https://img-blog.nos-eastchina1.126.net/blog/hexo_tag_cloud2.jpg)

```
git clone https://github.com/MikeCoder/hexo-tag-cloud
```

## 配置插件
插件的配置需要对应的环境，可以在主题文件夹里找一下，有没有对应的渲染文件，然后根据渲染文件的类型，选择对应的插件配置方法。

### swig 用户 (Next主题在列)
在主题文件夹找到文件 `theme/next/layout/_macro/sidebar.swig`, 然后添加如下代码：
```
{% if site.tags.length > 1 %}
<script type="text/javascript" charset="utf-8" src="/js/tagcloud.js"></script>
<script type="text/javascript" charset="utf-8" src="/js/tagcanvas.js"></script>
<div class="widget-wrap">
    <h3 class="widget-title">Tag Cloud</h3>
    <div id="myCanvasContainer" class="widget tagcloud">
        <canvas width="250" height="250" id="resCanvas" style="width=100%">
            {{ list_tags() }}
        </canvas>
    </div>
</div>
{% endif %}
```
代码添加到后面即可，添加示意图如下:
![](https://img-blog.nos-eastchina1.126.net/blog/hexo_tag_cloud_code.jpg)



### 对于`ejs`的用户 (默认主题landscape在列)
在主题文件夹找到文件` hexo/themes/landscape/layout/_widget/tagcloud.ejs`,将这个文件修改如下：
```
<% if (site.tags.length) { %>
    <script type="text/javascript" charset="utf-8" src="/js/tagcloud.js"></script>
    <script type="text/javascript" charset="utf-8" src="/js/tagcanvas.js"></script>
    <div class="widget-wrap">
        <h3 class="widget-title">Tag Cloud</h3>
        <div id="myCanvasContainer" class="widget tagcloud">
            <canvas width="250" height="250" id="resCanvas" style="width=100%">
                <%- tagcloud() %>
            </canvas>
        </div>
    </div>
<% } %>
```

### 对于`jade`用户 (Apollo主题在列)
找到 apollo/layout/archive.jade 文件，并且把 container 代码块修改为如下内容:
```
block container
    include mixins/post
    .archive
        h2(class='archive-year')= 'Tag Cloud'
        script(type='text/javascript', charset='utf-8', src='/oj-code/js/tagcloud.js')
        script(type='text/javascript', charset='utf-8', src='/oj-code/js/tagcanvas.js')
        #myCanvasContainer.widget.tagcloud(align='center')
            canvas#resCanvas(width='500', height='500', style='width=100%')
                !=tagcloud()
            !=tagcloud()
    +postList()
```

## 主题配置

在博客根目录，找到 `_config.yml`配置文件然后在最后添加如下的配置项，可以自定义标签云的字体和颜色，还有突出高亮:
```
# hexo-tag-cloud
tag_cloud:
    textFont: Trebuchet MS, Helvetica
    textColor: '#333'
    textHeight: 25
    outlineColor: '#E2E1D1'
    maxSpeed: 0.1 
```
textColor: '#333'   字体颜色
textHeight: 25      字体高度，根据部署的效果调整
maxSpeed: 0.1       文字滚动速度，根据自己喜好调整

## 效果预览

本地预览
```
hexo clean && hexo g && hexo s 
```

## 博客部署

本地预览
```
hexo clean && hexo g && hexo d 
```
推荐使用 `&&` 作为组合命令的串联符号

注：一定要严格清理缓存，这样不容易出现问题，即需要执行`hexo clean`

---


[参考文章1](https://github.com/MikeCoder/hexo-tag-cloud/blob/master/README.ZH.md)

[参考文章2](https://blog.csdn.net/DreamHome_S/article/details/78250692)