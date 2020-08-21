---
title: ISP之黑电平矫正
date: 2020-08-19 10:08:00
tags: [图像处理, ISP]
---

ISP之黑电平矫正
<!--more-->


## 黑电平定义
CMOS传感器采集的信息经过一系列转换，最后生成原始RAW格式数据，RAW数据每个像素点只有对应颜色的灰度信息。

　　黑电平（Black Level Correction）：即黑色数据的最低电平值，通常指感光图像数据为0时对应的sensor信号电平值。

## 黑电平成因

黑电平形成的原因有多种，主要的形成原因如下面两点：

(1) CMOS传感器采集的信息经过一系列转换生成原始RAW格式数据。以8bit数据为例，单个pixel的有效值是0~255，但是实际AD芯片（模数转换芯片）的精度可能无法将电压值很小的一部分转换出来，因此，sensor厂家一般会在AD的输入之前加上一个固定的偏移量，使输出的pixel value在5（非固定）~255之间，目的是为了让暗部的细节完全保留，当然同时也会损失一些亮部细节，由于对于图像来说，我们的关注度更倾向于暗部区域，ISP后面会有很多增益模块（LSC、AWB、Gamma等），因此亮区的一点点损失是可以接受的。

(2)  sensor的电路本身会存在暗电流，导致在没有光线照射的时候，像素单位也有一定的输出电压，暗电流这个东西跟曝光时间和gain都有关系，不同的位置也是不一样的。因此在gain增大的时候，电路的增益增大，暗电流也会增强，因此很多ISP会选择在不同gain下减去不同的bl的值。

如多sensor输出raw数据中附加的黑电平值，需要在ISP最前端去干净。如果不去干净，干扰信息会影响后端ISP各模块的处理，尤其会导致AWB容易不准，出现画面整体偏绿或者整体偏红现象。

## 黑电平校正算法

一般BLC模块会放在ISP比较靠前的位置。有些sensor会在sensor内部集成BLC的模块，那么此时ISP里的BLC模块只做微调即可。如下图：

![](https://img-blog.nos-eastchina1.126.net/blog/blog_camera-isp-flow.png)


目前主流黑电平校正方案有两种：

(1) 由于硬件设计人员在设计BLC模块时需要考虑效果和成本，因此目前市场上使用的ISP一般采用的方法是在sensor输出的图像上减去一个固定数值。

1、固定数值，对RGB各通道可以是一样，也可以是不一样；
2、固定数值，可以根据增益不同选择不同的数值。

(2) 利用黑电平随温度和gain的漂移曲线，利用一次函数的方式进行校正，但是对于不同sensor，漂移曲线不一样，因此该方案没有作为通用方案

## 黑电平调整
黑电平减多变绿，减少变红， 黑电平调整导致r/b gain 不平衡
![测试图像](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/Blog_Demosaic_kodim19.png)
图、kodim19测试图像

![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_blc_i_R.png)
图、kodim19 偏红（黑电平减的少）

![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_blc_i_G.png)
图、kodim19 偏绿（黑电平减的多）


## 黑电平受增益温度等因素影响 
1、黑电平跟增益相关，可以根据不同的增益调整不同黑电平数值。      

2、黑电平受到温度的影响较大，高温下的黑电平会飘，若sensor有温度传感器，最好实时重置sensor的BLC功能。

参考：https://www.cnblogs.com/qiqibaby/p/8591036.html
 


### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


