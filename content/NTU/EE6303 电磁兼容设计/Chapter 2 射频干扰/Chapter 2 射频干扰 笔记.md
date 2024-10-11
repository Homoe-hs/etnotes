---
date: 2024-08-15 22:34
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
[[Chapter 7 Antennas 笔记]]

# 1. 基本偶极天线

一般情况下，通过对天线表面的电流分布的积分能获得辐射电场和磁场。在这一章会对一些简单的天线进行研究，因为他们的在远处的辐射场和其他实际的天线的辐射场类似。

## 1.1. 电偶极子

电偶极子由长度为 $dl$ 的无穷小电流元件组成。我们假设其携带的相量电流 $\hat{I}$ 在沿元件长度的所有点上都具有相同的幅度和相位。

![[球坐标表示的电偶极子.png]]

通常用球坐标系描述天线，因为从远距离天线辐射的波是球面波。该坐标系中点的位置由到该点的径向距离 $r$ ，从 $z$ 轴到该点的径向线的仰角 $\theta$ ，以及在 $xy$ 平面上的投影与 $x$ 轴之间的方位角 $\phi$ 来描述。

正交单位向量 $\vec{a}_{r},\vec{a}_{\theta},\vec{a}_{\phi}$ 指向这些坐标值增加的方向。

### 1.1.1. 一般情况分析

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

有自由空间阻抗为 $120 \pi \Omega$，

![[自由空间波阻抗计算式]]

$$
\beta_{0} = \dfrac{2\pi}{\lambda}
$$

### 1.1.2. 远场情况

但是我们更加关心的是对远场的电偶极子的分析。在远场的时候，$\dfrac{1}{r^{2}}$ 可以被忽略。因此对于磁场强度分量和电场强度分量，可以简化为以下两个公式，即只用考虑磁场矢量的方向角分量和电场矢量的仰角分量

![[远场条件下电偶极子磁场强度矢量方向角分量计算式]]
![[电偶极子远场条件下电场强度矢量仰角分量计算式]]

此时的波阻抗为，
![[远场电偶极子波阻抗计算式]]

### 1.1.3. 近场情况

在近场情况下，则是公式中的 $\dfrac{1}{r^{2}}$ 和 $\dfrac{1}{r^{3}}$ 两项起主导作用。由此重写公式为，

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
- 波阻抗 $\dfrac{E_{\theta}}{H_{\phi}}= \dfrac{\eta_{0}}{\beta_{0}r} \gg\eta_{0}$
- 此时的近场为高阻抗场或者电场

如果有 $\beta_{0}r= 1$，这对应于过渡场条件或近场和远场之间的边界。

## 1.2. 磁偶极子

假设有一个半径为 $a$ 的小磁环，其磁偶极矩为 $\hat{m}=\hat{I}\pi a^{2}$

![[Chapter 7 Antennas 笔记_2.png|300]]

### 1.2.1. 一般情况分析

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

有 $\beta_{0}=\dfrac{2\pi}{\lambda}$ 和 $\eta_{0}=\sqrt{ \dfrac{\mu_{0}}{\epsilon_{0}} }$

### 1.2.2. 远场分析

和电偶极子类似的情况，电场只用考虑方向角分量，磁场则是考虑仰角分量，其他分量为 0。

$$
\begin{aligned}
&\widehat{E} _{\phi}=\frac{\hat{m}\omega\mu_{0}}{4\pi r} \beta_{0}\sin\theta e^{-j\beta_{0}r} \\

&\widehat{H}_{\theta}=- \frac{\widehat{m}\omega\mu_{0}}{4\pi\eta_{0}r}\beta_{0}\sin\theta e^{-j\beta_{0}r} \\

\end{aligned}
$$

### 1.2.3. 近场分析

对于磁偶极子，其近场阻抗则是 $\dfrac{E_{\phi}}{H_{\theta}}=\eta_{0}\beta_{0}r\ll \eta_{0}$

# 2. 近场与远场的波阻抗分析总结

## 2.1. 远场的波阻抗分析

对于电偶极子和磁偶极子而言，其远场的波阻抗 $Z_{\omega}$ 都可以看作是自由空间的波阻抗。

![[自由空间波阻抗计算式]]

$\eta_{0} = 120 \pi \approx 377 \Omega$

## 2.2. 近场的波阻抗分析

当有 $\beta_{0}r\ll 1$ 的时候，可以看作近场。

对于电偶极子而言，其近场阻抗为 $Z_{\omega}=\dfrac{E_{\theta}}{H_{\phi}} = \dfrac{\eta_{0}}{\beta_{0}r}\gg \eta_{0}$，此时为高阻抗场。

对于磁偶极子而言，其近场阻抗为 $Z_{\omega}=\dfrac{E_{\phi}}{H_{\theta}}=\eta_{0}\beta_{0}r\ll \eta_{0}$，此时为低阻抗场。

![[电偶极子和磁偶极子的波阻抗.png|400]]

## 2.3. 近场远场边界

对于天线长度 $D\ll\lambda$ 的小天线而言，当场距离天线的距离满足 $R_{ff}>\dfrac{\lambda}{2\pi}$ 时，此时的场可以按照远场进行分析。

[[大天线远场条件推导]]

# 3. 天线辐射特性

## 3.1. 远场天线上任意一点与源的距离近似

辐射方向图是天线辐射特性的图形表示，除非另有说明，否则它是在**远场**中定义的，且一般考虑沿 z 轴放置的有限长度线源。

对于远场中的天线来说，天线上任意一点与源之间的距离 $R$ 可以写为

![[天线上任意一点与电磁波源之间的距离计算式]]

[[天线上任意一点与源之间的距离近似的推导]]

## 3.2. 线天线

假设现在有一个长度为 $2L$ 的具有均匀电流的线天线。

### 3.2.1. 归一化电场

对于线天线上 $z'$ 处任意一点，有仰角 $\theta'$，代入电偶极子的电场公式[[电偶极子远场条件下电场强度矢量仰角分量计算式]]。
$$
\hat{E}_{\theta}=j \frac{\hat{I}dz'}{4\pi}\eta_{0}\beta_{0}\sin\theta' \frac{1}{R}e^{-j\beta_{0}R}
$$

>[! question] 
>在这里，slides 上给的公式的距离是 $r$，即天线中心到源的距离，但是前面又是考虑的 $z'$ 处的电流，我觉得这里有些冲突了。于是改换成 $R$。

将其沿着 $-L$ 到 $L$ 进行积分，由于电流 $\hat{I}$ 是均匀的，所以有，
$$
\hat{E}_{\theta}=j \frac{\hat{I}}{4\pi}\eta_{0}\beta_{0} \int _{-L}^{L} \sin\theta' \frac{1}{R}e^{-j\beta_{0}R}~dz'
$$
将前面的近似距离代入可得，
$$
\begin{align}
\hat{E}_{\theta} & =j \frac{\hat{I}}{4\pi}\eta_{0}\beta_{0} \int _{-L}^{L} \sin\theta' \frac{1}{R}e^{-j\beta_{0}(r-z'\cos \theta )}~dz' \\
 & \approx j \frac{\hat{I}}{4\pi}\eta_{0}\beta_{0} e^{-j\beta r} \int _{-L}^{L} \sin\theta' \frac{e^{j\beta_{0}z'\cos \theta}}{R}~dz' 
\end{align}
$$
在远场，如果有 $r\gg 2L$，那么有 $R \approx r$ 和 $\theta' \approx \theta$，代入并积分得，
$$
\hat{E}_{\theta} =j\frac{\hat{I}L}{2\pi r}\eta_{0}\beta_{0}e^{-j\beta_{0}r}\frac{\sin(\beta_{0}L\cos\theta)}{\beta_{0}L\cos\theta}\sin\theta 
$$
有归一化电场定义，
![[100 项目笔记/NTU/EE6303 电磁兼容设计/Chapter 2 射频干扰/归一化电场定义式]]

因此，具有均匀电流的天线的归一化电场特性为，

![[均匀电流天线的归一化电场特性]]

![[均匀电流线天线的归一化辐射功率特性]]

### 3.2.2. 辐射方向图

主要参数有主瓣、增益、3dB波束宽度、第1零点、第1旁瓣、后瓣

### 3.2.3. 天线的方向性系数

![[方向性系数]]

$$
D = \dfrac{pd_{max}}{pd_{ave}} = \dfrac{p(\theta _{max},\phi _{max})}{p _{ave}}\ge 1
$$
$p(\theta,\phi)~ \left[\pu{w/sr}\right]$ 为辐射强度

![[立体角示意.png|300]]

立体角 $\Omega$ 为球体表面积与半径的比值，总立体角为 $4\pi$ 球面度（$\pu{ sr }$），具体计算如下
$$
\begin{aligned}
&d\Omega=\sin\theta d\theta d\phi \\
&\Omega=\int_{0}^{2\pi}\int_{0}^{\pi}\sin\theta d\theta d\phi \\
&=2\pi\int_{0}^{\pi}\sin\theta d\theta \\
&=2\pi|-\cos\theta|_0^{\pi} \\
&=4\pi \quad \left[ \pu{sr}\right]
\end{aligned}
$$
平均辐射功率为，
$$
\begin{aligned}P_{ave}&=\frac{1}{4\pi}\int_{0}^{2\pi}\int_{0}^{\pi}P(\theta,\phi)\sin\theta d\theta d\phi\\&=\frac{1}{4\pi}\iint_{4\pi}P(\theta,\phi) d\Omega\end{aligned}
$$
代入方向性系数公式可得，
$$
D = \frac{4\pi}{\iint_{4\pi}P_{n}(\theta,\phi) d\Omega}
$$
### 3.2.4. 波束面积

定义波束面积为 $\Omega _{A}$，是归一化辐射功率在总立体角上的积分。由此也可重写方向性系数。

$$
\begin{aligned}&\Omega_{A}=\iint_{4\pi}P_{n}(\theta,\phi) d\Omega\\&D=\frac{4\pi}{\Omega_{A}}\end{aligned}
$$
光束面积越小，方向性越大。

### 3.2.5. 各向同性天线

各向同性天线是一种向各个方向均匀辐射功率的理想天线。不存在实际的物理各向同性天线，然而经常被用作天线增益的参考天线。对于各向同性天线，$P_{n}(\theta,\phi) = 1$ 适用于所有角度。因此有 $\Omega _{A}=4\pi$ 和 $D = 1$。

### 3.2.6. 电偶极子

对于电偶极子，有 $F (\theta,\phi)= \sin \theta$，$\Omega _{A}=\dfrac{8\pi}{3}$，$D =1.5$。
[[电偶极子归一化电场特性计算式]]
[[电偶极子归一化电场、波束面积、方向性系数推导]]

## 3.3. 其他天线

### 3.3.1. $\lambda/2$ 偶极子天线
$$F\left(\theta,\phi\right)=\frac{cos\left(\frac{\pi}{2}cos\theta\right)}{sin\theta}$$
$$\Omega_A=7.66$$
$$D=1.64$$
### 3.3.2. $1\lambda$ 偶极子天线

![[1λ 偶极子天线归一化电场特性计算式]]
$$\Omega_A=5.21$$
$$D=2.41$$
### 3.3.3. 长线天线
$$D \sim \frac{2L}{\lambda} \left(L \gg \lambda\right)$$
L是天线长度
### 3.3.4. 孔径天线

![[孔径天线方向性系数计算式]]

### 3.3.5. 孔径效率

![[孔径效率]]

## 3.4. 天线增益

![[天线增益计算式]]

天线增益是互易的。即同一天线的发射增益与接收增益相同。

## 3.5. 无耗天线增益

#### 3.5.1.1. 无损偶极子

赫兹偶极子 $D=1.5$ ， $G=10log_{10}\left(1.5\right)=1.76dBi$
$\lambda/2$ 偶极子天线 $D=1.64$ ， $G=10log_{10}\left(1.64\right)=2.14dBi$
$1\lambda$ 偶极子天线 $D=2.41$ ， $G=10log_{10}\left(2.41\right)=3.82dBi$

### 3.5.2. 无损孔径天线

$10\lambda$ 直径孔径天线，假设 100%的孔径效率
$$
\begin{aligned}
&A_{e}=A_{ap}=\pi(5\lambda)^{2}=25\pi\lambda^{2} \\
&D=\frac{4\pi A_{e}}{\lambda^{2}}=100\pi^{2}=987 \\
&G=D=29.9dBi
\end{aligned}
$$

另一个 60%孔径效率的，在算有效面积的时候把效率算进去即可。

## 3.6. 有损天线增益

>[! question]
>天线增益的有损无损不包括孔径效率？

具体过程和上面一样，在计算 $G$ 的时候乘上天线效率即可。

## 3.7. 半功率波束宽度

半功率波束宽度指增益波动小于 $3\pu{ dB }$ 的波束宽度。波束宽度在两个主要平面中定义：$\phi=0^{\circ}$（x-z 平面）或者 $\phi = 90 ^{\circ}$（y-z 平面）

对于长度为 $L$ 的线天线，电流有，
$$
I(r)=\cos ^{n}(\dfrac{\pi r}{L})
$$
对于具有半径 $a$ 的圆孔径天线，
$$
E_{a}(r) = \lvert 1-(\dfrac{r}{a})^{2} \rvert ^{n}
$$

## 3.8. $3\pu{ dB }$ 波束宽度

对于高指向性天线，其方向性系数可以用下面的经验公式进行计算。
![[高指向性天线方向性系数经验计算式]]

## 3.9. 天线类型

各向同性天线、全向天线、舷侧天线、端火天线

## 3.10. 例题 1a 和 1b

[[EE6303 例题合集#Example 1a]]

## 3.11. 波的传导

### 3.11.1. 有效辐射功率

![[有效辐射功率]]

### 3.11.2. 远场功率密度与远场电场

![[远场功率密度计算式]]

![[远场电场强度计算式]]

[[远场电场推导]] 

### 3.11.3. 接收功率与 Friss 传输方程

$$
P_{r} = P_d\times A_e\times e_r
$$
$P_{d}$ 为远场功率密度；$A_{e}$ 为有效孔径面积；$e_{r}$ 为接收端天线的效率。由此导出 Friss 传输方程。

![[Friss 传输方程]]

![[路径损耗计算式]]

## 3.12. 极化损失

![[极化#^58e141]]

随后我们考虑线极化的远场端极化损失。

产生这种极化类型的天线一般都是偶极子天线、八木天线。根据线极化角度相对于地面的情况，分为垂直极化和水平极化。

计算极化损失时，考虑的是位于远场的接收端天线相对于需要接收的电磁波的极化损失。在远场时电磁波传播模式是TEM波，电场方向正交于电磁波传播方向。

如果两个天线的极化方向相同，但是位置错开，我们只需要知道接收端天线相对于电磁波传播方向的夹角就可以计算极化损失。这部分的原理非常简单，只需要知道电磁波的电场在天线位置上的投影就行。

![[计算电场分量.png|300]]

这里的 $\theta$ 就是入射电场 $E_{inc}$ 与接收端天线的夹角。所以接收端接收到的电场 $E_{rx}$ 为，
$$
E_{rx}=E_{inc}cos\theta
$$
需要注意的是极化损失计算的是**功率上的损失**，接收端接收功率与电磁波在这个位置的功率关系为：
$$
P_{rx}=\frac{E_{rx}^2}{\eta_0}=P_{inc}cos^2\theta
$$
其中 $\eta_0$ 是电磁波的特征阻抗， $\theta$ 代表的角度永远是接收端天线相对于电磁波的角度，由于已经处于远场所以和发射端关系不大。

以对数形式表示的话就是：
$$
P_{rx}\left(\mathrm{dB}\right)=P_{inc}\left(\mathrm{dB}\right)+20log_{10}\left(cos\theta\right)
$$
## 3.13. 圆极化的远场端极化损失计算

圆极化可以分为顺时针圆极化和逆时针圆极化，可以视为两个线极化的叠加。所以传递到线极化的话自然存在损失，这个值老印取了大约 $3dB$

在计算圆极化与线极化之间造成的极化损失时只需要在 $20log_{10}\left(cos\theta\right)$ 的基础上额外损失 $3dB$ 就可以了。

## 3.14. Example 2a, 2b, 2c

[[EE6303 例题合集#Example 2a]]

