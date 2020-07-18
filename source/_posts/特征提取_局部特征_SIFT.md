---
title: 特征提取——局部特征-SIFT算法尺度不变性的理解
date: 2018-07-16 09:39:40
tags: [图像处理, 特征提取]
mathjax: true
toc: true
---

特征提取——局部特征

<!--more-->
[参考这个就完事了](https://blog.csdn.net/ws_20100/article/details/51122322)

### 局部特征

不管原图尺度是多少，在包含了所有尺度的尺度空间下都能找到那些稳定的极值点，这样就做到了尺度不变！
>高斯函数是唯一可行的尺度空间核
比如说一张美女图片，想要框出帽子的信息，图像尺寸小时框要这么大，图像尺寸大时，框也要相应调大：

尺度不变性：
$$L(x,y,σ)=G(x,y,σ)*I(x,y)$$

为了有效的在尺度空间检测到稳定的关键点，提出了高斯差分尺度空间（DOG scale-space）。利用不同尺度的高斯差分核与图像卷积生成。构造高斯差分尺度空间(DOG scale-space): 
$$D(x,y,σ)=(G(x,y,kσ)-G(x,y,σ))*I(x,y)=L(x,y,kσ)-L(x,y,σ)$$

σ 是尺度坐标。σ大小决定图像的平滑程度，大尺度对应图像的概貌特征，小尺度对应图像的细节特征。大的σ值对应粗糙尺度(低分辨率)，反之，对应精细尺度(高分辨率)。

旋转不变性：
```
Lowe采用的方法是在生成描述子前将图片旋转到一个特定的方向上，这个方向是根据图片内容得到的，具体就是用在某个半径大小的圆内的像素的梯度信息。
sigma取的是1.5*<scale of key point>,r取3*sigma
将图片先旋转到主方向，这个方向由于是用相同的信息得到的，所以总是指向同一方。
```

抵抗噪声：
```
DoG得到极值点后，去除低对比度的点的点舍弃,在确定主方向和生成描述子时都将梯度模值加进行加权，即是噪声影响了部分点，经过加权统计会抑制变化，不会对全局造成太大影响
```

[参考文章](https://blog.csdn.net/u014485485/article/details/78681086?locationNum=1&fps=1)




### OpenCV代码
```
// opencv_empty_proj.cpp : 定义控制台应用程序的入口点。
//
 
#include "stdafx.h"
#include <opencv2/opencv.hpp>
#include <opencv2/features2d/features2d.hpp>
#include<opencv2/nonfree/nonfree.hpp>
#include<opencv2/legacy/legacy.hpp>
#include<vector>
using namespace std;
using namespace cv;
 
int _tmain(int argc, _TCHAR* argv[])
{
    const char* imagename = "img.jpg";
  
    //从文件中读入图像
    Mat img = imread(imagename);
    Mat img2=imread("img2.jpg");
 
    //如果读入图像失败
    if(img.empty())
    {
            fprintf(stderr, "Can not load image %s\n", imagename);
            return -1;
    }
    if(img2.empty())
    {
            fprintf(stderr, "Can not load image %s\n", imagename);
            return -1;
    }
    //显示图像
    imshow("image before", img);
    imshow("image2 before",img2);
     
 
    //sift特征检测
    SiftFeatureDetector  siftdtc;
    vector<KeyPoint>kp1,kp2;
 
    siftdtc.detect(img,kp1);
    Mat outimg1;
    drawKeypoints(img,kp1,outimg1);
    imshow("image1 keypoints",outimg1);
    KeyPoint kp;
 
    vector<KeyPoint>::iterator itvc;
    for(itvc=kp1.begin();itvc!=kp1.end();itvc++)
    {
        cout<<"angle:"<<itvc->angle<<"\t"<<itvc->class_id<<"\t"<<itvc->octave<<"\t"<<itvc->pt<<"\t"<<itvc->response<<endl;
    }
 
    siftdtc.detect(img2,kp2);
    Mat outimg2;
    drawKeypoints(img2,kp2,outimg2);
    imshow("image2 keypoints",outimg2);
 
 
    SiftDescriptorExtractor extractor;
    Mat descriptor1,descriptor2;
    BruteForceMatcher<L2<float>> matcher;
    vector<DMatch> matches;
    Mat img_matches;
    extractor.compute(img,kp1,descriptor1);
    extractor.compute(img2,kp2,descriptor2);
 
 
    imshow("desc",descriptor1);
    cout<<endl<<descriptor1<<endl;
    matcher.match(descriptor1,descriptor2,matches);
 
    drawMatches(img,kp1,img2,kp2,matches,img_matches);
    imshow("matches",img_matches);
 
    //此函数等待按键，按键盘任意键就返回
    waitKey();
    return 0;
}

```