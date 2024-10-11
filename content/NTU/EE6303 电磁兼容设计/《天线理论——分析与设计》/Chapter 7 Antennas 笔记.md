---
date: 2024-09-03 13:23
aliases: 
tags: 
number headings: auto, first-level 2, max 5, contents ^toc, 1.1.
---
在本章中，我们将回顾有意天线的基础知识。这将提供计算产品附近的电磁场水平的能力，用于确定其对干扰的敏感性。将讨论用于验证法规遵从性的天线。对有意天线的分析还可以帮助我们了解无意天线的辐射能力，这正是我们试图最小化或防止的辐射能力。

## 1. 基本偶极天线

一般情况下，通过对天线表面的电流分布的积分能获得辐射电场和磁场。在这一章会对一些简单的天线进行研究，因为他们的在远处的辐射场和其他实际的天线的辐射场类似。

### 1.1. 电偶极子

电偶极子由长度为 $dl$ 的无穷小电流元件组成。我们假设其携带的相量电流 $\hat{I}$ 在沿元件长度的所有点上都具有相同的幅度和相位。

![[Chapter 7 Antennas 笔记_1.png|300]]

通常用球坐标系描述天线，因为从远距离天线辐射的波是球面波。该坐标系中点的位置由到该点的径向距离 $r$ ，从 $z$ 轴到该点的径向线的仰角 $\theta$ ，以及在 $xy$ 平面上的投影与 $x$ 轴之间的方位角 $\phi$ 来描述。

正交单位向量 $\vec{a}_{r},\vec{a}_{\theta},\vec{a}_{\phi}$ 指向这些坐标值增加的方向。

#### 1.1.1. 一般情况分析

磁场强度矢量的分量变为，
$$
\hat{H}_{r} = 0
$$
$$
\hat{H}_{\theta} = 0
$$
![[电偶极子磁场强度矢量方向角分量]]

同样有电场强度矢量，
![[电偶极子电场强度矢量径向分量计算式]]
![[电偶极子电场强度矢量仰角分量计算式]]
![[电偶极子电场强度矢量方向角分量计算式]]

有自由空间阻抗为 $120\Omega$，
![[自由空间波阻抗计算式]]

$$
\beta_{0} = \dfrac{2\pi}{\lambda}
$$

#### 1.1.2. 远场情况

但是我们更加关心的是对远场的电偶极子的分析。在远场的时候，$\dfrac{1}{r^{2}}$ 可以被忽略。因此对于磁场强度分量和电场强度分量，可以简化为以下两个公式，即只用考虑磁场矢量的方向角分量和电场矢量的仰角分量

![[远场条件下电偶极子磁场强度矢量方向角分量计算式]]
![[电偶极子远场条件下电场强度矢量仰角分量计算式]]

此时的波阻抗为，
![[远场电偶极子波阻抗计算式]]

#### 1.1.3. 近场情况

在近场情况下，则是公式中的 $\dfrac{1}{r^{2}}$ 和 $\dfrac{1}{r^{3}}$ 两项起主导作用。
$$
\begin{aligned}
&\widehat{H}_{r} =0 \\
&\widehat{H}_{\theta} =0 \\
&\widehat{H} _{\phi}=\frac{\hat{I}dl}{4\pi r^{2}}\sin\theta e^{-j\beta_{0}r} \\
&\widehat{E}_{r}=-j2 \frac{\hat{I}dl}{4\pi} \eta_{0} \frac{1}{\beta_{0}r^{3}}\cos\theta e^{-j\beta_{0}r} \\
&\widehat{E}_{\theta}=-j \frac{\hat{I}dl}{4\pi}\eta_{0} \frac{1}{\beta_{0}r^{3}}\sin\theta e^{-j\beta_{0}r} \\
&\widehat{E}_{\phi}=0
\end{aligned}
$$

在近场情况下，如果有 $\beta_{0}r\ll 1$，那说明
- 通常有两个以上的电场和磁场
- $E_{r}$ 非 0
- 波阻抗 $\dfrac{E_{\theta}}{H_{\phi}}~ \dfrac{\eta_{0}}{\beta_{0}r} \gg\eta_{0}$
- 此时的近场为高阻抗场或者电场

如果有 $\beta_{0}r= 1$，这对应于过渡场条件或近场和远场之间的边界。

### 1.2. 磁偶极子

假设有一个半径为 $a$ 的小磁环，其磁偶极矩为 $\hat{m}=\hat{I}\pi a^{2}$

![[Chapter 7 Antennas 笔记_2.png|300]]

#### 1.2.1. 一般情况分析

磁偶极子的磁场矢量和电场矢量为，
$$
\begin{aligned}
&\widehat{E}_{r} =0 \\
&\widehat{E}_{\theta} =0 \\
&\hat{E}_{\phi} =-\mathrm{j}\frac{\hat{m}\omega\mu_{0}}{4\pi}\beta_{0}^{2} \sin\theta\left(j\frac{1}{\beta_{0}r}+\frac{1}{\beta_{0}^{2}r^{2}}\right)e^{-j\beta_{0}r} \\
&\widehat{H}_{r} =2j \frac{\hat{m}\omega\mu_{0}}{4\pi\eta_{0}}\beta_{0}^{2} \cos\theta\left(\frac{1}{\beta_{0}^{2}r^{2}}-j \frac{1}{\beta_{0}^{3}r^{3}}\right)e^{-j\beta_{0}r} \\
&\hat{H}_{\theta} =j \frac{\hat{m}\omega\mu_{0}}{4\pi\eta_{0}}\beta_{0}^{2} \sin\theta\left(j \frac{1}{\beta_{0}r}+\frac{1}{\beta_{0}^{2}r^{2}}-j \frac{1}{\beta_{0}^{3}r^{3}}\right)e^{-j\beta_{0}r} \\
&\hat{H}_{\phi} =0 
\end{aligned}
$$

#### 1.2.2. 远场分析

和电偶极子类似的情况，电场只用考虑方向角分量，磁场则是考虑仰角分量。

$$
\begin{aligned}
&\widehat{E} _{\phi}=\frac{\hat{m}\omega\mu_{0}}{4\pi r} \beta_{0}\sin\theta e^{-j\beta_{0}r} \\

&\widehat{H}_{\theta}=- \frac{\widehat{m}\omega\mu_{0}}{4\pi\eta_{0}r}\beta_{0}\sin\theta e^{-j\beta_{0}r} \\

\end{aligned}
$$

#### 1.2.3. 近场分析

对于磁偶极子，其近场阻抗则是 $\dfrac{E_{\phi}}{H_{\theta}}=\eta_{0}\beta_{0}r\ll \eta_{0}$

![[电偶极子和磁偶极子的波阻抗.png|400]]

## 2. 近场与远场的边界条件

