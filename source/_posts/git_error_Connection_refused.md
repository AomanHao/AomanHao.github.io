---
title: Gitc错误Failed to connect to 127.0.0.1 port 1080 Connection refused拒绝连接错误
date: 2020-04-05 10:59:59
tags: [Hexo, Next]
---
 
Failed to connect to 127.0.0.1 port 1080: Connection refused拒绝连接错误
<!--more-->

## 一、git拒绝连接原因分析
使用git从远程仓库下载代码出现上述的错误是因为使用了proxy代理，所以要解决该问题，核心操作就是要取消代理

## 二、解决方式
### 1、查看Linux当前有没有使用代理
通过git的配置文件查看有无使用代理（没有成功）
查询是否使用代理：
```
git config --global http.proxy 

git config --global https.proxy 
```

![](https://img-blog.nos-eastchina1.126.net/blog_hexo_proxy_1.png)


### 2、取消代理设置
#### 方式一：通过git取消代理设置
```
git config --global --unset http.proxy

git config --global --unset https.proxy
```
![](https://img-blog.nos-eastchina1.126.net/blog_hexo_proxy_2.png)

#### 方式二：通过系统命令取消代理
```
unset http_proxy

unset ftp_proxy

unset all_proxy

unset https_proxy

unset no_proxy
```



 [我的个人博客地址，欢迎访问](http://www.aomanhao.top)
 [我的CSDN地址，欢迎访问](https://blog.csdn.net/Aoman_Hao)
 [我的GitHub主页，欢迎访问](https://github.com/AomanHao)