---
title: ISP图像处理之Demosaic算法及相关
date: 2020-07-21 10:08:00
tags: [ISP, Sensor, 图像处理]
---

ISP图像处理之Demosaic算法及相关
<!--more-->

## CFA及Demosaic介绍
### 1.Bayer（拜耳滤波器得到彩色）
图像在将实际的景物转换为图像数据时， 通常是将传感器分别接收红、 绿、 蓝三个分量的信息， 然后将红、 绿、 蓝三个分量的信息合成彩色图像。 该方案需要三块滤镜， 这样价格昂贵，且不好制造， 因为三块滤镜都必须保证每一个像素点都对齐。

![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_sensor_cfa_ray.jpg)
（光线透过镜头然后通过颜色分离片分离 R G B信息，示意图来自《颜色插值算法改进及其电路设计》）

通过在黑白 cmos 图像传感器的基础上， 增加彩色滤波结构和彩色信息处理模块就可以获得图像的彩色信息， 再对该彩色信息进行处理， 就可以获得色彩逼真的彩色图像。通常把彩色图像传感器表面覆盖的滤波称为彩色滤波阵列（Color Filter Arrays，CFA）。
![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_sensor_cfa.jpg)
目前最常用的滤镜阵列是棋盘格式的， 已经有很多种类的， 其中绝大多数的摄像产品采用的是原色贝尔模板彩色滤波阵列（Bayer Pattern CFA）。R、G、B 分别表示透红色、透绿色和透蓝色的滤镜阵列单元。由于人的视觉对绿色最为敏感，所以在 Bayer CFA 中G分量是 R和B 的二倍，在每个像素点上只能获取一种色彩分量的信息，然后根据该色彩分量的信息通过插值算法得到全色彩图像。


### 2.Demosaic颜色插值 （抵马赛克）
当光线通过 Bayer型 CFA（Color Filter Arrays） 阵列之后， 单色光线打在传感器上，每个像素都为单色光，理想的Bayer 图是一个较为昏暗的马赛克图。（见感光元件成像示意图（2））。

根据sensor上感知的光线强度，再结合对应滤光片颜色排列就可以估计出 sensor输出的彩色图像（见bayer滤镜输出图像示意图（3））


首先需要说明的就是demosaiced并不是和字面的意思一样是为了去除电影中的一些打马赛克的图像，而是数字图像处理中用来从不完整的color samples插值生成完整的color samples的方法(因为bayer pattern看起来像一个个马赛克，因此称为去马赛克)。在sensor端通常需要使用CFA滤镜来得到Bayer pattern，而在后面的处理中需要把bayer pattern变成完整的RGB444(真彩色)图像。在ISP中需要有这么一个模块来做。

在传统的ISP中有很多算法可以来做这个插值，包括最近邻域法，bilinear 插值，cubic 插值等。

## 

![](https://img-blog.nos-eastchina1.126.net/blog/blog_4800W_sensor.png)

###[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
###[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
###[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


