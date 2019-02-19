---
title: git上传文件到Github
date: 2018-07-01 12:35:55
tags: [GitHub, Git]
---

准备工作：

<!--more-->

1、电脑装有Git
2、GitHub 已有仓库

1、克隆GitHub仓库，到本地

文件夹右键选择Git Bash Here，输入代码<br>

```
    Git clone git@github.com:用户名/仓库名.git
```
2、放置代码内容到第一步下载的文件夹里

3、执行代码

```
git add .
git commit -m "情况说明"
git push origin master
```

4、上传成功

---

### 多电脑同步
使用电脑搭建好博客后可能面临如下问题

1、是在家里私人电脑上搭建的，想在公司也可以愉快的写文章
2、换了一台新的电脑（挣钱了要换装备😂）
3、电脑系统崩了😭

关于多电脑同步解决方案1

gitHub分支管理，master分支存博客静态网页资源，Hexo分支存所有源文件（设置为默认分支）
每个电脑每次更新文章前需要正常的git同步操作
每个电脑每次更新文章后需要正常的git同步操作
但是个人感觉不安全，别人可能直接把你的Hexo分支拉取下来就等于获取了你的全部博客资源（虽然我的博客没什么有用的价值😂）
具体分支实现可参考利用分支同步
关于多电脑同步解决方案2

每次手动拷贝最新的文件夹替换另一台电脑旧文件夹（想想就麻烦）
通过云盘如Dropbox自动同步整个文件夹，使所有的电脑都可以同步到最新的
目标电脑获取到最新的博客文件后

如果是情形3可以考虑先把整个博客目录拷贝出来到新的系统博客目录下
GitHub添加配置新电脑的`SSH key` 和搭建时一样参考`Mac`搭建`Hexo`博客及`NexT`主题配置优化
配置运行环境，执行如下指令
```
brew install node   // 安装Node.js
npm install -g hexo // 安装hexo
```
切换到博客目录下安装博客模块和插件 (具体参考之前安装过的插件)
```
npm install
 npm install hexo-deployer-git --save
 npm install hexo-generator-feed --save
 npm install hexo-generator-sitemap --save
 npm install hexo-generator-feed --save
 npm install hexo-generator-searchdb --save
 ```
 ```
 
npm install -g gulp 
    npm install gulp-minify-css --save
    npm install gulp-uglify --save
    npm install gulp-htmlmin --save
    npm install gulp-htmlclean --save
    npm install gulp-imagemin --save
    ```