---
对象类型: 笔记
aliases: 
tags:
---
>[! reference]
>“10.3 THE GUNN DIODE” (Streetman和Banerjee, 2015, p. 548)

这里给出一个大概的推导，理解趋势的变化即可。
![[耿氏二极管 I-V 特性曲线.png]]
有 I-V 关系（J-E 关系）为 $\dfrac{J}{E}=\sigma$，所以我们从导电率的变化就能看出 I-V 特性的变化。

# $0\leq E \leq E_{th}$

此时电子全部都囤积在低导带上，所以有电导率为，
$$
\sigma = nq\mu_{L}
$$
此时，随着电压的增加，电子的速度线性增加。

# $E_{th}\leq E \leq E_{v}$

随着电压超过临界值，电子开始向状态密度更大、迁移率更小的卫星谷迁移，由此导致导电率为负。
$$
\begin{align}
 & \text{总电子浓度} & n =n_{L}+n_{U} \\
 & \text{总电导率} & \sigma = n_{L}q\mu_{L}+n_{U}q\mu_{L}
\end{align}
$$

# $E_{v}\leq E$

此时电子已经基本全部迁移到卫星谷中，以更低的迁移率随着电压增加速度。
$$
\sigma = nq\mu_{U}
$$
