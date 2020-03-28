---
title: ISP-YUV格式
date: 2020-03-28 18:44:45
tags: [ISP, 图像处理]
mathjax: true
---

ISP-YUV格式
<!--more-->
## 简介
数字图像处理的过程中，YUV文件是比较常见的视频源数据。YUV不像RGB那样要求三个独立的视频信号同时传输，所以用YUV方式传送占用极少的频宽。

## YUV采样格式
和RGB颜色空间相比，YUV颜色空间充分利用了人眼的特性，人的眼睛对亮度的敏感度远大于色度。在保证基本画质的前提下，可以对一幅画面的色度分量进行删减。下面三张图片是常见的三种YUV采样方式，YUV4：4：4、YUV4：2：2、YUV4：2：0。其中，YUV4：4：4是一种无压缩的采样方式，每一个Y分量对应一组UV分量；YUV4：2：2的采样方式丢弃了一半的色度分量，每两个Y分量对应一组UV分量；YUV4：2：0的采样方式对齐了四分之三的色度分量，每四个Y分量对应一组UV分量。


![](https://img-blog.nos-eastchina1.126.net/blog/blog_yuv_1.bmp)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_yuv_2.bmp)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_yuv_3.bmp)


## YUV文件格式之UYVY和I420
下面说明UYVY和I420的文件存储格式。
### <1> UYVY文件
UYVY文件是YUV4：2：2采样格式的一种存储格式，具体的地址对应关系如下图所示，U、Y、V、Y依次按顺序存储在文件中。

![](https://img-blog.nos-eastchina1.126.net/blog/blog_yuv_4.bmp)

### <2> I420文件
I420文件是YUV4：2：0采样格式的一种存储格式，具体的地址对应关系如下图所示，和UYVY文件稍有不同。I420文件先存储Y块、然后是U块和V块。每个Y/U/V块块内的的像素依次存储在文件中。

![](https://img-blog.nos-eastchina1.126.net/blog/blog_yuv_5.bmp)


## 
以YUV4：2：2 和YUV4：2：0转换为例，如下：

　　最简单的方式：

　　YUV4:2:2 ---> YUV4:2:0  Y不变，将U和V信号值在行(垂直方向)在进行一次隔行抽样。 YUV4:2:0 ---> YUV4:2:2  Y不变，将U和V信号值的每一行分别拷贝一份形成连续两行数据。

　　在YUV420中，一个像素点对应一个Y，一个4X4的小方块对应一个U和V。对于所有YUV420图像，它们的Y值排列是完全相同的，因为只有Y的图像就是灰度图像。YUV420sp与YUV420p的数据格式它们的UV排列在原理上是完全不同的。420p它是先把U存放完后，再存放V，也就是说UV它们是连续的。而420sp它是UV、UV这样交替存放的。(见下图) 有了上面的理论，我就可以准确的计算出一个YUV420在内存中存放的大小。width * hight =Y（总和） U = Y / 4   V = Y / 4 ，所以YUV420 数据在内存中的长度是 width * hight * 3 / 2。
## 色域转换

本文采用的转换公式如下：
R =1.164*(Y-16) + 1.596*(V-128)
G =1.164*(Y-16) - 0.813*(V-128) - 0.392*(U-128)
B =1.164*(Y-16) + 2.017*(U-128)
具体实践的时候，我又将这些浮点数扩大1024倍变为定点数，然后再做处理，经过处理后的公式如下：
R =(1192*(Y-16) + 1634*(V-128))/1024
G =(1192*(Y-16) -  833*(V-128) -401*(U-128))/1024
B =(1192*(Y-16) + 2065*(U-128))/1024


[参考YUV播放器设计](https://blog.csdn.net/jiandan524/article/details/57452211)

#[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
#[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
#[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


