---
title: Hexo主题Next配置及加载优化
date: 2019-02-25 11:55:00
tags: [GitHub, Hexo, Next]
---


Hexo主题Next配置及加载优化

<!--more-->

## 主题源加载优化
把在NexT主题的_config.yml里面的：
```
# Uri of fonts host. E.g. //fonts.googleapis.com (Default)
host:
```
改为：
```
# Uri of fonts host. E.g. //fonts.googleapis.com (Default)
host: //fonts.lug.ustc.edu.cn
```
因为`fonts.lug.ustc.edu.cn`是中科大的源，相比之前能快一下

---
## 博客双线部署

(参考文章地址)[https://www.ieclipse.cn/2016/08/29/Web/Hexo-deploy-lines/]

---
## 压缩网页静态资源
(参考文章地址)[https://blog.csdn.net/lewky_liu/article/details/82432003]
(hexo-neat插件github地址)[https://github.com/rozbo/hexo-neat]

常规的做法是使用`gulp`来进行压缩，每次压缩时还需要输入额外的命令，比较繁琐
### 配置hexo-neat压缩插件

#### 在站点根目录下安装hexo-neat
博客目录下运行
```
npm install hexo-neat --save
```

如果报错，选择克隆插件，然后手动复制到插件目录里面`hexo目录\node_modules\`
```
git clone https://github.com/rozbo/hexo-neat
```

#### 站点配置文件添加相关配置
配置信息添加到博客目录文件夹下的`hexo目录\_config.yml`的末尾，可以安装自己的需求去自定义配置
```
# hexo-neat
# 博文压缩
neat_enable: true
# 压缩html
neat_html:
  enable: true
  exclude:
# 压缩css  
neat_css:
  enable: true
  exclude:
    - '**/*.min.css'
# 压缩js
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '**/*.min.js'
    - '**/jquery.fancybox.pack.js'
    - '**/index.js'  
```
#### 报错及相应解决
(原文链接)[https://blog.csdn.net/dataiyangu/article/details/84963491 ]

#### 1、跳过压缩文件的正确配置方式
如果按照官方插件的文档说明来配置exclude，你会发现完全不起作用。这是因为配置的文件路径不对，压缩时找不到你配置的文件，自然也就无法跳过了。你需要给这些文件指定正确的路径，万能的配置方式如下：
neat_css:
enable: true
exclude:
- ‘**/*.min.css’

压缩html时不要跳过.md文件
.md文件就是我们写文章时的markdown文件，如果跳过压缩.md文件，而你又刚好在文章中使用到了NexT自带的tab标签，那么当hexo在生成静态页面时就会发生解析错误。这会导致使用到了tab标签的页面生成失败而无法访问。

压缩html时不要跳过.swig文件
.swig文件是模板引擎文件，简单的说hexo可以通过这些文件来生成对应的页面。如果跳过这些文件，那么你将会发现，你的所有页面完全没有起到压缩的效果，页面源代码里依然存在着一大堆空白。

点击的桃心效果消失
```
# 压缩js
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '**/*.min.js'
    - '**/jquery.fancybox.pack.js'
    - '**/index.js'  
    - '**/love.js'
```

gitalk js文件报错
在上面的代码底部加入如下代码
```
    - '**/comments.gitalk.js'
```

jquery pjax min js报错
我这里的 jquery pjax min js是指的加入pjax前需要以来的两个cdn文件，一个是jq，一个是它，我将它下载到了本地，不要在意这些细节~
同样加入如下代码
```
    - '**/jquery_pjax_min_js.js'
```


---

### lazyload 图片懒加载
Hexo 博客虽然功能很强大，但也越来越繁重了，访问速度上有了一些问题，这里我也考虑了许多，例如加 cdn，将国外的资源引用改为国内镜像等方式。今天又想到如果一个页面的图片很多，那么如何来提高博客的访问速度呢？。

经过一番寻找之后，找到一个方案，就是懒加载，通俗点讲就是当你翻到图片的时候再加载那张图片，而不是以下将本页面的所有图片都加载完。

配置
配置过程也很简单，就是一个 npm 模块。
在你的 Hexo 目录下，执行以下命令：

npm install hexo-lazyload --save
然后在你的 Hexo 目录的配置文件 _config.yml 中添加配置:

lazyload:
  enable: true
  # className: #可选 e.g. .J-lazyload-img
  # loadingImg: #可选 eg. ./images/loading.png
loadingImg - 图片未加载时的代替图

默认路径: ‘/js/lazyload-plugin/loading.svg’
如果需要自定义，添填入 loading 图片地址，如果是本地图片，不要忘记把图片添加到你的主题目录下。
className - 需要延迟加载的图片 class 选择器

默认会延迟加载文章中的所有图片。
如果不为空，请填入需要延迟加载的图片 class 选择器