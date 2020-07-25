---
title: ISP图像处理之image output interface
date: 2020-06-17 18:44:45
tags: [图像处理, ISP]
---

ISP图像处理之image output interface
<!--more-->

手机，车载sensor常见的接口主要是DVP和MIPI。 DVP是比较老的并行接口；MIPI是高速串行接口。另外安森美自己搞了一个HiSPi接口，但是只有他家自己在用，和MIPI差不多。

MIPI全称为“Mobile Industry Processor Interface”，分为MIPI DSI 和MIPI CSI，分别对应于视频显示和视频输入标准。

接口对比如下：


![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_isp_inter1.jpg)

MIPI采用差分线传输，速度还是很快的，比并行传输要快很多



## DVP接口：

Digital Video Port： DVP是比较老sensor支持的接口，但是现在的sensor一般都兼容。

DVP采用并行输出方式，d数据位宽有8bit、10bit、12bit、16bit，是CMOS电平信号（重点是非差分信号），PCLK最大速率为96MHz，接口和时序如下图：
![](https://img-blog.nos-eastchina1.126.net/PersonalPhoto/blog_isp_interDVP.jpg)

## MIPI 接口；

MIPI（移动行业处理器接口）是Mobile Industry Processor Interface的缩写。

MIPI联盟是一个开放的会员制组织。2003年7月，由美国德州仪器（TI）、意法半导体（ST）、英国ARM和芬兰诺基亚（Nokia）4家公司共同成立。MIPI联盟旨在推进手机应用处理器接口的标准化 。该组织结集了业界老牌的软硬件厂商包括最大的手机芯片厂商TI、影音多媒体芯片领导厂商意法、全球手机巨头诺基亚以及处理器内核领导厂商ARM、还有手机操作系统鼻祖Symbian。随着飞思卡尔、英特尔、三星和爱立信等重量级厂商的加入，MIPI也逐渐被国际标准化组织所认可 。

由于对更高的图像分辨率、更大的颜色深度和更快的帧速率的需求，今天的主机处理器到摄像机传感器接口的带宽已经达到了极限。但是对于具有跨越多个产品代的性能目标的设计人员来说，更多的带宽是远远不够的。移动行业需要一个标准的、健壮的、可扩展的、低功耗的、高速的、低成本的摄像机接口来支持移动设备的广泛的成像解决方案

MIPI联盟相机工作小组创造了一个清晰的设计路径,不仅是今天的带宽足够灵活来解决挑战但“特性和功能”挑战的行业,每年生产超过十亿手机用户广泛,应用程序和成本点。

MIPI CSI-2和MIPI CSI-3是原MIPI相机接口标准的继承者。这两种标准都在不断演变。两者都是高能力的架构，可以为设计师和制造商提供服务最终消费者——更多的选择和更大的价值，同时保持标准接口的优势。




## 硬件相关
面试别人的时候问一问就可以知道别人到底有没有真的做过MIPI（可能做过也不知道），那就是：

MIPI DPHY 的传输距离一般不超过20cm。

DVP总线PCLK极限大约在96M左右，而且走线长度不能过长，所有DVP最大速率最好控制在72M以下，故PCB layout会较好画

MIPI总线速率随便就几百M，而且是lvds接口耦合，走线必须差分等长，并且注意保护，故对PCB走线以及阻抗控制要求高一点。

一般而言，96M pclk是DVP的极限，曾经在一个team做多摄相头的图象采集设备，DVP总线连接。几个不懂技术的一直push我说是硬件走线干扰啊，拘泥纠缠在什么I2C这种低速控制信号受干扰，还搞了好几天看示波器，被烦的不行，我用一个晚上时间改驱动降低PCLK降桢率搞定。

DVP是并口，需要PCLK、VSYNC、HSYNC、D[0：11]——可以是8/10/12bit数据，看ISP或baseband是否支持；

MIPI是LVDS，低压差分串口。只需要要CLKP/N、DATAP/N——最大支持4-lane，一般2-lane可以搞定。

显然，MIPI接口比DVP的接口信号线少，由于是低压差分信号，产生的干扰小，抗干扰能力也强。最重要的是DVP接口在信号完整性方面受限制，速率也受限制。500W还可以勉强用DVP，800W及以上都采用MIPI接口。

## 工频干扰 (Banding)
　　Sensor在日光灯作为光源下获取图像数据时会产生flicker，其根本原因是照在不同pixel上光能量不同产生的，所接受的光能量的 不同也就是图像的亮度的不同。

　　由于CMOS sensor的曝光方式是一行一行的方式进行的，任何一个pixel的曝光时间是一样的，也就是同一行上的每个pixel的曝光开始点和曝光的时间都是一模一样的，所以同一行的所有点所接收到的能量是一样的，而在不同行之间虽然曝光时间都是一样的，但是曝光的开始点是不同的，所以不同行之间所接受到的能量是不一定相同的。 为了使不同行之间所接受的能量相同，就必须找一个特定的条件，使得每一行即使曝光开始点不同，但是所接受的光能量是相同的，这样就避开了flicker，这个特定的条件就是曝光时间必须是光能量周期的整数倍时间。

　　Banding由工频干扰引起，交流电光源都有光强的波动，在中国交流电频率是50Hz，光强的波动就是100Hz，周期10ms。如果camera曝光时间不是10ms的整数倍，那么在不同的感光面接收到的光能量一定不一样，体现在图像上就是有明暗条纹。 消除banding就得想办让曝光时间是10ms的整数倍！60Hz的交流电需要控制曝光时间为8.33ms的整数倍。
　　
>以50Hz为例说明，实现这个有两种办法：
　　1、设置曝光控制，强制为10ms整数倍变化，但是这样会浪费一部分曝光时间，导致曝光无法用满，在室内自然就会损失性能。
　　2、修改桢率，使每桢图像分到的时间是10ms的整数倍，则可以用满每桢曝光时间在，室内效果更好。修改桢率可以插入Dummy Line或者Dummy Pixel。这需要一点点计算，具体计算需要看sensor输出Timing。
　　例如把桢率设置为7.14fps，则每桢曝光时间是140ms。如果是15fps，则每桢曝光时间是66.66ms，如果强制曝光为10ms整数倍，最大即60ms，则有6.66ms无法参与曝光，损失性能。
　　具体调整桢率方法得和sensor的FAE沟通，每个sensor都可能不一样，不能一概而论。调整桢率还有个原则要注意，预览一般不能低于 10fps，再低就很卡，常用14.3fps和12.5fps；抓拍不能低于5fps，否则用手就很难拍出清晰的照片，常用7.14fps。桢率是一个权 衡折中的选择，高了曝光时间不够，暗光效果太差，低了没法拍照，容易虚

参考文章：
1、ISP从算法到硬件设计——从CCM到sensor结构 - 烓围玮未 -https://zhuanlan.zhihu.com/p/140931885
2、高清摄像头MIPI接口与ARM处理器的连接 – 老拙 – 博客园 https://www.cnblogs.com/whw19818/p/5811299.html

###[我的个人博客主页，欢迎访问](http://www.aomanhao.top/)
###[我的CSDN主页，欢迎访问](https://blog.csdn.net/Aoman_Hao)
###[我的GitHub主页，欢迎访问](https://github.com/AomanHao)

