---
title: 为什么图片反复压缩后普遍会变绿（安卓）
date: 2019-09-21 18:44:45
tags: [图像处理]
---

为什么图片反复压缩后普遍会变绿
<!--more-->

专业版概要：问题出在 Android 提供的压缩图片接口上，准确的说是一个 Android 里一个叫做 Skia 的库上。而这个 bug 在 2016 年 4 月中旬被修复了，如果按照 Android 的发行来看，那就是从 Android 7 (Nougat) 开始才消除这个问题。（不是百度的阴谋。（认真）前言：刚才在社区里和 StarBrilliant 等人一起研究，现在应该可以下一个精确的定论了。如他的答案所说，问题出在 RGB 色彩空间转换到 YUV 的时候。但问题不仅仅是精度下降，最大的问题是，错误的舍入（向下取整）。另外，JDCT_IFAST 方法会导致图片严重劣化：“格子状崩坏”、灰块、黑白块、画面粗糙，但是题目问的仅仅是变绿，就不在这上面浪费篇幅了。网页模拟 by StarBrilliant ：JPEGreen Simulator历史性的修复：Use libjpeg-turbo for YUV->RGB conversion in jpeg encoder · google/skia@c7d01d3 · GitHub=================================# 是谁的锅？百度贴吧是最多人批评的，而且……出事的客户端仅仅是 Android 系统上的。我后来注意到 QQ 也有这个问题，特别是上传头像。以前一直不知道为什么有一些图稍微有点绿，以为是打开了新世界的大门（x后来做了一点微小的测试，注意到百度贴吧、QQ，都会用 Android 系统提供的接口：Bitmap.compress(Bitmap.CompressFormat.JPEG, quality, outputStream);看起来都很干净……难不成是系统的问题？我自己做了一个我这辈子写的第一个 Android 的小程序（我真不敢斗胆叫做 App），模仿一个正常的应用，反复 JPEG 压缩。发现还真是那么回事。顺便完善了一下，做成了“效果拔群的绿化器”。



作者：Lion Yang
链接：https://www.zhihu.com/question/29355920/answer/119088684
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

源代码已开放：terribleGreen/MainActivity.java at master · LionNatsu/terribleGreen · GitHub（开源许可证：Apache License Version 2.0，欢迎提供 PR）现在就要说到 Android 系统到底为什么出了这个问题了。Android 系统自起诞生以来就引入了名为 Skia 的图像库（Google 自家产品），用于处理图像，其中包括把图片压缩成 JPEG（平时说的 JPG）。而 Skia 又是调用 libjpeg-turbo 来实现真正的压缩过程的。为了达到更好的压缩效果，JPEG 算法本身，将通常屏幕上表示颜色的 RGB（红绿蓝）数值，转换为 YUV 数值（亮度，蓝色分量，红色分量）。正常情况下这个算法是轻微有损的。但是 Skia 不走寻常路，将这个变换算法的各个常数复制到自己的代码里（当然是合法地），然后降低了精度，以达到更高的速度（专业准确地说，从 16 位定点数，降低到了 8 位定点数），这导致了更大的损伤。最可怕的是……在进行这个变换运算的最后一步，需要除以 256，而代码中，采用了右移操作代替除法以提高执行速度（看不懂可以跳过）：int  y = ( CYR*r + CYG*g + CYB*b ) >> CSHIFT;
int  u = ( CUR*r + CUG*g + CUB*b ) >> CSHIFT;
int  v = ( CVR*r + CVG*g + CVB*b ) >> CSHIFT;
// C?? 是已经扩大到 2^CSHIFT 倍的矩阵参数（-0.5 ~ 0.5），CSHIFT = 8
这个操作并没有什么问题，数学意义就是除以 256。但是问题出在：1、直接截断了小数部分，等价于 trunc()。如果符号数是用补码实现的。即全部往负数方向取整。如：1.2 → 1； 3.9 → 3；0.0 → 0；-5.1  → -6.2、较冒险的符号数移位：根据规范的定义，对符号数（可正可负的数）使用移位的效果将由具体的编译器明确定义决定（implementation-defined）。因为移位是一个符号无关的操作，对符号数移位将依赖于符号数的具体表现形式。而这个形式 C++ 没有给出一个限定，由具体的编译器自行决定，对于非“补码”（2's complement）的情况结果可能并不是所期待的那样数值整除2的幂。这里假设了编译器都能“正确”理解为整除。=================================# YUV 值向负方向取整导致什么？复习一下 YUV 的定义：Y，亮度，0.0 ~ 1.0；U，或者叫做  Cb，蓝色分量，-0.5 ~ 0.5；V，或者叫做 Cr，红色分量，-0.5 ~ 0.5。在 Skia 的代码里，YUV 三个值均对应到 0~255 的范围。因为向下取整，所以误差在 1 一个单位以内：0/256 到 1/256 也就是，YUV 三个值都变小 0.00% 到 0.39% 这个范围。看一下 U, V 这两个决定颜色的值是如何变化的：<img src="https://pic3.zhimg.com/50/6d51626208ef196b3332f024361dba19_hd.jpg" data-caption="" data-size="normal" data-rawwidth="480" data-rawheight="480" class="origin_image zh-lightbox-thumb" width="480" data-original="https://pic3.zhimg.com/6d51626208ef196b3332f024361dba19_r.jpg"/>（图片来自 Tonyle, Wikimedia Commons, File:YUV UV plane.svg）显然，YUV 值向负方向取整，结果是呼之欲出的：变暗，变绿。（这里的变暗是 YUV 里的 Y 减小，并不完全准确对应人类视觉的明暗概念）这个错误的舍入，使得：所有在 0 ~ 255 范围内非整数的 YUV 值都受到影响。那么某个像素被舍入到整数之后，下一次再压缩 JPEG 应该会好一些吧？很不幸的是，随之而来的大量其他有损操作（比如 DCT 变换之后滤去高频）又会使得 YUV 值发生变化：如果发生变化，假设随机产生关于 0 对称的误差，那么实际上也有 50% 的机率使得这个数值 -1，因为只要比原来的值小，都会被向下舍去。这使得，图片随着 Skia 缺陷的色彩空间变换算法反复压缩，越来越绿。=================================## 假如我们是 Skia 开发者，如何修复这个问题？（阅读本节需要 C/C++ 常识）交回给 libjpeg-turbo 库自己来做色彩空间变换。这也正是本文开头提到的那个历史性的修复具体做的：把原本 Skia 库 YUV 转换代码全部删掉了，把这个过程留给整个过程最底层的 libjpeg-turbo 库自己来做，并且用默认的 JDCT_ISLOW 方法代替 JDCT_IFAST 方法，那么自然就没这个问题了。注：libjpeg-turbo 是个运用极其广泛的库。可以说，基本上电脑上手机上能见到的 JPEG 压缩的地方用的一般都是 libjpeg-turbo。（iOS 应该也是吧？我没有苹果设备抱歉……Adobe 公司的魔法可能是另一回事）如果不删除呢？自己捣鼓：* 本节所提到的代码以及示例图片可以在这里找到：GitHub - LionNatsu/greenError: Discover the reason how `terribleGreen`(my another repo.) works on Android.首先我们要模拟一个 Skia 的 libjpeg-turbo 操作（略），然后，在把图片递交给 libjpeg-turbo 之前，把色彩空间像 Skia 一样，做一个变换（矩阵数据完全与 Skia 相同）。我们所要做的修复就是，把运算改成能够对数字进行合理四舍五入的运算：int R=i[0], G=i[1], B=i[2];

#if 1 // Shift or float-divide (shift in Skia)
  int Y = (R*CYR + G*CYG + B*CYB) >> CSHIFT;
  int U = (R*CUR + G*CUG + B*CUB) >> CSHIFT;
  int V = (R*CVR + G*CVG + B*CVB) >> CSHIFT;

  o[0] = Y;
  o[1] = U + 128;
  o[2] = V + 128;
#else
  double Y = (R*CYR + G*CYG + B*CYB) / pow(2, CSHIFT);
  double U = (R*CUR + G*CUG + B*CUB) / pow(2, CSHIFT);
  double V = (R*CVR + G*CVG + B*CVB) / pow(2, CSHIFT);

  o[0] = round(Y);
  o[1] = round(U + 128);
  o[2] = round(V + 128);
#endif
这里我把原版操作和修正版操作都写在一起了，把 #if 1 改成 #if 0 即可切换。（为什么我要说这些= =）示例：左边为原版 Lena 酱，右边均为压缩质量设置为 80%，重复 30 次。完全 Skia 原版效果（即 Android 的）：8-bit 变换，移位除法，JDCT_IFAST 方法。<img src="https://pic2.zhimg.com/50/2b308422edc48a435f67bae3b0a069d2_hd.jpg" data-caption="" data-size="normal" data-rawwidth="1024" data-rawheight="512" class="origin_image zh-lightbox-thumb" width="1024" data-original="https://pic2.zhimg.com/2b308422edc48a435f67bae3b0a069d2_r.jpg"/>画质严重劣化，色彩偏绿。不辣眼睛修正效果：8-bit 变换，移位除法，JDCT_FLOAT 方法。<img src="https://pic3.zhimg.com/50/1f6ee2471aa3f6105805102e6be8bed5_hd.jpg" data-caption="" data-size="normal" data-rawwidth="1024" data-rawheight="512" class="origin_image zh-lightbox-thumb" width="1024" data-original="https://pic3.zhimg.com/1f6ee2471aa3f6105805102e6be8bed5_r.jpg"/>可以看到关闭 JDCT_IFAST 之后画面细腻了。继续修复舍入漏洞的效果：8-bit 变换，正常舍入的除法，JDCT_FLOAT 方法。<img src="https://pic3.zhimg.com/50/33f75a87653da3d65145ab17e56b139d_hd.jpg" data-caption="" data-size="normal" data-rawwidth="1024" data-rawheight="512" class="origin_image zh-lightbox-thumb" width="1024" data-original="https://pic3.zhimg.com/33f75a87653da3d65145ab17e56b139d_r.jpg"/>可以看到色彩偏绿的问题被正确四舍五入修正了。回归原版 libjpeg-turbo 的压缩效果（现在的新版 Android）：16-bit 变换，正常舍入的除法，JDCT_FLOAT 方法。（其实原版是JDCT_ISLOW，但差别不大）<img src="https://pic4.zhimg.com/50/59d5d1378de925f5049b892a9818aec0_hd.jpg" data-caption="" data-size="normal" data-rawwidth="1024" data-rawheight="512" class="origin_image zh-lightbox-thumb" width="1024" data-original="https://pic4.zhimg.com/59d5d1378de925f5049b892a9818aec0_r.jpg"/>比起 8-bit 少了很多色斑，因为数字范围更大，不溢出了。

此资料部分转载自网络，仅供学习参考。


#[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
#[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
#[我的GitHub主页，欢迎访问](https://github.com/AomanHao)


