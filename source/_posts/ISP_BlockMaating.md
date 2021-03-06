---
title: 3D降噪_运动估计块运动匹配
date: 2020-11-12 10:08:00
tags: [ISP, 图像处理]
---

3D降噪_运动估计块运动匹配
<!--more-->

## 运动估计
运动估计是视频去噪技术的重要组成之一，计算相邻两帧视频序列各像素的相对运动偏移量，从而得到其运动轨迹。

点$(i,j)$和$(x,y)$分别是同一物体第`ｔ－１`帧和第`ｔ`帧的像素点。

运动估计的目的就是需要找到该点在这两帧中的运动向量`（x-i, y-j/）`。在寻找视频序列中两顿图像各像素之间的运动向量时，往往需要确定其整体、局部或者特征的对应关系，即得到图像像素之间的匹配关系，因而图像匹配是运动估计的核心内容。根据图像中匹配方式的不同，运动估计算法可分：块匹配算法、像素法、特征法和相位法等。

其中块匹配法原理简单、运算效率较高，在视频去噪领域应用比较广泛。

## 块运动匹配 

块运动匹配是当前数字图像处理领域中应用最广泛的一种运动估计方法。

首先将当前帧图像分成若干块，然后依次对每个块在参考帧（当前帧前一帧图像）的特定搜索区域中寻找与其最匹配的像素块，得到两个匹配块之间的位移即为当前诀的运动向量。以块为单位匹配，块内部的所有像素具有统一的运动向量。

在应用块匹配运动算法时，首先需要在当前顿中选取一个`n x n`大小的像素块（子块），如下图中左侧所示：

然后在参考帧中选取`N X N`的搜索窗口，并且需要保证该搜索窗口的中也与当前侦中`n x n`的像素块中也在空间坐标上重合，然后按照一定的匹配规则和搜索模式在该搜索窗口中寻找最为匹配的像素块。在块匹配运动估计算法中常用的匹配规则一般可分为两类：最小均方误差(Minimum Mean Square Deviation, MMS)
匹配和最小绝对误差(Minimum Absolute Daviation, MAD)匹配。


块运动匹配是视频去噪中最常用的匹配算法，像素法、特征法和相位法等匹
配算法因为其较高的运算复杂度并不适合在视频去噪领域进行运用，因为视频去
噪在大部分应用中归于前处理步骤中，需要较高的实时性，当算法过于复杂时将
不能满足实时性要求。但块匹配有一些列的缺点，其并不适用于缩放、旋转、变
型或者移出边界等情境中



### １）最小均方误差匹配
假设$f_c(i,j)$为当前帧中子块的中心像素，$f_p(i,j)$表示参考帧中搜索窗口内一子块的中心像素，

$$S(\delta_i,\delta_j) = \sum_{i=1}^n \sum_{j=1}^n(f_c(i,j)-f_p(i+\delta_i,j+\delta_j))^2 $$

上式中出了参考帧中特定子块与当前帧子块的均方差值，并求出参考帧变动范围内的所有子块的均方差值，比较得到最小值。

$$(\delta_{i_{0}},\delta_{j_{0}}) = argmin_{\delta_{i},\delta_{j}}S(\delta_i,\delta_j)$$

上式求使$S(\delta_i，\delta_j)$最小的参数值$(\delta_{i_{0}},\delta_{j_{0}})$。在参考帧中与当前帧子块匹配的像素块中。为，运动向量为最小绝对误差匹配最小绝对误差匹配与上述的最小均方误差匹配的操作步骤类似，只是所比较的值由均方差变成了差的绝对值。

### ２）最小绝对误差匹配
最小绝对误差匹配与上述的最小均方误差匹配的操作步骤类似，只是所比较
的值由均方差变成了差的`绝对值`。

$S(\delta_i,\delta_j) = \sum_{i=1}^n \sum_{j=1}^n(f_c(i,j)-f_p(i+\delta_i,j+\delta_j)) $ 

在运动匹配算法中．常用的匹配规则即为如上两种，相对来说最小绝对误差
匹配的复杂度更低，但是匹配的准确性不如最小均方误差匹配。


## 运动估计算法
在参考帧的搜索窗口中寻找匹配块时，搜索的模式也分成很多种。最为简单的就是全搜索方法，较为通用的有三步法，菱形搜索法。

### 全搜索方法

搜索一定范围内的所有点，注意计算最小差值和SAD，选取失真率最小的点作为最佳搜索点，该店位置和参考帧中所对应快中心像素点的位置的矢量差作为运动矢量。

1、搜索窗口选择中心点作为搜索初点，从初点开始做点向外搜索，计算每一个搜索点的SAD值；

2、比较所有点的SAD值，选择数值最小的点作为最佳匹配点。

### 三步法
三步搜索法先粗略估计最匹配子块的位置，然后逐渐精确定位找出最匹配的子块。

### 菱形搜索法
葵形搜索法采用两种搜索模板来完成匹配操作，为如上图所示的大莖形搜索
模板和小菱形搜索模板巧种。大菱形搜索模板需要计算９个子块对应的乂Ａｉ，Ｚ＼ｊ），
小菱形搜索模板需巧计算５个子块对应的Ｓ（Ａｉ

菱形搜索算法首先Ｗ搜索窗口的中也为中也，按照大菱形搜索模板完成

Ｓ（Ａｉ，ＡＤ的计算操作，若９个点当中最小的乂Ｍ，Ａｊ）不位于菱形中屯、位置，则Ｗ
Ｓ（Ａｉ，Ａｊ）所在位置为中也继续使用大菱形搜索模板完成同样操作，否则Ｗ小菱形
为模板进行计算。上图中，第一步的Ｓ（Ａｉ，Ａｊ）的最小值位于大菱形的左侧（空也
方块所示），并不为大菱形的中也，则Ｗ该空也方块为中私继续大菱形模板搜索
操作。第二步中发现该点仍不为大菱形中也（空也圆形所示），继续Ｗ该空也圆
为中屯、进行大菱形模板搜索操作。第＝步中得出Ｓ（Ａｉ，Ａｊ）的最小值出现于大菱形
中也，则按小菱形搜索模板完成最后操作，找出Ｓ（Ａｉ






### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


