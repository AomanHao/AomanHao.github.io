---
title: Hexo博客Yilia主题_more截断文章_多标签添加
date: 2018-02-08 17:00:06
tags: [GitHub, Hexo, yilia]
---

Hexo博客Yilia主题_more截断文章_多标签添加
<!--more-->
以下均为自己遇到的问题并加以修改或者纠正.



在文章下方可以使用more语句进行截断，这样博客首页只会出现文章的前面一小部分，看起来很清爽简约

 或者
```
 language: zh-CN
 <!--more--> //在需要阶段的地方插入该代码语句
 aa
```


在这里，yilia主题会判断含有`<!--more-->`的位置，然后文章截断两部分，第一部分展示在博客首页，第二部分即上方的aa只能点开展开全文，才能继续阅读文章。

截断效果如下图：


![效果](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtZGZmNzFiY2MxOGRmNzU4My5wbmc)



在这里我对yilia主题做了修改

原始效果为：

![原始效果](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtMmJjNzQ0Njg1N2JjMDRlNi5wbmc)


修改后为：去掉了more按钮，打开文章可以点击文章或者点击展开全文

![修改效果](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtNTFlYTczNmZmZDk0MGQyYy5wbmc)


做法很简单，进入theme目录，打开yilia目录下的_config.yml文件，修改excerpt_link参数：

```
excerpt_link：之后的more单词换成空格
注：‘excerpt_link： ’。其中：后有一个空格键
```

修改图如下图

![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtYzNlYzBiMjE1NDIxYmNlZS5wbmc)


如何给文章加多个标签：

修改如下图，格式为` [tag1, tag2]`

注：逗号之后要有一个空格。`[tag1, tag2]= [tag1+逗号+空格+tag2]`

修改如下图所示：

![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL3VwbG9hZC1pbWFnZXMuamlhbnNodS5pby91cGxvYWRfaW1hZ2VzLzYyODA5NjYtNjIzMDVjOTQwZmVlMjA4Mi5wbmc)


#[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
#[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
#[我的简书主页，欢迎访问](https://www.jianshu.com/u/4082f682db35)
#[我的GitHub主页，欢迎访问](https://github.com/AomanHao)