---
title: Camera ISP与DSP的区别
date: 2020-06-05 18:44:45
tags: [图像处理]
---

Camera ISP与DSP的区别
<!--more-->
在介绍Camera ISP和DSP区别前，我们先看看Camera的工作流程
![](https://img-blog.nos-eastchina1.126.net/blog/blog_camera-isp-flow.png)

![](https://img-blog.nos-eastchina1.126.net/blog/blog_camera_system_components.png)

拍摄景物通过镜头，将生成的光学图像投射到传感器上，然后光学图像被转换成电信号，电信号再经过模数转换变为数字信号，数字信号经过DSP加工处理，再被送到电脑中进行处理，最终转换成手机屏幕上能够看到的图像。

数字信号处理器DSP(DIGITAL SIGNAL PROCESSING)功能：主要是通过一系列复杂的数学算法运算，对数字图像信号参数进行优化处理，并把处理后的信号通过USB等接口传到PC等设备。DSP结构框架:
```
ISP(image signal processor)(图像信号处理器)
JPEG encoder(JPEG图像解码器)
USB device controller(USB设备控制器)
```

## 名词

>`ISP` 是`Image Signal Processor` 的简称，也就是图像信号处理器。
`DSP`是`Digital Signal Processor` 的缩写，也就是数字信号处理器。

## 功能
ISP一般用来处理`Image Sensor`（图像传感器）的输出数据，如做`AEC`（自动曝光控制）、`AGC`（自动增益控制）、`AWB`（自动白平衡）、色彩校正、`Lens Shading`、`Gamma` 校正、祛除坏点、`Auto Black Level`、`Auto White Level` 等等功能的处理。

DSP功能就比较多了，它可以做些拍照以及回显（JPEG的编解码）、录像以及回放（Video 的编解码）、H.264的编解码、还有很多其他方面的处理，总之是处理数字信号了。

ISP是一类特殊的处理图像信号的DSP。


###[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
###[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
###[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


