---
title: 详解同为4800W像素的相机传感器，三星GM1和索尼IMX586区别在哪里？
date: 2019-09-07 18:44:45
tags: [ISP, 图像处理]
---

详解同为4800W像素的相机传感器，三星GM1和索尼IMX586区别在哪里？
<!--more-->

数字影像之父Bryce Bayer基于RGB模式，通过在感光元件前加上一个滤镜的方法终于实现了彩色照片。Bayer滤镜跨出了照片从黑白到彩色的一大步，但是对于挑剔的人眼来说，每个像素只有一个颜色是远远不够的，所以还需要后期色彩还原去猜色，最后形成一张完整的彩色照片。这一整套流程，就叫做Bayer阵列。数码相机包括手机拍摄照片的大致流程：感光元件→Bayer滤镜→色彩还原。可以看下图


![](https://img-blog.nos-eastchina1.126.net/blog/blog_4800W_sensor.png)

IMX586是索尼适用于手机的全新堆栈式CMOS感光元件，这颗感光元件有效像素高达4800万。通过Quad Bayer的排列结构变换，合成之后能够将感光度提升至1.6μm像素尺寸的水平。就是说，搭载IMX586传感器的手机，正常模式下是4800万像素，在使用夜景模式时，则会转换成高曝光、低噪点的拍照模式。

IMX586最大的特色就是使用 Quad Bayer 阵列，不同于经典的Bayer阵列是以2x2共四格分散RGB的方式成像，Quad Bayer 阵列扩大到了4x4，并且以2x2的方式将RGB相邻排列。在使用搭载IMX586传感器手机拍照的时候，Quad Bayer 阵列会让每一个像素点就近计算周围的颜色，并且通过独立的信号处理变换像素结构，从而实时输出4800万像素的高清照片。换句话说，IMX586的4800万个感光单元每个都能独立显示并且输出数据。4800万像素的照片是硬件直出的，无需软件插值。

![](https://img-blog.nos-eastchina1.126.net/blog/blog_4800W_1.jpg)


三星GM1的输出方式如下图所示，阵列也扩大到了4x4，但是和IMX586相比，每个2x2阵列只能识别同样的颜色，且只能一起输出数据。也就是说，GM1传感器直出的照片素质跟1200万传感器输出的图像结果大体相同。


![](https://img-blog.nos-eastchina1.126.net/blog/blog_4800W_2.jpg)


### 索尼imx586及更新的imx600都是可以直出4800W像素的传感器，且用在华为的高端旗舰上，三星GM1是不能直出4800W像素的，用在中端手机终端上，宣传4800W是一个吆喝点。

声明：

此资料部分转载自网络，仅供学习参考。
[参考资料](http://dy.163.com/v2/article/detail/E5KN3O100511HI42.html)

#[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
#[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
#[我的GitHub主页，欢迎访问](https://github.com/AomanHao)

