---
title: 10句话读懂图像频域滤波（转载）
date: 2019-09-21 18:44:45
tags: [图像处理]
---

Raw数据相关概念
<!--more-->


今天的图像处理依靠各类方便易用的工具箱与函数库似乎已然成为上手就能用的应用科学。但没有那种算法是普适的，知其所以然才能真正理解原理，深刻的理解才能针对具体应用行成独到见解。图像处理是信号与信息处理学科的分支，图像滤波的理论当然得从信号与系统说起。尽管很多文献都有详细的论述，但如果你对LSI系统、空间卷积、二维傅里叶变换、空域与频域、滤波与变换的理论概念虽耳熟能详但仍一知半解，本文将尽力用简单的文字将这些关系屡屡清楚，总结并告诉我们一些不可不知的图像频域滤波处理基本理论。

## 10句话读懂图像频域滤波基本理论
### 1  数字图像信号为离散二维或三维信号。


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_1)


二维灰度图像                                                                  三维视频图像

图像处理很简单，给一幅输入图像x得到一幅输出图像y(n1,n2)，通常将这个过程视为一个二维信号处理系统T：


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_1.2)

线性移不变(LSI)系统有很多优良的性质，这类系统必须同时具有线性与空间移不变性：输出对任意输入都满足均匀性与叠加性（合称线性），输出与系统的坐标原点位置无关（移不变性）

![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_1.4)


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_2)


单位冲激函数δ(n1,n2)通过LSI系统，输出为系统的冲激响应h(n1,n2)：


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_3)

想得到输出图像其实不难：若已知LSI系统的冲激响应h(n1,n2)，则输出图像=输入图像与冲激响应的二维卷积：



![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_4)

傅里叶很牛，可将图像信号从空域x(n1,n2)变到到频域X(ω1,ω2)，也可以将图像信号从频域变回空域，(ω1,ω2)分别表示频域中的垂直与水平频率


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_5)
![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_6)



 LSI系统冲激响应h(n1,n2)的傅里叶变换就是该系统的频率响应H(ω1,ω2)，它给出了系统在频点(ω1,ω2)处的响应特性：


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_7)

有了卷积定理，一切变得简单：LSI系统在空域的二维卷积运算，等于该系统在频域的乘积运算：



![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_8)

### 结论:频域滤波就是设计合适的LSI系统频谱响应H(ω1,ω2)，即可实现对输入图像中某些频率的放大、衰减或不通过（拒绝）：


![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_9)

那么问题来了，到底怎么分析呢(｡･∀･)ﾉﾞ~图像滤波中所用的滤波核或模板就是系统的冲激响应h，每个滤波核都已其特定的频率响应函数H，例如：

          
 

低通滤波器：频率响应曲线中间凸、四周低表示低频部分系数高：低频分量通过，高频被抑制

       ![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_10)        

高通滤波器：频率响应曲线四周高、中间凹表示高频部分系数高：高频分量通过，低频被抑制



![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_11)

P.S. 如果还想更进一步，请参考博文“如何构造频域滤波器——图像频域滤波的信号与系统基本理论”。



版权声明：本文为CSDN博主「iracer」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/iracer/article/details/49311463



![](https://img-blog.nos-eastchina1.126.net/blog/blog_filter_1)
声明：



此资料部分转载自网络，仅供学习参考。


#[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
#[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
#[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


