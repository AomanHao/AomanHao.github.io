---
title: Hexo博客添加相册
date: 2018-09-23 09:39:40
tags: [Hexo, Next]
toc: true
---


相册
<!--more-->

## 实现思路
1.在主页上必须有一个可供点击的相册连接
2.要用 `hexo` 生成一个`photos.html `文件
3.`photos.html `中的图片数据来源?因为这是一个静态页面所有要有一个 `json `文件
4.`json `文件中有含有信息,图片的文件名.
5.图片要有一个完整的路径,用`github`的空间
6.`Python`脚本剪裁、压缩、上传图片到自定义的`github`备份仓库中


## 操作步骤
### 1.在主页上必须有一个可供点击的连接
`BLOG\source`目录下创建一个`photos`目录，目的是存放利用脚本生成的`json `文件和渲染文件。

![](https://img-blog.nos-eastchina1.126.net/blog_photos_1.png)



配置 Yilia 主题让其显示出来.
`yourBlog/themes/yilia/_config.yml`文件
添加相册

```
  相册: /photos/
```
![](https://img-blog.nos-eastchina1.126.net/blog_head_photo1.png)


### 2.如何生成 photos.html 文件来

在`github`上新建一个仓库，主要用于存储图片，可以通过`url`访问到，也方便管理，备份图片和其他东西

![](https://img-blog.nos-eastchina1.126.net/blog_backup1.png)

`git clone` 到本地，模仿作者的文件目录结构

`source`文件夹是备份图片，`theme`是备份yilia配置文件等
![](https://img-blog.nos-eastchina1.126.net/blog_backup2.png)

`min_photos`是缩略图文件夹，`photos`是原图文件夹，`blog_photos_copy`是渲染文件备份，最后再弄
![](https://img-blog.nos-eastchina1.126.net/blog_backup3.png)

备份渲染文件，最后再弄
![](https://img-blog.nos-eastchina1.126.net/blog_backup4.png)


`ejs `文件是以后要`hexo` 渲染的文件.

`ins.js `文件设置自己的东西.

### 3.修改 ejs 模板文件

#### 3.1 index.ejs文件可以不用修改

#### 3.2 修改 ins.js 文件的 render()函数.这个函数是用来渲染数据的

修改图片的路径地址.`minSrc` 小图的路径. `src` 大图的路径.修改为自己的图片路径(github的路径).

```
  var minSrc = 'https://raw.githubusercontent.com/AomanHao/Blog-Back-Up/master/source/min_photos/' + data.link[i];
  var src = 'https://raw.githubusercontent.com/AomanHao/Blog-Back-Up/master/source/photos/' + data.link[i];
```

这个链接不是直接的图片url，是需要点“下载”才能看到的url。

github仓库上传的图片文件
![](https://img-blog.nos-eastchina1.126.net/blog_photos_git_1.png)

下载选项，看网址

![](https://img-blog.nos-eastchina1.126.net/blog_photos_git_2.png)


黄色画出了链接网址，路径地址.minSrc 小图的路径. src 大图的路径
![](https://img-blog.nos-eastchina1.126.net/blog_photos_git_3.png)


我的路径有`source/min_photos/`和`source/photos`，分别是缩略图（压缩的图快速加载预览）和原图（点击查看图片）



#### 3.3生成 json 文件.

这一步是关键的一步,也是最后一步.先用脚本把图片处理成一套大图和一套小图,
然后上传的七牛或者 github 上再回头生成这个 `json`文件.
每次更新图片都要执行脚本重新生成 `json `文件.这个`json `文件会出现在
`yourBlog/source/photos/data.json`

![](https://img-blog.nos-eastchina1.126.net/blog_photos_2.png)

### 4.处理图片
处理脚本试用python语言写的，运行环境也是python

python脚本文件原作者GitHub地址：`https://github.com/lawlite19/Blog-Back-Up`

下载python2或者3，在`cmd`运行窗口运行`python tool.py`

![](https://img-blog.nos-eastchina1.126.net/blog_python1.png)

`tool.py`是运行主函数，`ImageProcess`图像处理功能函数，包括裁剪、压缩等

`git_operation()`方法:

如果你把图片上传到你的 github上这个方法就不用更改了.但是要确保在可以push到github的文件夹里，按照之前操作兴建了博客文件备份仓库

`handle_photo()`方法:
注意: 该脚本对图片的命名规则有要求.
最前面是日期，然后用_进行分隔；后面是图片的描述信息，注意不要包含_和.符号
![](https://img-blog.nos-eastchina1.126.net/blog_photos_git_4.png)

### 5.注意事项
5.1 
最前面是日期，然后用_进行分隔；后面是图片的描述信息，注意不要包含_和.符号

图片应该这样命名: `2016-10-12_xxx.jpg/png`；存放在`photos`中，然后脚本运行会生成压缩图片，放置在`min_photos`文件夹中。

5.2

`tool.py`文件中`open`里面的设置的是本地博客路径

如`D:/GitHub/AomanHao.github.io/source/photos/data.json`

`D:/GitHub/AomanHao.github.io/`是你的博客在本地的路径，`data.json`是图片信息文件

5.3
点开图片可以显示，缩略图不显示

下载empty图，[下载地址](https://raw.githubusercontent.com/wardseptember/BlogPicture/master/assets/img/empty.png)，直接右键另存，保存为“empty.png”。

在你博客的本地仓库source下新建一个文件夹命名为assets,再在assets下新建一个文件夹命名为img。最后把empty.png放到img里面。

我的目录如下：
![](https://img-blog.nos-eastchina1.126.net/blog_photos_git_5.png)


结尾：
在github上新建一个仓库，主要用于存储图片，可以通过url访问到，也方便管理
将要放到相册的图片处理成json格式的数据，然后进行访问，这里json的格式需要配合要使用的样式，所以需要处理成特定格式的json数据，下面会给出
图片裁剪，因为相册显示的样式最好是正方形的的图片，这里使用脚本处理一下
图片压缩，相册显示的图片是压缩后的图片，提高加载的速度，打开后的图片是原图。

问题：
当我用中文作为相册名字的时候，无法生成data.json文件，很纳闷，报错 UTF8的编码错误

算了，暂时找不改正的方法，可能是python是2.多的原因吧，我的相片都是用了英文命名

[参考文章1](https://www.jianshu.com/p/a9f309aaa0e0)
[参考文章2](http://lawlite.me/2017/04/13/Hexo-Github%E5%AE%9E%E7%8E%B0%E7%9B%B8%E5%86%8C%E5%8A%9F%E8%83%BD/)
[参考文章3](https://blog.csdn.net/wardseptember/article/details/82780684)

