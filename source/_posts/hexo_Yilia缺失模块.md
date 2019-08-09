---
title: Hexo博客Yilia主题_缺失模块_解决方案
date: 2018-02-08 18:44:45
tags: [GitHub, Hexo, yilia]
---
hexo博客yilia主题
<!--more-->
hexo博客yilia主题,左侧栏目有一个全部文章的按钮，刚开始开始报错缺失模块，如下图：

![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtZDNmYjI4YjVhMWRjYjY5Yy5wbmc)

我解决了这个问题着实不容易饶了弯路，但是跟着提示步骤，其实很简单，走起：


1、查看node版本
`win键+R键 `打开命令控制台，输入代码  

`node -v `查看node版本，如下图：

![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtZTc5ODE1NWVkZjlkM2M2MC5wbmc)


只要node的版本高于6.2就行



2、博客根目录下运行命令行
```
npm i  hexo-generator-json-content --save
```
如果这个包已经存在，会报错，图忘了截了。

但是你需要在theme文件夹的yilia主题文件夹下，找到`node——modules`文件夹。如果`hexo-generator-json-content `这个包是存在的就OK，可以进行第三步了，见下图：

![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtN2JkYzM2MzljYTA1Y2M2NC5wbmc)




3、配置文件
博客根目录下，找到_config.yml，打开找一个空白地方复制一下配置信息：

```
jsonContent:

  meta: false

  pages: false

  posts:

    title: true

    date: true

    path: true

    text: false

    raw: false

    content: false

    slug: false

    updated: false

    comments: false

    link: false

    permalink: false

    excerpt: false

    categories: false

    tags: true
```

<h4>**注（重点）：细节处--复制的信息格式要调好
1、配置文件内找空白处粘贴文件
2、第一行jsonContent:    即下图46行前没有空格
47、48、49行前有一个空格
剩下的有两个空格**

如下图所示：

![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtMzBlNDY4ZGQ0NzMyZWE0Mi5wbmc)


保存后同步文件在看你的博客，点全部文章按钮

应该是修复了缺失模块这个报错

谢谢

#[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
#[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
#[我的简书主页，欢迎访问](https://www.jianshu.com/u/4082f682db35)
#[我的GitHub主页，欢迎访问](https://github.com/AomanHao)