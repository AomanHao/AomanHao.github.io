---
title: 图像超分辨率-数据集和评价标准
date: 2021-05-12 10:08:00
tags: [图像处理, 超分辨率]
---
 
图像超分辨率-数据集和评价标准
<!--more-->

## 图像数据



  | Dataset      | Amount |  
  | ------------ | ------ | 
  | Set5         | 5      | 
  | Set14        | 14     |      
  | Urban100     | 100    |      
  | BSDS300      | 300    |      
  | BSDS500      | 500    |      
  | DIV2K        | 1000   |      
  | General-100  | 100    |     
  | L20          | 20     |      
  | Manga109     | 109    |      
  | OutdoorScene | 10624  |      



数据库链接：
http://vllab.ucmerced.edu/wlai24/LapSRN/ 

### 插值算法
部分数据集包含HR-LR图像对，其他的只提供HR图像，通过对HR图像`BiCubic`插值得到LR图像。



基于插值的上采样方法仅基于其自身的图像信号来提高图像分辨率，而不带来更多的信息。重建结果容易带来噪声放大、模糊结果。



为了克服插值方法的缺点，学者提出基于深度学习的上采样层，应用在 post-upsampling framework，在端与端学习的网络末端

![](D:\杂货文件夹\文章MD\图像附件\上采样\Post-up.png)

### Transposed Convolution Layer

通过补0并卷积来扩展图像

1、图像扩展，需要添加的像素补0；

2、使用3X3的内核进行卷积；



![](D:\杂货文件夹\文章MD\图像附件\上采样\UPSam_Transposed.png)

### Sub-pixel Layer

端到端深度学习的上采样层方式，也被SR模型广泛使用

![](D:\杂货文件夹\文章MD\图像附件\上采样\UPSam_Sub-pixel.png)

1、设定上采样因子即放大倍数 S;

2、若对特征图放大S倍，则生成 S^2个相同尺寸的特征图；

3、将S^2个特征图拼接成一个原图放大S倍的大图



## PQ评价标准

### PSNR

Peak signal-to-noise ratio (PSNR)是应用广泛的质量评估标准
$$
PSNR = 10*log_{10}( \frac{L^2}{\frac{1}{N}\sum_{i=1}^N (I(i)-J(i))^2} )
$$
其中，$N$表示像素数，$I$表示原始图像，$J$表示重建图像，针对 uint8 数据，最大像素值为 255；针对浮点型数据，最大像素值为 1

`PSNR`与`MES`强相关，对比图像质量越高，`PSNR`值越大

### SSIM
结构相似性Structural Similarity Index (SSIM) 有效评价图像的视觉质量，广泛应用图像压缩、超分辨率等算法评价



![](D:\杂货文件夹\文章MD\图像附件\SSIM评价标准.png)

### 主观评价

### 基于深度学习的IQA质量评价模型
