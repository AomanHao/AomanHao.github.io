---
title: Lens Shading成因及相关
date: 2020-06-14 18:44:45
tags: [图像处理, ISP]
---

Lens Shading成因及相关
<!--more-->


一个监控摄像头光学处理包含以下几个部分：镜头（Lens）（定变焦镜头）、红外截止滤波片（IR-cut filter）（红外截止滤光片和蓝玻璃滤光片为主）、图像传感器（Image Sensor）和印制电路板（PCB）。其中，镜头、红外截止滤波片）和图像传感器是组成摄像头的核心部件，也是引起Lens Shading的主要部分。

![](https://img-blog.nos-eastchina1.126.net/blog/blog_camera_system_components.png)
图 分解示意图

>关于Lens Shading，一直未找到明确且合理的解释。不论是维基百科，还是百度百科，均为对该词条进行解释。但在一些博客和文献中，有人将Lens Shading称为暗角，也有将Lens Shading视为镜头阴影/镜头暗影，此外，还有称Lens Shading为亮度均匀性的。称谓很多，但没有固定且统一的说法。在文中，本人更偏向于镜头暗影的说法，即可用“暗”表示图像亮度变化引起的暗角，也能用“影”表示图像中出现的偏色现象。

一般来说，物体到lens中心的距离越远，图像越暗，呈圆形中性对称的方式递减。在算法中很容易想到用曲线映射的方式来补偿亮度

## Lens Shading
Lens Shading可细分为Luma Shading（亮度均匀性）和Color Shading（色彩均匀性）
### Luma Shading（亮度均匀性）
Luma Shading就是我们常说的暗角。图像中心区域较亮，图像边角偏暗。

![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_shadingluma.png)

### Color Shading（色彩均匀性）

Color Shading则表现在图像中心区域与四周颜色不一致，体现出来一般为中心或者四周偏色。
![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_shadingcolor.png)

## Luma Shading的成因
### 1.由摄像头本身的机械结构导致产生。
由于摄像头各模块在制作和组装的过程中，均存在一定的工艺误差，从而影响物体光线在摄像头内的传播。
### 2.由镜头（Lens）的光学特性引起。
对于整个镜头，可将其视为一个凸透镜。由于凸透镜中心的聚光能力远大于其边缘，从而导致Sensor中心的光线强度大于四周。此种现象也称之为边缘光照度衰减。对于一个没有畸变的摄像头，图像四周的光照度衰减遵循一定的衰减规律。

## Color Shading的成因
Color Shading的成因则要相对复杂的多。在分析其成因之前，需要对IR-Cut filter和Image Sensor有所了解。
### 红外截止滤波片（IR-cut filter）
红外截止滤波片位于镜头和图像传感器之间，为了消除这些投射到Sensor上不必要的光线，防止Sensor产生伪色/波纹，从而提高色彩还原性。

Sensor可以感知人眼感知不到的红外光和紫外光，因此需要使用另外的滤波片进行滤除，否则会导致红绿蓝像素点的亮度值与人眼观察到的亮度值存在较大的差异。


### 红外截止滤波片类型
红外截止滤波片主要分为干涉型、吸收型。

反红外滤光片为干涉型红外截止滤波片，即反射红外光。在可见光区域有较高的透过率，存在较低反射率，而在红外区域正好相反，反射率较高，透过率很低。但成角度拍摄照片时，红外光在IR膜上会有较大反射，经过多次反射后，被Sensor接收从而改变图像R通道的值，引起图像偏色问题。

蓝玻璃则是吸收型红外截止滤波片，对红外光有很强的吸收作用，不存在很大的反射，能在一定程度上减轻渐晕和色差问题。

### 图像传感器Image Sensor
在红外截止滤波片之后便是图像传感器，主要由相间的RGB像素感光块构成。为了使感光面积不受感光片的开口面积影响，一般会在其上方增加一层微透镜（Micro Lens），用于收集光线，提高感光度。但微透镜的主光线角CRA（Chief ray angle）值与镜头的CRA值不匹配便会导致严重的shading问题。

### Color Shading成因分析
>1.由于镜头对不同光谱光线的折射程度不同，导致入射光线中不同波长的光线落在Sensor的不同位置，从而引起Color Shading。我们都知道光的色散现象，即白光通过三棱镜后会被分解为七色光。而产生这种现象的原因就是三棱镜对不同波长光线的折射不同，从而导致不同波长光线走过的光程不同。
2.由IR-Cut filter引入。具体描述详见上文。
3.由Sensor上微透镜的CRA与镜头的CRA不匹配导致。镜头的主光线角与传感器不匹配，会使传感器的像素出现在光检测区域周围，致使像素曝光不足，亮度不够。
4.在校正Lens Shading时，由于校正参数计算不准确导致。
通常而言，摄像头在拍摄原始图像（raw）之后，会经过图像信号处理器（ISP）处理之后再呈现在用户面前。在整个ISP的pipeline中，会含有一个LSC（Lens Shading Correction）模块，用于校正镜头暗影

![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_shading1.png)
Lens Shading校正前后示意图

在实际使用中，校正后边角Noise略大，需要在边角亮度和Noise之间取一个平衡。在低光照条件下，通常会让四周的亮度达到中心亮度的70%～90%就可以了。环境色温的差异，也会导致计算出LSC gain curve有所差异，在调校IQ的过程中，会计算多种色温的LSC gain curve，然后在实际使用过程中动态的调整curve形状。

## Imatest测试
进行白平衡处理后，便可用Imatest软件对其亮度均匀性和色彩均匀性进行分析，通过Shading的测试原理，确定图像校正的好坏。
### 亮度均匀性测试原理
在整幅图像中的四角和中央分别取相同大小的区域，然后算出这些区域的亮度值，以中间区域为基准，用四角区域的亮度值和中间区域的亮度值相比，得到一个比值，这个比值越大表示边角比较亮，即Shading值 =（四角最暗处的亮度值Y/中心最亮处的亮度值)×100%，考虑到边角信噪比，选择合适的矫正参数。
### 色彩均匀性测试原理
把整幅图像等分成若干区域，然后算出这些中R/B、R/G或G/B的值，以中间区域为基准，用其他区域的比值和中间区域的比值相比，得到一个接近于1的数值，这些最终得到的比值越接近于1说明Color Shading越好。

### shading调试
镜头阴影校正（Lens Shading Correction）是为了解决由于lens的光学特性，由于镜头对于光学折射不均匀导致的镜头周围出现阴影的情况。
LSC的tuning一定要把校正图采集好，一般情况下raw图的G通道中心亮度在8bit的70%~80%之间，一般情况下需要在不同色温灯箱TL84、D65、A光源下进行校正。
注意采集的raw图不能有filcker。

LSC强度一般是可调的，因为图像边角的增益相比中心区域会很大，因此在高增益下，可以降低边角的LSC强度，避免高增益下图像边角噪声比较严重。


参考文章：https://blog.csdn.net/yxyx13120297/article/details/85206426


###[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
###[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
###[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


