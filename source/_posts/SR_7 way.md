---
title: 【阅读笔记】Seven ways to improve example-based single image super resolution
date: 2021-05-14 10:08:00
tags: [ISP, 图像处理, Paper]
---

【阅读笔记】Seven ways to improve example-based single image super resolution
<!--more-->


## 论文信息

【Seven ways to improve example-based single image super resolution】-Radu Timofte, 2016, CVPR

[论文链接](https://www.cv-foundation.org/openaccess/content_cvpr_2016/html/Timofte_Seven_Ways_to_CVPR_2016_paper.html)

提出来了提升example-based single image SR的七个技巧。



## 前置内容



数据集：Train91, Set5, Set14, B100, L20

对比方法:Yang, Zeyde, ANR, A+, SRCNN

Yang：即Sparse Coding（SC），图像特征块由原子字典和原子稀疏矩阵表示

> Image Super-Resolution via Sparse Representation-Yang
>
> image super-resolution as sparse representation of raw image patches-Yang

Zeyde：通过使用K-SVD有效地学习字典和使用正交匹配追求(OMP)进行稀疏解，改进了Yang方法

> On Single Image Scale-Up Using Sparse-Representations  zeyde

ANR：在SC方法上改进，在训练阶段对LR字典每一个原子额外计算一团邻居原子，计算对应HR字典的邻居原子，求LR邻居原子团-HR邻居原子团的投影矩阵。在重建阶段用投影矩阵乘以输入LR图像特征块进行重建HR图像特征块

> TIMOFTER, D E V , G O O LLV. Anchored Neighborhood Regression for Fast Example-Based uper Resolution [ C/ OL]// IEEE International Conference on Computer Vision 2013

A+：是对ANR的改进，改进了寻找投影矩阵时寻找邻居的方法。ANR是在LR字典找原子的邻居原子，A+是在LR训练样本集中找LR字典每一个原子的邻居特征样本

> TIMOFTER, SM E T V D, GOOLLV. A +: Adjusted Anchored Neighborhood Regression for Fast Super-Resolution[C/OL]// Asian Conference on ComputerVision, Singapore, 2014

 

## 改进内容项

### 1、Augmentation of trainning data

　　即增加训练阶段的数据，训练数据的增加可以有效提升重建质量。有两种途径:

1). scaling the training images 缩放训练图像
2). considering the flippped and rotated versions of the training data/patches训练图像旋转、训练图像反转。

 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Fig2.png)

图2展示旋转90、180、270，翻转后90、180、270度

如果我们将原始图像旋转90，180，270度，我们得到了很多张没有改变内容的图像。对其他旋转角度使用插值可能会损坏边缘并影响性能。



 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Fig3.png)

图3展示LR-HR训练图像数量的影响

1、数量越大对PSNR提升有效果

2、锚点数量增加，PSNR也增加



### 2、Large dictionary and hierarchical search

　　字典大小增加，稀疏表示方法的效果一般也会增加。在A+中，anchor越多，误差越小，字典变大字典查找速度会慢。因此为了提高搜索与输入patch最近的anchor效率，提出了hierarchical search

其主要思想就是将N个anchors（锚点）使用k-means分为$\sqrt{N}$类，每一类都一个质心，每个质心分给$c\sqrt{N}$个相关的anchors，搜索先在最近的质心处搜索，然后在$c\sqrt{N}$个相关的anchors处搜索



 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Fig5.png)

图5展示搜索速度的优化

字典规模越大，查找字典速度越慢，优化了搜索结构后（蓝线），查找字典的时间能得到改善





### 3、Back projection

　　让output退化后的图像与输入LR尽可能一致，类似输出得到的HR图像进行下采样在和输入的LR图像比较，如果误差较大，信息反馈后优化重建HR图像。下一次重建HR图像与输入LR图像的误差要更小



 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Tab1.png)

表1展示结合迭代反向投影的算法对比效果

### 4、Cascade of anchored regressors

小的放大倍数（x2，x3）SR结果比较准确，大的放大倍数（x4，x8）SR效果比较一般，因此有人提出逐步放大，即使用相同的特征和参数，阶梯状的输出模型。将前一阶段的输出作为LR图像输入和每个阶段的HR图像，而每个阶段使预测更接近目标HR图像。



 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Fig6.png)

图6展示多层级联效果



 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Tab2.png)

表2展示1-4层级联的算法对比效果



​	级联的效果会变好，会增加计算时间



### 5、Enhanced prediction

　　重建阶段对输入LR图像进行裁剪（还是缩放）、旋转和翻转，得到8张LR图像。对每一张都进行一次SR，对重建结果取平均值得到一张HR结果。



实验结果表明能有效提升PSNR



### 6、Self-similarities

　　一般的字典学习相当于建立了external dictionary，文中提出可以利用internal dictionary。当然如果把internal dictionary和external dictionary结合起来肯定效果会更好。

> 外部字典：训练过程提供的过完备字典
>
> 内部字典：根据输入LR图像的大小和纹理复杂性构建内部字典

具有高几何规则的城市HR图像，具有内部字典的结果比外部更好，内部字典的构建在重建过程会耗时间，考虑提升效果与计算量的权衡选择吧



 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Fig7.png)

图7展示字典改进，联合internal dictionary和external dictionary效果更好



### 7、Reasoning with context

　　利用上下文信息来提高超分的效果，对于每一个anchor，不止训练一个regressor，而是训练4个context specific regressors.对于每一个LR patch，首先是匹配anchors，然后这些邻近的context specific regressors用来获得HR output。

 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Tab4.png)

表4展示结合上下文信息的效果，效果提升不明显





## 结合改进提出Improved A+



简单总结

> Augmentation of training data (A)增加训练数据
>
> Large dictionary and hierarchical search (H) 大型字典和层次结构搜索
>
> Reasoning with context (R)利用上下文信息
>
> Cascade of core SR method（c）级联   略微耗时，效果提升明显
>
> Enhanced prediction (E)旋转和翻转 略微耗时，效果提升明显



> Self-similarities (S) 很耗时，效果提升不明显
>
> Back projection (B) 迭代反向投影，IBP， 效果提升不明显



其中，使用(A、H、R、C、E)这几项改进提出**Improved A+**方法，(C)和(E)以增加计算时间为代价。





 ![](https://img-blog.nos-eastchina1.126.net/blog2021/blog_SR_7Way_Fig8.png)

图8展示这几个方法的质量提升程度



每项改进都有效果，并且用在别在对比算法上也能提升重建效果，还是那句要权衡计算量和效果来结合改进项





参考文章：

1、https://www.cnblogs.com/wyboooo/p/13377024.html

Seven ways to improve example-based single image super resolution【阅读笔记】