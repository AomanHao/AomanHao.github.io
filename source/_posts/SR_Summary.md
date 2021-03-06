图像超分辨率重建



## 按照算法的输入输出类型归类

1、输入为低分辨率图像序列（视频），输出为单帧高分辨率图像的超分辨率问题，称为基于重建的超分辨率（）

reconstruction-based super-resolution

2、输入输出均为低分辨率图像序列（视频）的超分辨率问题，称为视频超分辨率问题（）video super-resolution

3、输入输出均为单帧图像的超分辨率问题，称为单幅图像的超分辨率问题（）single image super-resolution SISR



输入为单帧低分辨率图像，输出为图像序列的超分辨率问题，因为缺失信息太多，研究的实际意义不大。



SISR中，根据是否需要训练数据集的超分辨率问题分为增强边缘的超分辨率问题和基于学习的超分辨率问题





## 成像观测模型

$$
y_k = DB_kW_kx + n_k, k=1,2,...,N
$$



其中，*y*是低分辨率图像，*X*是原始高分辨率图像，*D*表示下采样矩阵，*B*表示成像模糊矩阵，*W*表示运动矩阵，*n*表示加性噪声



![](D:\杂货文件夹\文章MD\图像附件\高分低分图像观测模型.jpg)

## 基于插值的方法



### 最近邻插值法

通过计算待估计像素值的位置与周围像素 的位置之间的距离，选取最近位置的像素值作为自身的像素值。 

优点：计算量小、计算速度快

缺点：重建效果较差。



### 双线性插值法

分别在水平方向和垂直方向进行一 阶线性插值，然后将两者结合起来。 

双线性方法提高了图像的清晰度，但减少了细节。 



### 三次样条插值

 这种算法是高阶插值函数 中最经典的方法，即在插值点附近使用更多的像素 值，能够达到较高的插值精度，但是存在计算量较 大、易受噪声干扰的缺点。



## 基于重构的方法

### 频域法

１９８４年，Ｔｓａｉ和 Ｈｕａｎｇ［７］首次提出了在频域内提高 图像分辨率的思想，在假定 ＬＲ图像生成模型后，分别 对 ＬＲ图像和原始 ＨＲ图像进行傅里叶变换，在频域中 建立起二者之间的线性关系，重建出 ＨＲ图像．该方法假设图像中不存在运动模糊和观测噪声，同时忽略了 光学系统的点扩散函数，因此只适合理想图像退化模 型．后续改进算法分别采用递归最小二乘法［１５］、离散 ＤＣＴ变换［１６］和小波变换［１７，１８］消除图像中的观测噪声、 空间模糊和相对物体运动，有效提高了重建图像质量， 并加快了算法速度． 



频域重建方法：

优点：简单，运行速度快，

缺点：处理复 杂退化模型的能力有限且难以加入先验知识．



### 空域法 

空域法对影响图像成像效果的空域因素（如光学 模糊、运动模糊等）建模．因此，更接近实际应用情况． 常用的 空 域 ＳＲ方 法 主 要 包 括基于迭代反投影（ＩＢＰ）的方法、基于最大 后验概率（ＭＡＰ）的方法、基于凸集投影（ＰＯＣＳ）的 方法等．





#### 基于迭代反投影

![](D:\杂货文件夹\文章MD\图像附件\迭代反投影法.jpg)

表示由初始估计得到低分辨率图像与实际的低分辨率图像相等。否则，将误差反投影并修正。直到误差适当时，终止迭代。



优点：简单直观、运算量小、收敛快

缺点：反投影算子较难选择、通常解不唯一，并且每次迭代的误差均匀地累加到重建的图像上，所以图像的边缘存在一定程度的锯齿。



##### 实现边缘保持

Dai等人[18]提出基于双向滤波的 IBP算法，双向滤波可以通过添加来自特征域的额外信息来实现边缘保持图像平滑，对位于空间域和特征域中的像素进行平滑，从而改善了重建图像的细节信息，使得图像的质量有很大的提高。

##### 针对锯齿改进

使用传统的插值算法会产生锯齿，,\陶志强等人[20]提出基于新边缘指导插值的迭代反投影超分辨率重建算法，该算法使用新边缘指导插值算法[21]。获得高分辨率图像的初始估计，并引入迭代终止条件，不但提高了迭代算法的效率，而且能有效地提高图像的质量，尤其在处理图像的边缘和细节时效果要更好一些。【陶志强，李海林，张红兵.基于新边缘指导插值的迭代反投影超分辨率重建算法[J]. 计算机工程，2016，42（6）：255-260.】





#### 凸集投影法

该方法先通过迭代，得出高分辨率图像解空间与代表高分辨率图像的约束集的交集，从而确定一个更小的解空间来完成高分辨率图像的重建。在高分辨率图像空间中选取一点作为出发点，连续多次迭代投影获得满足所有约束凸集合的下一个点，从而获取高分辨率图像。



优点：充分利用先验知识，较好地保证高分辨率图像的边缘和细节。

缺点：很大程度上依赖于初始点的随机选择（导致解不稳定，同时也不唯一），收敛慢、计算量大、收敛稳定性不高。

改进方向：添加约束条件使解唯一，提高收敛速度、收敛稳定性、优化计算量



#### 最大后验概率估计法

凸集投影法的解不唯一，为了解决这个问题，Schultz等人提出了最大后验概率估计法，该方法在解中加入先验约束，可以确保解存在并且唯一，收敛稳定性得到了提高，但是收敛慢，提高了计算量，且图像细节保持能力不佳。



优点：解唯一，收敛性好

缺点：计算量大，图像细节易被平滑

改进方向：保持细节边缘、提高收敛速度、优化计算量



## 基于学习的方法

其基本思想是通过学习得到高分辨率图像与低分辨率图像之间的映射关系，训练的样本数量越大，重建得到的图像越精确， 边缘和纹理等细节信息越丰富。

![训练过程](D:\杂货文件夹\文章MD\图像附件\学习SR训练过程.jpg)

训练过程



![](D:\杂货文件夹\文章MD\图像附件\SR重建过程.jpg)

重建过程





### 基于邻域嵌入的方法

假设 ＨＲ图像与其对应的 ＬＲ图像块在特征空间中具有相似的局部流形





优点：对样本数据集依赖性小

缺点：近邻图像块数目参数需要人为固定，





### 基于稀疏表示的方法

通过稀疏分解将图像变换到稀疏域，样本库中 LR、HR图像对共享同一稀疏表示系数。

输入待重建LR图像，利用LR字典计算稀疏系数，再应用在已知的HR图像的字典，重建HR图像



优点：

缺点：



