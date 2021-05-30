## 论文信息



[Anchored Neighborhood Regression for Fast Example-Based uper Resolution]-TIMOFTER, 2013, IEEE International Conference on Computer Vision 



## 前置内容

邻域嵌入（Neighbor Embedding, NE）是“样本-样本”映射，在训练样本中寻找测试样本的相似邻居特征样本，计算量略大。

稀疏编码（Sparse Coding）重建的过程是从字典中自适应的选择一个或者多个字典原子，这些字典原子适合当前输入低分辨率图像块特征，最后利用这些字典原子的线性组合来得到相应的高频细节特征。需要在重建过程计算LR到HR图的原子投影矩阵，计算复杂度高。

锚点邻域回归（Anchored Neighborhood Regression, ANR）改进SC算法，SC的原子投影矩阵需要在重建过程进行在线处理，耗时很大。ANR算法提出找一个投影矩阵可以在训练阶段离线计算，映射关系确定后在重建过程直接使用，可以实时重建高分辨率图像。

稀疏表示的思想在于LR字典与HR字典可以共用一套稀疏系数矩阵

LR: 低分辨率；HR：高分辨率

## 全局回归（ **Global Regression**） 



全局回归（ Global Regression, GR）是ANR的极端情况。全局回归通过相同的投影矩阵把LR特征投射到HR空间 ，针对所有字典特征,，由GR引出投影矩阵的公式

假设输入图像块特征对应相同的映射矩阵全局回归看作稀疏为$l_2$范数正则化的最小二乘回归
$$
min\lVert y_F-N_l\beta \rVert_2^2+ \lambda \rVert\beta\rVert_2 (1)
$$


其中，$y_F$表示 输入的LR块特征，$N_l$表示 LR空间的邻居元素，$\beta$ 表示稀疏系数，$\lambda$解决 singularity (ill-posed) problems



1、在NE算法中，$N_l$是输入特征样本$y_F$的K个邻居元素（特征样本）

2、在本文中$N_l$表示在LR字典中，中心原子的$K$个最近邻居元素（原子）





我们可以将这个问题重新表述为由系数的$l_2$范数正则化的最小二乘回归，求Eq1得稀疏系数
$$
β = (N_l^T N_l + λI)^{−1}N_l^T y_F (2)
$$
因为LR字典与HR字典共用稀疏系数，so HR patch 重建表示如下:
$$
x = N_h \beta(3)
$$
$x$: 输出的HR patch；$N_h$：  $N_l$的邻居HR元素

---



考虑是GR是特殊情况，即中心原子的邻居元素是字典的其他的原子，可以表示如下：
$$
(N_h, N_l)=(D_h, D_l)(4)
$$
将Eq4带入Eq2，3，得到


$$
x = D_h(D_l^T D_l + λI)^{−1}D_l^T y_F(5)
$$
$y_F$是输入的LR特征patch，$x$是输出的HR 特征patch；

投影矩阵表示为：
$$
P_G = D_h(D_l^T D_l + λI)^{−1}D_l^T(6)
$$


投影矩阵可以在训练阶段离线计算，在重建阶段输入LR 特征patch  乘以  投影矩阵 就可以输出HR 特征 patch。

全局回归通过相同的投影矩阵把 LR特征投射到HR空间，针对所有字典特征。得到的HR特征不一定与LR特征匹配算法灵活性差，图像质量不理想

