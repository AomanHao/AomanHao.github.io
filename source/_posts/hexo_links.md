---
title: Hexo博客Next主题友链页面
date: 2019-12-29 18:44:45
tags: [Hexo, Next]
---


Hexo博客Next主题友链页面
<!--more-->

博客友链太多，需要自定义一个友情链接页面

### link渲染文件
在 `hexo/themes/next/layout` 目录下建一个 `link.swig`文件，写入以下代码

```

{% block content %}
  {######################}
  {### LINKS BLOCK ###}
  {######################}

    <div id="links">
        <style>

            #links{
               margin-top: 5rem;
            }

            .links-content{
                margin-top:1rem;
            }

            .link-navigation::after {
                content: " ";
                display: block;
                clear: both;
            }

            .card {
                width: 300px;
                font-size: 1rem;
                padding: 10px 20px;
                border-radius: 4px;
                transition-duration: 0.15s;
                margin-bottom: 1rem;
                display:flex;
            }
            .card:nth-child(odd) {
                float: left;
            }
            .card:nth-child(even) {
                float: right;
            }
            .card:hover {
                transform: scale(1.1);
                box-shadow: 0 2px 6px 0 rgba(0, 0, 0, 0.12), 0 0 6px 0 rgba(0, 0, 0, 0.04);
            }
            .card a {
                border:none;
            }
            .card .ava {
                width: 3rem!important;
                height: 3rem!important;
                margin:0!important;
                margin-right: 1em!important;
                border-radius:4px;

            }
            .card .card-header {
                font-style: italic;
                overflow: hidden;
                width: 236px;
            }
            .card .card-header a {
                font-style: normal;
                color: #2bbc8a;
                font-weight: bold;
                text-decoration: none;
            }
            .card .card-header a:hover {
                color: #d480aa;
                text-decoration: none;
            }
            .card .card-header .info {
                font-style:normal;
                color:#a3a3a3;
                font-size:14px;
                min-width: 0;
                text-overflow: ellipsis;
                overflow: hidden;
                white-space: nowrap;
            }
        </style>
        <div class="links-content">

             <div class="no-icon note warning"><div class="link-info">👨‍🎓 跟着大佬走，成为小大佬</div></div>
            <div class="link-navigation">
                    {% for link in theme.defaultlinks %}

                    <div class="card">
                        <img class="ava nofancybox" src="{{ link.avatar }}"/>
                        <div class="card-header">
                        <div><a href="{{ link.site }}" target="_blank"> {{ link.nickname }}</a> <a href="{{ link.site }}"><span class="focus-links"><i class="fa fa-plus" aria-hidden="true"></i>&nbsp;关注</span></a></div>
                        <div class="info">{{ link.info }}</div>
                        </div>
                    </div>

                {% endfor %}

            </div>

            <div class="no-icon note primary"><div class="link-info">🍭 五湖四海的朋友们</div></div>

             <div class="link-navigation">
                    {% for link in theme.friendslinks %}

                    <div class="card">
                        <img class="ava nofancybox" src="{{ link.avatar }}"/>
                        <div class="card-header">
                        <div><a href="{{ link.site }}" target="_blank"> {{ link.nickname }}</a> <a href="{{ link.site }}"><span class="focus-links"><i class="fa fa-plus" aria-hidden="true"></i>&nbsp;关注</span></a></div>
                        <div class="info">{{ link.info }}</div>
                        </div>
                    </div>

                {% endfor %}

            </div>

            {{ page.content }}
            </div>
        </div>

  {##########################}
  {### END LINKS BLOCK ###}
  {##########################}
{% endblock %}

```

### page渲染文件

然后修改 `hexo/themems/next/layout/page.swig` 文件，
```
#}{% elif page.type === "tags" and not page.title %}{#
    #}{{ __('title.tag') + page_title_suffix }}{#
```
位置添加如下代码：
```
<!-- 友情链接-->
#}{% elif page.type === 'links' and not page.title %}{#
  #}{{ __('title.links') + page_title_suffix }}{#
```
如图所示：

![](https://img-blog.nos-eastchina1.126.net/blog/hexo_links1.png)

然后还是在这个 page.swig 文件中，引入刚才新建的 swig 页面：
```
<!-- 友情链接-->
{% elif page.type === 'links' %}
    {% include 'links.swig' %}
```
这个代码位置可以放到下面
```
    {% elif page.type === 'categories' %}
      <div class="category-all-page">
        <div class="category-all-title">
            {{ _p('counter.categories', site.categories.length) }}
        </div>
        <div class="category-all">
          {{ list_categories() }}
        </div>
      </div>
    {% elif page.type === 'links' %}
     {% include 'links.swig' %}
    {% else %}
      {{ page.content }}
    {% endif %}
  </div>
```

![](https://img-blog.nos-eastchina1.126.net/blog/hexo_links2.png)

### index文件
然后在 `hexo/source` 下创建 `links` 文件夹，创建 `index.md` 文件，写入以下内容，如下，这个是友链页面的申请信息，可以按照自己想法修改：
```
----
title: 友情链接
date: 2019-12-08 03:21:39
type: "links"
---

---

### 申请要求：

1、内容持续更新且可以稳定访问
2、网页整洁无繁杂广告推广
3、博客主页被百度或谷歌等搜索引擎收录
4、头像能够快速加载
5、拥有独立域名


### 友链声明：

1、本站会主动保存您的 HTTPS 形式的头像图片链接
2、本站会定期清理无法访问的友链，如果更换了链接信息请至评论区留言，谢谢合作！
3、本站会定期查看双方是否互为友链，如果取消本站友链，本站也会将您的友链移除

### 申请方式：

先将本站的友链添加到您的友链，相关信息如下
然后按照以下格式在本站留言区留言，待博主为您添上友链

>名称：AomanHao 
头像链接：http://www.aomanhao.top/images/Avatar.jpg
主页链接：http://www.aomanhao.top/ 
说明信息：图像处理，优化世界


```

### config配置文件
最后，我们添加友链的话，需要在主题配置文件 `hexo/themes/next/_config.xml` 文件末尾添加：
```
# 友情链接
defaultlinks:
  - nickname: AomanHao     # 昵称
    avatar: http://www.aomanhao.top/images/Avatar.jpg    # 头像地址
    site: http://www.aomanhao.top #友链地址
    info: 图像处理，优化世界

friendslinks:
  - nickname: AomanHao     # 昵称
    avatar: http://www.aomanhao.top/images/Avatar.jpg    # 头像地址
    site: http://www.aomanhao.top #友链地址
    info: 图像处理，优化世界
```

`defaultlinks:`呼应的是`link.swig`文件中 `👨‍🎓 跟着大佬走，成为小大佬`段落，此处链接写大佬的博客；
`friendslinks:`呼应的是`link.swig`文件中 `🍭 五湖四海的朋友们`段落，此处链接写朋友的博客。
此处内容可以根据自己需要自行修改

菜单栏汉化需要在 `hexo/themes/next/languages/zh-CN.yml`文件中，新增 links ：

```
menu:

  links: 友链
```


---

[参考文章，sanarous](https://bestzuo.cn/posts/2016690040.html)


### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


