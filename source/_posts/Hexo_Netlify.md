---
title: 个人博客迁移到托管平台Netlify上
date: 2019-05-03 10:59:59
tags: [Hexo]
toc: true
---

个人博客迁移到托管平台Netlify上
<!--more-->
Netlify是一家国外的静态网站的托管平台，提供免费的https，自动化部署和升级，可以监控GitHub、GitLab或者Bitbucket做到自动更新发布



### 一、使用github或者gitlab登陆netlify

打开[Netlify网站](https://app.netlify.com/)
然后点击右上角Sign up注册账号，选择GitHub关联登录。

### 二、根据github/gitlab仓库创建网站

创建站点，点击New site from Git按钮：

### 三、选择代码托管空间
可以选择GitHub、GitLab或者BitBucket。

### 四、选择要部署的项目仓库
点击你已经建好的库，选好分支（默认master即可），然后点击“Deploy site”，系统就会自动编译你的静态页面了。网站的控制台去进行设置域名绑定和https申请即可，部署成功后会自动进行cdn加速的。


之后我们就不需要这么麻烦了以后编辑好文章之后，只需要执行 hexo clean && hexo g && hexo d 即可自动化部署，然后要记得将我们的项目文件 push 到 github 的 master分支上去哦。

## 域名解析
Netlify网站 提供的网站域名是该网站的二级域名，看起来不太美观，如果你拥有自己的域名，可以通过绑定自己的域名然后跳转到Netlity的二级域名。