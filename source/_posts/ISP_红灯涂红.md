---
title: CMOS sensor HCG模式？
date: 2020-09-05 10:08:00
tags: [图像处理]
---

CMOS sensor HCG模式？
<!--more-->

High conversion gain吗？这个要High和low配合去做才会有动态范围的优势，就把它当成Gain就行，一个high gain，一个low gain，可以拼出来一个HDR的图像。我60fps全尺寸High+Low，经过ISP支持可以出30fps HDR拼好的图像。High Gain用在暗处，Low Gain用在亮处。（uV/e-）

作者：Shingo
链接：https://www.zhihu.com/question/265887206/answer/312331088
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

是 pixel level原生的gain（可从LCG切换），相比 ramp adc的gain，有更好的snr，不过不能线性调节，是固定的，需要在gain在一定范围以上与ADC的gain做重新分配

会影响动态单位。hcg就是增大放大倍数，adc的输入是范围是固定的。
然而hcg就是在弱光下用的，一般也不会超过动态范围。
发布于 2018-01-21


###[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
###[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
###[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


