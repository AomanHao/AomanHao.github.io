---
title: 滤光片相关
date: 2019-09-21 21:44:45
tags: [ISP]
---

滤光片相关
<!--more-->Hexo博客需要引入第三方插件，不少包作者误把包项目得`.git`文件上传到`github`，或者在插件的`github`路径下直接下载插件文件夹，结果是插件内含有`.git`文件，导致下载别的`npm`包时报错`npm err:`

### 报错信息如下：
```
$ npm install hexo-generator-index-pin-top --save                                            npm ERR! path D:\GitHub\AomanHao.github.io\node_modules\hexo-symbols-count-time
npm ERR! code EISGIT
npm ERR! git D:\GitHub\AomanHao.github.io\node_modules\hexo-symbols-count-time: Appears to be a git repo or submodule.
npm ERR! git     D:\GitHub\AomanHao.github.io\node_modules\hexo-symbols-count-time
npm ERR! git Refusing to remove it. Update manually,
npm ERR! git or move it out of the way first.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\10143\AppData\Roaming\npm-cache\_logs\2019-11-22T12_30_49_238Z-debug.log
```


![](https://img-blog.nos-eastchina1.126.net/blog/git_error_repo.png)
### 解决方式：


进入到报错的/data/app/pay/node_modules/alipayment-fork目录去把.git目录删除就可以了

![](https://img-blog.nos-eastchina1.126.net/blog/git_error_repo1.png)

---

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


