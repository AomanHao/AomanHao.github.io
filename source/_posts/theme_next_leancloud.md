---
title: Hexo博客Next主题阅读次数热度不能读取的问题，报错Counter not initialized! More info at console err msg.
date: 2019-01-30 21:55:00
tags: [GitHub, Hexo, Next]
---



Hexo博客Next主题阅读次数热度不能读取的问题
<!--more-->


### 加入valine在线评论
设置效果：

设置方法：
首先要先去[LeanCloud](https://leancloud.cn/)注册一个帐号.然后再创建一个应用.

拿到`appid`和`appkey`之后，打开`themes/next/_config.yml`主题配置文件，查找`valine`，填入`appid `和 `appkey`
我的配置:

```
# You can get your appid and appkey from https://leancloud.cn
# More info available at https://valine.js.org
valine:
  enable: true # When enable is set to be true, leancloud_visitors is recommended to be closed for the re-initialization problem within different leancloud adk version.
  appid: llBsNPTabKsl2d4aU3OvrmSz-gzGzoHsz
  appkey: gzSQowSIzhnuc5eYPj4k7c7z
  notify: true # mail notifier, See: https://github.com/xCss/Valine/wiki
  verify: true # Verification code
  placeholder: 欢迎交流讨论... # comment box placeholder
  avatar: mm # gravatar style
  guest_info: nick,mail,link # custom comment header
  pageSize: 10 # pagination size
  visitor: false # leancloud-counter-security is not supported for now. When visitor is set to be true, appid and appkey are recommended to be the same as leancloud_visitors' for counter compatibility. Article reading statistic https://valine.js.org/visitor.html
  comment_count: true # if false, comment count will only be displayed in post page, not in home page

```

---
## Hexo添加阅读次数
`next` 集成了 `leancloud` 。可以在`leancloud`进行账号注册。
创建一个新的应用。点击应用进入。
创建名称为`Counter`的`Class`，名称必须为`Counter`

[![k1gdSK.md.png](https://s2.ax1x.com/2019/01/31/k1gdSK.md.png)](https://imgchr.com/i/k1gdSK)

点击设置 > 应用Key 复制App ID 和 App Key
[![k1gUW6.md.png](https://s2.ax1x.com/2019/01/31/k1gUW6.md.png)](https://imgchr.com/i/k1gUW6)

修改配置文件
在主题`themes`目录下有第三方提供的主题配置文件`\themes\next_config.yml`
打开主题配置文件 添加`app_id` 和`app_key`:
```
# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.文章热度
leancloud_visitors:
  enable: true
  app_id: llBsNPTabKsl2d4aU3OvrmSz-gzGzoHsz
  app_key: gzSQowSIzhnuc5eYPj4k7c7z
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: false
  betterPerformance: false
```
修改统计设置
打开主题配置文件 定位到 `post_wordcount`
```
# Post wordcount display settings
# Dependencies: https://github.com/willin/hexo-wordcount
post_wordcount:
  item_text: true
  wordcount: true
  min2read: true
  totalcount: false
  separated_meta: true
```
Web安全性
为了保证应用的统计计数功能仅应用于自己的博客，你可以在应用 > 设置 > 安全中心的Web安全域名中加入自己的博客域名，保证数据的调用安全。

[![k1gwQO.md.png](https://s2.ax1x.com/2019/01/31/k1gwQO.md.png)](https://imgchr.com/i/k1gwQO)

---


## 显示文章热度

首先要先去[LeanCloud](https://leancloud.cn/)注册一个帐号.然后再创建一个应用.

设置方法：
`next`主题集成`leanCloud`，打开`themes/next/layout/_macro/post.swig`,准备添加`℃`


```
          {# LeanCloud PageView #}
          {% if theme.leancloud_visitors.enable or (theme.valine.enable and theme.valine.appid and theme.valine.appkey and theme.valine.visitor) %}
            <span id="{{ url_for(post.path) }}" class="leancloud_visitors" data-flag-title="{{ post.title }}">
              <span class="post-meta-divider">|</span>
              <span class="post-meta-item-icon">
                <i class="fa fa-eye"></i>
              </span>
              {% if theme.post_meta.item_text %}
                <span class="post-meta-item-text">{{ __('post.views') + __('symbol.colon') }}</span>
              {% endif %}
                <span class="leancloud-visitors-count"></span>
              <span>℃</span>
            </span>
          {% endif %}
```
插入摄氏度到倒数第三句，如下：
```
<span>℃</span>
```

打开，`themes/next/languages/zh-CN.yml`,将`views`后的文字描述改为热度.
```
views: 热度
```
有的版本不一样，打开，`themes/next/languages/zh-Hans.yml`，将以下

```
visitors: 热度
```

然后打开`themes/next/_config.yml`找到`leancloud_visitors`,将`enable:`改成`true`,再填上自己`LeanCloud`的`app_id`和`app_key`。
```
# Show number of visitors to each article.
# You can visit https://leancloud.cn get AppID and AppKey.文章热度
leancloud_visitors:
  enable: true
  app_id: 你自己的id
  app_key: 你自己的key
  # Dependencies: https://github.com/theme-next/hexo-leancloud-counter-security
  # If you don't care about security in leancloud counter and just want to use it directly
  # (without hexo-leancloud-counter-security plugin), set `security` to `false`.
  security: true
  betterPerformance: false
```

### 报错Counter not initialized! More info at console err msg.

安装`hexo-leancloud-counter-security`插件

```
npm install hexo-leancloud-counter-security --save
```
