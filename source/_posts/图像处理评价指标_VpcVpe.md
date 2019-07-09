---
title: 图像处理评价指标_划分系数Vpc划分熵Vpe
date: 2019-07-09 21:39:40
tags: [图像处理, 评价指标, 图像分割]
---

图像处理评价指标_划分系数Vpc划分熵Vpe

<!--more-->
## 划分系数划分熵
评价指标划分系数`Vpc`和划分熵`Vpe`能够反映分割矩阵的模糊程度，`Vpc`数值越大，分割矩阵的模糊性越小，分割效果越好；`Vpe`数值越小，像素分类越准确，分割效果越好。

（1）划分系数Vpc评价指标的定义为：

$$V_{pc} = \sum_{i=1}^{n}\sum_{k=1}^K u_{ki}^2/n$$

    
其中，$K$表示聚类数目，$u_{ki}$ 是隶属度函数，表示第$i$个像素属于第$k$分类的隶属度，$n$是像素总数。

（2）划分熵Vpe评价指标的定义为： 
$$V_{pe} = -\sum_{i=1}^{n}\sum_{k=1}^K u_{ki}*log(u_{ki})/n$$
	
## Matlab代码
```
function [V_pc,V_pe_10,V_pe_e]=V_pcpe(u)
%评价函数指标 划分系数V_pc，划分熵V_pe

%% u是隶属度函数
[m,n]=size(u);
%% 划分系数V_pc
V_pc = sum(sum(u.^2))/n;

%% 划分熵V_pe
V_pe_10=-sum(sum(u.*log10(u)))/n;
V_pe_e=-sum(sum(u.*log(u)))/n;
```