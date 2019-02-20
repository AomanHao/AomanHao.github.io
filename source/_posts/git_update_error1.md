---
title: git_update_error1
date: 2018-08-01 11:58:40
tags: [GitHub, Git]
toc: true
---

git 上传报错及解决
<!--more-->

## failed to push some refs to 

报错内容，不能推送文件到github上
```
error: failed to push some refs to github地址
```

原因是github项目与本地文件夹一些关键文件的确实，比如.git，readme.md文件等等

## 解决： 
本地文件夹打开控制命令台 

1、添加本地文件夹，github项目更新到本地
```
git add .
git pull origin master
```

2、再上传文件夹到github
```
git push -u origin master
```

## fatal: The remote end hung up unexpectedly
git推送项目时候出现 “fatal: The remote end hung up unexpectedly ” 原因是推送的文件太大。

上传网速过慢导致文件传输不完整

## 解决
等一会，重新在push上传一遍 