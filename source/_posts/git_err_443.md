---
title: Git无法push提示报错443
date: 2021-06-19 10:08:00
tags: [Git]
---


Git无法push提示报错443
<!--more-->

今天在使用git push到github的时候遇到了这样的错误，提示
```
OpenSSL SSL_connect: Connection was reset in connection to github.com:443
```
报错提示

![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_git_err443.png)


可能是电脑使用的代理服务器，在cmd 执行命令，刷新dns 缓存试试
```
ipconfig/flushdns
```

可以在电脑设置里找到网络代理，或者输入命令关闭代理

```
#取消http代理
git config --global --unset http.proxy
#取消https代理
git config --global --unset https.proxy
```

![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_git_err443_web.png)






## [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
## [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
## [我的GitHub主页，欢迎访问](https://github.com/AomanHao)

