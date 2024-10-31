---
aliases: []
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 引入

当电路存在电压的时候，就会形成电场耦合；当电路存在电流的时候，就存在磁场耦合。于是当两个电路靠得非常近的时候，就会产生串扰。

串扰会对相邻电路产生噪声，由此导致信号完整性下降、减少噪声容限。

## 1.1. 并联微带线

![[并联微带线 串扰.png]]

当电压增加的时候，会造成干扰。

#挂起/信息不足  录屏 gif 需要

# 2. 频域串扰分析

![[频域串扰分析示例.png]]

在受害线的两端观察到串扰信号。

- Near End：受害线路的一端更靠近攻击线路的源头。
- Far End：受害线路的另一端更靠近攻击线路的终端。

需要分析的就是攻击线路导致的 $V_{NE}$ 和 $V_{FE}$。

## 2.1. 平行线的分布参数

我们需要知道平行线的分布电感和电容来确定串扰。

![[平行线的分布电感和电容来确定串扰.png]]

为了简化分析，这里假设了频率足够低，我们用集总电路模型来分析。将上面的电路用集总电路建模，并且分电容和电感来分析。

![[集总电路建模分析串扰.png]]

$$
\begin{gathered}
C_{1}=C_{s1}\times l & L_{1}=L_{s1}\times l \\
C_{2}=C_{s2}\times l & L_{2}=L_{s2}\times l \\
C_{12}=C_{m}\times l & M_{_{12}}=L_{_m}\times l 
\end{gathered}
$$

## 2.2. 电容串扰

大多数情况下，两条平行线具有相同的分布参数和终端电阻。即假设所有电阻相同以及电容相同。

![[电容串扰分析.png]]

由此能分析出来，由于电容串扰产生的干扰为，
$$
\frac{V_{NE}}{V_{G}}=\frac{V_{FE}}{V_{G}}=\frac{j\omega C_{12}R}{4-\omega^{2}R^{2}C^{2}\left(1+\dfrac{2C_{12}}{C}\right)+j4\omega R\left(C_{12}+C\right)}
$$
可以看到这个公式的分母由三个部分组成，并且分别不和频率相关，和 $\omega^{2}$ 相关，和 $\omega$ 相关。由此，
- 当低频时，第一项为主，其他项可忽略
- 当频率增加，第三项为主，其他项可忽略；
- 当频率增加地更多，第二项为主，其他项可忽略。

但是这个界限在哪？我们通过对比项之间的大小可以得知。
$$
\begin{aligned}
\text{当有~}\omega=\omega_{1} \\
&4\omega_{1}R\left(C_{12}+C\right)=4 \\
&\omega_{1}=\frac{1}{R\left(C_{12}+C\right)} \\
\\
\text{当有~}\omega=\omega_{2} \\
&\omega_{2}{}^{2}R^{2}C^{2}\left(1+\frac{2C_{12}}{C}\right)=4\omega_{2}R\left(C_{12}+C\right) \\
&\omega_{2}RC\left(C+2C_{12}\right)=4\left(C_{12}+C\right) \\
&\omega_{2}=\frac{4\left(C_{12}+C\right)}{RC\left(C+2C_{12}\right)}
\end{aligned}
$$
于是可以有以下近似，
$$
\begin{aligned}
\omega<\omega_{_1}: \\
&\frac{V_{NE}}{V_{G}}=\frac{V_{FE}}{V_{G}}\approx\frac{j\omega C_{12}R}{4} C \\
\omega_{1}<\omega<\omega_{2}: \\
&\frac{V_{NE}}{V_{G}} =\frac{V_{FE}}{V_{G}}\approx\frac{j\omega C_{12}R}{j4\omega R\left(C_{12}+C\right)}=\frac{C_{12}}{4\left(C_{12}+C\right)} \\
\omega>\omega_{2}: \\
&\frac{V_{NE}}{V_{G}}=\frac{V_{FE}}{V_{G}}\approx\frac{j\omega C_{12}R}{-\omega^{2}R^{2}C^{2}\left(1+\frac{2C_{12}}{C}\right)}=\frac{C_{12}}{j\omega RC\left(C+2C_{12}\right)}\omega 
\end{aligned}
$$

### 2.2.1. 电容串扰特性


## 2.3. 电感串扰

$$
\begin{align}
&\frac{V_{NE}}{V_{G}}=\frac{j\omega M_{12}R}{4R^{2}+j4\omega RL-\omega^{2}\left(L^{2}-M_{12}^{2}\right)} \\
&\frac{V_{FE}}{V_{G}}=-\frac{V_{NE}}{V_{G}}
\end{align}
$$

### 2.3.1. 电感串扰特性


# 3. 低频频谱电容串扰

