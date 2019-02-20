---
title: Hexo博客使用valine评论系统无效果及终极解决方案
date: 2019-02-20 10:59:59
tags: [Hexo, Next, GitHub]
---
 
 Hexo博客使用valine评论系统无效果及终极解决方案
<!--more-->

## 注意事项
有一些博主valine评论系统无效果，有一些原因：

>1、很大程度是因为next的版本升级导致某些参数设置不同
2、valine评论是基于LeanCloud，还有一个文章阅读次数功能也是用LeanCloud，两者会有一点冲突

之后会给出一些解决方案

## 评论系统选择
Hexo可用的评论系统有很多，如下：  

来必力：https://livere.com （需要邮箱注册，加载慢，较卡顿）

畅言： http://changyan.kuaizhan.com （安装需要备案号）

Gitment： https://github.com/imsun/gitment （加载慢，有Bug）

Valine: https://github.com/xCss/Valine (简约，实用，使用Leancloud作为线上数据库）


## 评论系统配置过程
`next` 集成了 `leancloud` 。可以在`leancloud`进行账号注册。

### 1、注册LeanCloud
注册地址 https://leancloud.cn/

### 2、配置LeanCloud

创建一个新的应用
![k2FG0s.png](https://s2.ax1x.com/2019/02/20/k2FG0s.png)

随便取个名字，自己看着取吧
![k2FdpT.png](https://s2.ax1x.com/2019/02/20/k2FdpT.png)

应用创建完成，点开配置按钮
![k2F8mj.png](https://s2.ax1x.com/2019/02/20/k2F8mj.png)

点击`设置` > `应用Key` 复制App ID 和 App Key
![k2FNt0.png](https://s2.ax1x.com/2019/02/20/k2FNt0.png)

点击`设置` > `安全中心` 把自己博客网址添加到安全中心，保证数据的调用安全。
![k2FUhV.png](https://s2.ax1x.com/2019/02/20/k2FUhV.png)

### 修改配置文件
在主题`themes`目录下有第三方提供的主题配置文件`\themes\next\_config.yml`
打开主题配置文件 添加`appid` 和`appkey`:

```
valine:
  enable: true # When enable is set to be true, leancloud_visitors is recommended to be closed for the re-initialization problem within different leancloud adk version.
  appid: 粘贴id
  appkey: 粘贴key
  notify: false # mail notifier, See: https://github.com/xCss/Valine/wiki
  verify: false # Verification code
  placeholder: 欢迎交流讨论... # comment box placeholder
  avatar: mm # gravatar style
  guest_info: nick,mail,link # custom comment header
  pageSize: 10 # pagination size
```


## 阅读次数功能配置过程
### 创建阅读次数Class类
在应用里面创建名称为`Counter`的`Class`，名称必须为`Counter`
![k2Ftkq.png](https://s2.ax1x.com/2019/02/20/k2Ftkq.png)

创建完成，效果如下：
![k2FJ7n.png](https://s2.ax1x.com/2019/02/20/k2FJ7n.png)

## 修改配置文件

```
leancloud_visitors:
  enable: true
  appid: 粘贴id
  appkey: 粘贴key
```

## 评论系统无效原因
next为5.X版本的时候，配置文件`_config.yml`的`valine`的`id`和`key`的书写方式为`appid`和`appkey`

```
valine:
  appid: 粘贴id
  appkey: 粘贴key
```
next为6.X版本的时候，配置文件`_config.yml`的`valine`的`id`和`key`的书写方式为`app_id`和`app_key`
```
valine:
  app_id: 粘贴id
  app_key: 粘贴key
```

而`Valine`文件`themes\next\layout\_third-party\comments\valine.swig`内调用函数依旧为`appid`和`appkey`
```
	appId: '{{ theme.valine.appid }}',
    appKey: '{{ theme.valine.appkey }}',
```
## 解决方案

---