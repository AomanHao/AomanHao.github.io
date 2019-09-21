---
title: 图像处理_ISP_坏点矫正
date: 2019-07-08 21:39:40
tags: [图像处理, ISP]
toc: true
mathjax: true
---

图像处理_ISP_坏点矫正
<!--more-->

## 1 坏点介绍
图像坏点(Bad pixel) : 图像传感器上光线采集点(像素点)所形成的阵列存在工艺上的缺陷，或光信号进行转化为电信号的过程中出现错误，从而会造成图像上像素信息错误，导致图像中的像素值不准确，这些有缺陷的像素即为图像坏点。

由于来自不同工艺技术和传感器制造商，尤其对一些低成本、消费品的sensor来说，坏点数会有很多。另外，sensor在长时间、高温环境下坏点也会越来越多，从而破坏了图像的清晰度和完整性。坏点校正的目的就是修复这类问题，通常坏点分为一下两种：

        (1) 静态坏点：分为静态亮点和静态暗点。
             静态亮点：一般来说像素点的亮度值是正比于入射光的，而亮点的亮度值明显大于入射光乘以相应比例，并且随着曝光时间的增加，该点的亮度会显著增加；
             静态坏点：无论在什么入射光下，该点的值接近于0;
        (2) 动态坏点：在一定像素范围内，该点表现正常，而超过这一范围，该点表现的比周围像素要亮。与sensor 温度、增益有关，sensor 温度升高或者gain 值增大时，动态坏点会变的更加明 显；
## 2 坏点校正成因
　　 为什么图像处理的过程中需要做坏点校正，而且坏点校正(DPC)通常在ISP的pipeline靠前位置？主要有如下原因：

        (1) 如果图像中存在坏点的话，ISP后续进行插值和滤波处理时，会影响周围的像素点值，因此需要在插值和滤波之前对坏点进行校正 ;
        (2) 图像存在坏点比较多或动态坏点很多的情况下，会造成图像的边缘出现伪色彩的情况，这种现象不但影响图像的清晰度，而且会影响边缘的色彩;
        (3) 坏点也会造成图像部分pixel闪烁的现象;
## 3 坏点校正策略
图像的坏点校正(DPC)通常在Bayer域(灰度图原理一致)进行。若Bayer域为R/G/B三通道，则分别进行坏点校正;若Bayer域为RGBIR格式，则分别对R/Gr/Gb/B四通道独立进行。动态坏点校正和静态坏点校正是两个相互独立的过程，可以同时开启，也可以只开启一个，视需要设置。

        静态坏点校正：基于已有的静态坏点表，比较当前点的坐标是否与静态坏点表中的某个坐标一致，若一致则判定为坏点，然后再计算校正结果对其进行校正。一般情况下，每个sensor的坏点都不一样，需要sensor厂商给出每个sensor的静态坏点表，但是出于成本的考虑，很多sensor厂商并没有给出，而用户校正的话只能一个一个对其进行校正，因此对于一些低成本的sensor，静态坏点校正的实用性不是很强。另外，由于在硬件设计的时候需要占用大量的memory，考虑到芯片面积以及一些其他原因，因此静态坏点有大小的限制，不可以无限制的校正。

        动态坏点校正：可以实时的检测和校正sensor 的亮点与暗点，并且校正的坏点个数不受限制。动态坏点校正相对静态坏点校正具有更大的不确定性。动态dpc可以分为两个步骤，分别为坏点检测和坏点校正。
## 4 源码实现(Matlab Version)
该算法是动态坏点校正策略实现，算法使用梯度百分比的方式去检测坏点，检测到坏点之后通过中值滤波进行坏点校正，最终通过alpha混合的方式计算出最终的计算结果。代码如下：   

```
close all;
clear;
clc;
%% variable
dp_slope = 0.02;
dp_thresh = -0.3;
r=3;        %Stencil radius

%% read raw image
% x = 0:255;
% y = dp_slope * x + dp_thresh;
% y(y<0) = 0;
% y(y>1) = 1;
% figure,
% plot(0:255,y)
% axis([0 255 0 1.5])

[filename, pathname] = ...
    uigetfile({'*.raw'}, 'select picture');
str = [pathname filename];
fp = fopen(str, 'rb');
[X,l] = fread(fp, [1920,1080], 'uint16');
fclose(fp);
img = uint8(X/16)';
[height, width] = size(img);
img_correct = zeros(height, width);

%% Image edge extension
imgn=zeros(height+2*r,width+2*r);
imgn(r+1:height+r,r+1:width+r)=img;
imgn(1:r,r+1:width+r)=img(1:r,1:width);                 
imgn(1:height+r,width+r+1:width+2*r+1)=imgn(1:height+r,width:width+r);    
imgn(height+r+1:height+2*r+1,r+1:width+2*r+1)=imgn(height:height+r,r+1:width+2*r+1);    
imgn(1:height+2*r+1,1:r)=imgn(1:height+2*r+1,r+1:2*r);

%% dp algorithm
for i = r+1:height-r
    for j = r+1:width-r

        img_r = imgn(i-r:2:i+r, j-r:2:j+r);
        data_r_center = img_r(r, r);
        data_r_diff(1:r+1, 1:r+1) = abs(img_r - img_r(r,r));
        data_r_sort = sort(img_r(:));
        data_r_median = data_r_sort(r*2+1);
        data_r_detect = data_r_diff * dp_slope + dp_thresh;
        data_r_detect(data_r_detect < 0) = 0;
        data_r_detect(data_r_detect > 1) = 1;
        data_r_judge = sum(sum(data_r_detect > 0));
        data_r_weight = sum(sum(data_r_detect)) / data_r_judge;
        if i-r == 18 && j-r == 43
            a = 1;
        end
        if data_r_judge >= 7
            data_r_correct = data_r_median * data_r_weight + (1-data_r_weight) * data_r_center;
        else
            data_r_correct = data_r_center;
        end
        img_correct(i-r, j-r) = data_r_correct;

    end
end

%% show
figure,imshow(uint8(img));
figure,imshow(uint8(img_correct));
```

[参考文章](https://www.cnblogs.com/qiqibaby/p/8597057.html)