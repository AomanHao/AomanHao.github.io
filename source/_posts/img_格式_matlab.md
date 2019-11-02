---
title: 图像格式及Matlab的格式转换
date: 2019-10-21 21:44:45
tags: [图像处理]
---

图像格式及Matlab的格式转换
<!--more-->

## 1. matlab图像保存说明
　　matlab中读取图片后保存的数据是uint8类型(8位无符号整数，即1个字节)，以此方式存储的图像称作8位图像，好处相比较默认matlab数据类型双精度浮点double（64位，8个字节），自然可以节省很大一部分存储空间。 
　　详细来说imread把灰度图像存入一个8位矩阵，当为RGB图像时，就存入8位RGB矩阵中。例如，彩色图像像素大小是400*300( 高 * 宽 )，则保存的数据矩阵为400*300*3，其中每个颜色通道值是处于0~255之间。 
但是虽然matlab中读入图像的数据类型是uint8，而在图像矩阵运算的时候，使用的数据类型却是double类型。一是为了保证精度，二是因为如果不转换，在对uint8进行加减时会产生溢出，可能提示的错误为：　
Function ‘*’ is not defined for values of class ‘uint8’
　　1个字节无符号整型最大只能存储数据为255，对图片的操作所以很容易溢出。
## 2. matlab图像类型转换
　　matlab读入图像的数据是uint8，而matlab中数值一般采用double型（64位）存储和运算。所以要先将图像转为double格式的才能运算，区别如下：
img = imread('./1.jpg'); % 读入是unit8型(0~255)数据I1  = im2double(img);    % 把图像转换成double精度类型（0~1）I2  = double(img)/255;   % uint8转换成double,作用同im2double
1
2
3
　　这里补充说明一下，im2double( )和double( )的区别。double( img)就是简单的数据类型转换，将无符号整型转换为双精度浮点型double，但是数据大小没有变化，原本数据是0~255之间，转化后还是0~255。例如原来是255，那么转换后为255.0，小数位0个数是由double数据长度决定，实际数据大小还是255，只不过这个255已经是double类型空间存储了，再增加不会发生溢出情况。而im2double(img)则不仅仅是将uint8转换到double类型，而且把数据大小从0~255映射到0~1区间。
　　另外需要补充说明下面这种情况：
img = imread('./1.jpg');I1  = double(img);I2  = im2double(I2); % I2数据依然是0~255，并不是0~1，即I1=I2
1
2
3
　　因为I1已经是double类型，imdouble不会对double类型数据0~255映射到区间0~1，所以上面im2double操作没有任何作用，I1和I2相等。 
　　总结如下：函数im2double将输入转换成double类型。如果输入是uint8、unit16 或者是二值的logical类型，则函数im2double 将其值归一化到0～1之间，当然就是double类型的了。如果输入本身就是double类型，输出还是double类型，并不进行映射。
　　如果已经是double类型的数据需要映射，则进行下面操作即可：　　
I2 = I1/255;
1
## 3. matlab图像显示imshow类型问题
　　在matlab处理完数据好，我们希望显示或者imwrite写入图片时候，需要注意。如果直接对double之间的数据矩阵I运行imshow(I)，我们会发现有时候显示的是一个白色的图像。 
　　这是因为imshow()显示图像时对double型是认为在0~1范围内，即大于1时都是显示为白色，而imshow显示uint8型时是0~255范围。所以对double类型的图像显示的时候，要么归一化到0~1之间，要么将double类型的0~255数据转为uint8类型。解决方法如下：
imshow(I/255);    % 将图像矩阵转化到0-1之间imshow(I,[]);     % 自动调整数据的范围以便于显示inshow(uint8(I)); % 转成uint8
1
2
3
## 4. uint和double数据转换的深入说明
　　double和uint8、uint16之间数据转换有下面的函数：
im2double(); % 将图像数组转换成double精度类型im2uint8();  % 将图像数组转换成unit8类型 im2uint16(); % 将图像数组转换成unit16类型
1
2
3
　　当然，当图像数据是double类型的0~1之间，下面两者操作是等价的：
I1=im2uint8(I); I2=uint8(round(I*255)); 
1
2
　　但是matlab默认double类型图片数据是位于0~1之间的，而uint8是位于0~255。所以如果矩阵数据图像是double类型（0~1之间）可直接im2uint8，这样不仅完成数据类型转换，而且将0~1之间映射为了0~255之间的数据。 
但是如果图像矩阵数据是double类型的0~255，直接im2uint8转换的话，matlab会将大于1的数据都转换为255，0~1之间的数据才会映射到0~255之间整型的数据。例如下面程序：
img64 = [1,2,3,4];I8    = im2uint8(img64); % I8结果为[255255255255]
1
2
## 5. mat2gray()和im2double()区别
　　这两个如果都是对uint8数据操作，区别就在于前者是归一化操作，归一化后也在0~1之间，自然结果也是double类型，后者是将数据从0~255映射到0~1。例如：
I  = uint8([1,1,2,3]);I1 = mat2gray(I);  % 归一化，I1结果是double型[0,0,0.5,1]I2 = im2double(I); % 映射化，I2结果是double型[0.0039,0.0039,0.0078,0.0118]
1
2
3
　　可以看出，虽然两者都是一种归一化，im2double只不过最大值永远是常数255，最小值永远是0，如下： 
I−0.0255.0−0.0

　　而mat2gray最大值和最小值都是当前矩阵中最大最小的值，如下： 
I−min(I)max(I)−min(I)
　　另外补充一个函数，mat2str()是将数型转换为字符串类型，一般在批量处理图片，给保存图片格式的名称中有作用，这样就不需要格式化sprintf操作了，非常方便。

---

### [我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
### [我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
### [我的GitHub主页，欢迎访问](https://github.com/AomanHao)


