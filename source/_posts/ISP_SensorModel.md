---
title: sensor binning
date: 2021-06-01 10:08:00
tags: [ISP, 图像处理, sensor]
---

sensor binning
<!--more-->


Signal是简单的增加，Noise是以均方根形式增加

例如：
2*2的binning模式中，signal增加4倍，noise增加$\sqrt4$倍，so SNR增加2倍。

sony sensor 每个pixel是10bit的，4个10bit的 binning后输出一个12bit数据

signal data $S$ is：
$$
S = S_{10} + S_{10} + S_{10} + S_{10} = S_{12}
$$

其中，$S_{10}$为10bit signal data

$$
N = \sqrt {N_{10}^2 + N_{10}^2 + N_{10}^2 + N_{10}^2}
$$
其中，$N_{10}$为10bit noise data


## Binning 

Binning是将相邻pixel（相同颜色）感应的电荷加在一起，以一个pixel的模式读出。在环境光照低的情况下，提高摄像头表现力

处理位置：电荷域（charge）、模拟（电压）域（valtage）、数模转换后的数字域（digital）。

1、电荷域的N个pixel做binning，signal放大N倍，readout noise 减少，所以 S/N差不多增加N倍。

2、模拟（电压）域（valtage）和数字域环节在读出pixel值之后，会有readout noise，N个pixel做binning，signal放大N倍，因为readout noise 增加导致noise放大$\sqrt N$，所以 S/N差不多是之前$\sqrt N$倍。

![](https://img-blog.nos-eastchina1.126.net/blog/blog_sensor_binning.png)
上图行列均做x2，相当分辨率下降为之前的1/4

### 方案1：sensor靶面大小不变，pixel数目不变，pixel合并降低分辨率
低照环境下，通过binning技术降低sensor输出分辨率提高亮度和信噪比

比如800w pixels 的sensor，良好光照环境下，输出800w 10bit数据，低照环境下做2x2的binning，输出200w 的12bit数据较之前会有信噪比的提升，若输出10bit数据，亮度也会有提升

### 方案2：扩大sensor靶面，pixel数目不变，pixel大小增大
目标输出400w pixels，靶面增加，pixel大小增加即感光面积增加

比如pixel大小$x$ 平方微米，增加为$2x$平方微米，即pixel感光面积为$4x^2$，较之前的$x^2$提升4倍，SNR由$\frac {S}{\sqrt{S} + D}$提升为$\frac {S}{\sqrt{4S} + D}$，整体SNR约提升2倍




















## [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
## [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
## [我的GitHub主页，欢迎访问](https://github.com/AomanHao)

