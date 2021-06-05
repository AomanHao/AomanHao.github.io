---
title: sensor binning
date: 2021-06-01 10:08:00
tags: [ISP, 图像处理, sensor]
---

sensor binning
<!--more-->


Signal是简单的增加，Noise十一均方根形式增加

例如：
2*2的binning模式中，signal增加4倍，noise增加$\sqrt4$倍，so S/N增加2倍。

sony sensor 每个pixel是10bit的，4个10bit的 binning后输出一个12bit数据

signal data S is：
$$
S = S_10 + S_10 + S_10 + S_10 = S_12
$$
S_10为10bit signal data
$$
N = \sqrt {N_10^2 + N_10^2 + N_10^2 + N_10^2}
$$
N_10为10bit noise data


Binning 处理位置：电荷域（charge）、模拟（电压）域（valtage）、数模转换后的数字域（digital）。

电荷域的N个pixel做binning，signal放大N倍，readout noise 减少，所以 S/N差不多增加N倍。

模拟（电压）域（valtage）和数字域环节在读出pixel值之后，会有readout noise，N个pixel做binning，signal放大N倍，因为readout noise 增加导致noise放大$\sqrt N$，所以 S/N差不多是之前$\sqrt N$倍。



方案1：





















## [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
## [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
## [我的GitHub主页，欢迎访问](https://github.com/AomanHao)

