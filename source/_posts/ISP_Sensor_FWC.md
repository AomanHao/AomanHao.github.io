---
title: CMOS信噪比与感光面积的关系
date: 2020-09-05 10:08:00
tags: [图像处理]
---

CMOS信噪比与感光面积的关系
<!--more-->

## 前言
一般情况下，相同分辨率的sensor，如果感光面积越大，则其单位像素的感光面积也越大，成像质量也会越好。即相同分辨率品质相当的sensor，`2/3”`的传感器成像质量`一般情况`就要优于`1/2”`的，尤其是在低照环境下的成像。

## 举例
### SC200AI
思特威公司的`SC200AI`举例，一款`200W`sensor（官方资料）
```
项目            |  参数 
Resolution      2MP
Pixel Array     1928H x 1088V
Pixel Size       2.9μm x 2.9μm
Optical Format  1/2.8"
Max Frame Rate  1920H x 1080V @60fps
10 bit DVP
10/8 bit 1/2 lane MIPI
Output Format RAW RGB
CRA 15°
Sensitivity 8,200mV/Lux·s
HDR Mode up to 100dB
Linear Mode 83dB
SNR 42dB
Operation Temperature Range -30°C to +85°C
Best IQ Temperature -20°C to +60°C
Analog = 2.8V
Digital = 1.2V
I/O = 1.8V
Package 41 pin CSP
Package Size 6.26mm x 4.07mm
```


### SC2238
思特威公司的`SC2238`举例，一款`200W`sensor（官方资料）
```
项目 参数
Resolution 2MP
Pixel Array 1936H x 1096V
Pixel Size 3.0μm x 3.0μm
Optical Format 1/2.7″
Max Frame Rate 1936H x 1096V @50fps
Output Interface 12 bit DVP
Output Format RAW RGB
CRA 15°
Sensitivity 3900mV/Lux·s
Dynamic Range 72dB
SNR 40dB
Operation Temperature Range -30°C to +85°C
Best IQ Temperature -20°C to +60°C
Analog = 2.8V
Digital = 1.5V
I/O = 1.8V
Package 41 pin CSP
Package Size 6.48mm x 4.67mm
```
SC2238的像素大小`2.9μm x 2.9μm`，靶面大小`1/2.8"`，分辨率`1920H x 1080V` 

SC200AI的像素大小`3.0μm x 3.0μm`，靶面大小`1/2.7″"`，分辨率`1936H x 1096V`

SC2238像素感光面积更大一点，靶面较SC200AI大一点，实际开发情况也是SC2238的低照效果较SC200AI好一些


## 满阱容量（Full-Well Capacity-FWC）
一般情况下，相同分辨率的sensor，如果感光面积越大，则其单位像素的感光面积也越大，成像质量也会越好。具体探讨特殊情况，就要提到`CIS`（`CMOS Image Sensor`）器件的满阱容量（`Full-Well Capacity-FWC`），光电二极管的电容能够积累的最大电荷量称为`满阱容量`。

关于`FWC`的详细内容可以阅读《数码相机中的图像传感器和信号处理》

一款sensor的信噪比主要是由`散粒噪声`和`暗噪声`影响，散粒噪声分析可以参考“https://zhuanlan.zhihu.com/p/153079295”，在光照充足的条件即sensor低增益下，主要受散粒噪声影响，反之，在光照不足的情况即sensor高增一下，信噪比主要受暗噪声影响。

一般情况下，sensor的FWC提高了，散粒噪声会减少，即低增益下的信噪比会提升，高增益的信噪比会下降；sensor的FWC降低了了，暗噪声会减少，即高增益下的信噪比会提升，低增益的信噪比会下降。


CIS（CMOS Image Sensor） 器件的 FWC（Full Well Capacity）

## 


工业摄像头的靶面大小，厂商也会告诉你像元的大小以及分辨率，同样可以计算传感器的靶面大小。如某相机的分辨率为`2588*1940`的`500`万像素，像元大小为`2.2um`，则其传感器的尺寸为`2588*2.2=5694um=5.694mm`，宽方向为`1940*2.2=4268um=4.268mm`，即为`1/2.5”`的传感器。当然，现在的传感器像素一般是正方形的像素，如果是矩形的像素，则分别使用像素长*分辨率的长、像素宽*分辨率的宽即可。按照后面这种像素*分辨率计算得到的靶面大小是肯定准确的。




### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


