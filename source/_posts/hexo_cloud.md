---
title: 云储存选择做Hexo博客图床（腾讯云、七牛云、网易云）
date: 2019-02-26 10:59:59
tags: [Hexo]
---

博客图床
<!--more-->
## 前言
博客里需要添加很多图片作为内容的补充，但是把图片放在本地博客文件夹里，上传到网上后，加载这些图片就是一个很大的问题，他们会拖累网页加载的速度，所以建议把图片放图床里，通过外链来访问和加载这些图片。

## 云对象储存服务商
国内免费的云对象储存的服务商(网易云、七牛云、腾讯云)



### 1.网易云

官网：https://www.163yun.com/
![网易云](https://img-blog.nos-eastchina1.126.net/blog/cloud163.jpg)
网易NOS（Netease Object Storage）网易对象存储为你提供基于互联网的数据存取服务，通过使用 NOS，你可以随时通过网络将你的文本、图片、音视频等各类文件存储到 NOS 系统中，并随时可以通过网络进行安全访问。

NOS 对象存储从三个维度进行计量收费：存储容量、流量、接口调用次数。存储容量0-50 GB是免费，下载流量在0-20 GB免费，每月前 10 万次 Put 请求免费，每月前 100 万次 Get 请求免费。






### 2.七牛云

官网：https://www.qiniu.com/

![七牛云](https://img-blog.nos-eastchina1.126.net/blog/cloud_qiniu.jpg)

七牛云存储提供云存储、云处理、云加速分发一站式服务，注册成为标准用户后可获得10GB免费存储空间、每月10GB下载流量、每月10万次Put请求、每月100万次Get请求。

#### 缺点：
临时域名仅有三个月，三个月后没有自己的备案域名，所有图片均会失效





### 3.腾讯云

官网：https://cloud.tencent.com/

![](https://img-blog.nos-eastchina1.126.net/blog/cloud_tencent.png)

腾讯云对象存储服务COS，全称为Cloud Object Service，主要是为开发者提供安全、稳定、高效、实惠的对象存储服务，开发者可以将任意动态、静态生成的数据，存放到COS上，再通过HTTP的方式进行访问。

#### 缺点：
自2019年后新建用户可以领取一个6月有效期，50G的存储量。6月过后，按照存储量和流量收费。



---
## 在线图床选择

https://sm.ms SM图床

https://tu.aixinxi.net/ 爱信息图床

https://imgchr.com/ 路过图床

---


## 总结
云储存选择`网易云`

图床选择`路过图床`

目前还在用路过图床，缺点是图片链接不能看到任何图片名称等图片信息，不方便插入在博客里

