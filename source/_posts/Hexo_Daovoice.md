---
title: 个人博客迁移到托管平台Netlify
date: 2019-05-03 10:59:59
tags: [Hexo, GitHub]
toc: true
---

个人博客迁移到托管平台Netlify上
<!--more-->
Netlify是一家国外的静态网站的托管平台，提供免费的https，自动化部署和升级，可以监控GitHub、GitLab或者Bitbucket做到自动更新发布。
<font color=DeepPink size=6>个人体会访问速度不是很理想，不如部署在GitHub上。</font>


### 一、使用github或者gitlab登陆netlify

打开[Netlify网站](https://app.netlify.com/)
然后点击右上角Sign up注册账号，选择GitHub关联登录。

![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step1.png)
### 二、根据github/gitlab仓库创建网站

创建站点，点击New site from Git按钮：
![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step0.5.jpg)
### 三、选择代码托管空间
可以选择GitHub、GitLab或者BitBucket。

![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step2.png)

![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step3.png)
### 四、选择要部署的项目仓库
点击你已经建好的库，选好分支（默认master即可），然后点击“Deploy site”，系统就会自动编译你的静态页面了。网站的控制台去进行设置域名绑定和https申请即可，部署成功后会自动进行cdn加速的。

![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step4.png)




之后我们就不需要这么麻烦了以后编辑好文章之后，只需要执行 hexo clean && hexo g && hexo d 即可自动化部署，然后要记得将我们的项目文件 push 到 github 的 master分支上去哦。

## 域名解析
### 网站引导
Netlify网站 提供的网站域名是该网站的二级域名，看起来不太美观，如果你拥有自己的域名，可以通过绑定自己的域名然后跳转到Netlity的二级域名。
![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step7.jpg)


![](https://img-blog.nos-eastchina1.126.net/blog/hexo_netlity_step8.png)

### 域名控制台
添加两条解析记录，一条A记录，一条CNAME记录。A记录的记录值IP是你的`https://xxx.netlify.com`域名对应的`ip`，这个可以网上查。
CNAME记录的记录值是`https://xxx.netlify.com`的`xxx.netlify.com`值，添加完解析后就可将你的域名绑定到`Netlify`了。


## 使用体验
想要部署在Netlity的初衷是部署在Coding上需要备案，且已经被公安催了要备案，需要一个不用备案的代码托管网站。在网站部署操作不是很麻烦，但是实际部署下来访问速度不是很理想，不如部署在GitHub上。纠结一下