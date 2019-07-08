---
title: Hexo博客yilia主题首页添加helper-live2d模型插件
date: 2018-08-23 09:39:40
tags: [Hexo, GitHub, yilia]
toc: true
---

Hexo添加helper-live2d模型插件
<!--more-->

插件效果
[插件的github地址](https://github.com/EYHN/hexo-helper-live2d)
插件作者提供了较为详细的安装步骤，我结合自己操作和图示，提供大家。

效果展示：红框内为2d模型，可以随鼠标移动而变化
![](https://img-blog.nos-eastchina1.126.net/koharu4.png)



## 安装模块:

hexo博客根目录选择`cmd`命令窗口或者`git bash` 输入以下代码，安装插件
### 操作：
```
npm install --save hexo-helper-live2d
```
![](https://img-blog.nos-eastchina1.126.net/koharu1.png)



### 下载模型
作者提供了三个下载模型的办法，我选择操作比较简单的一种
`npm 模块名` 的方法

作者提供以下模型的模型包，模型包预览地址见下面的链接，选择你想用的模型，记住名字，选择对应的后缀模型包

[作者各种模型包展示](https://huaji8.top/post/live2d-plugin-2.0/)



```
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko
live2d-widget-model-z16
```

选择好对应的模型，使用 `npm install 模型的包名 `来安装，比如我选择的的是`live2d-widget-model-koharu` 模型包
### 操作：
在hexo博客根目录选择`cmd`命令窗口或者`git bash` 输入以下代码

```
npm install live2d-widget-model-koharu
```
执行安装就完事了

![](https://img-blog.nos-eastchina1.126.net/koharu3.png)


## 配置
请向`Hexo`的 `_config.yml` 文件添加配置.
### 操作：
打开个人Hexo博客文件根目录下的 `_config.yml` 文件，在最后添加一下代码
示例:

```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-koharu
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```
注：在移动端可能会干扰阅览，可以选择取消移动端显示，`true`改为`fasle`
```
  mobile:
    show: fasle
```

你需要配置的是` use: live2d-widget-model-koharu`
`use`后为你选择的安装包的全称

![](https://img-blog.nos-eastchina1.126.net/koharu2.png)


插件部署与配置就完成了

## 效果预览

本地预览
```
hexo clean && hexo g && hexo s 
```

## 博客部署

博客部署
```
hexo clean && hexo g && hexo d 
```