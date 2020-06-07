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

### 文章目录
1 名词解释
2 功能解释
3 手机摄像头ISP是独立好还是内置好
### 名词解释
ISP 是Image Signal Processor 的简称，也就是图像信号处理器。
DSP是Digital Signal Processor 的缩写，也就是数字信号处理器。
功能解释
ISP一般用来处理Image Sensor（图像传感器）的输出数据，如做AEC（自动曝光控制）、AGC（自动增益控制）、AWB（自动白平衡）、色彩校正、Lens Shading、Gamma 校正、祛除坏点、Auto Black Level、Auto White Level 等等功能的处理。
DSP功能就比较多了，它可以做些拍照以及回显（JPEG的编解码）、录像以及回放（Video 的编解码）、H.264的编解码、还有很多其他方面的处理，总之是处理数字信号了。
个人认为ISP是一类特殊的处理图像信号的DSP。
手机摄像头ISP是独立好还是内置好
ISP是独立还是内置，对最终拍照效果并没有决定性影响，并不像PC上的独立显卡与集成显卡有那么大差异。从性能上看，这一代高通处理器内置的ISP性能已经可以跟富士通的独立ISP媲美。而各家ISP的主要处理流程都是类似的，差异也只是在于部分模块有优劣之分，比如去噪、色彩增强等。进一步来说，即便用了独立ISP，它毕竟是一个外部组件，也有可能会因为调试过程复杂，开发周期过短，开发人员难以驾驭，使得最终效果并不特别理想。
真正影响整个相机拍照效果的，还是调试，看工程师能否发挥出一块ISP真正实力。例如对ISP里面每个算法模块的优化，相关多个模块的配合等等。我们从产品上来看，有很多即便用了独立ISP，但成像效果也依然不尽人意的，也有很多虽然用了内置ISP，成像效果居然很不错的。所以这个问题，需要辩证的来看，而非依照参数配置论来粗暴的进行理解。

###[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
###[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
###[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


