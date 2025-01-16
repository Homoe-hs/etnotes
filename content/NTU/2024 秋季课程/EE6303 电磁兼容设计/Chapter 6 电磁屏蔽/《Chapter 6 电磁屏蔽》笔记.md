---
对象类型: 笔记
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 电磁场基础
## 1.1. 电磁场的特性

空间中特定点的电磁场特性取决于： 
- 距辐射源的距离
- 频率
- 辐射天线的类型（线或者环）

描述空间任意特定点电磁场特性的最佳参数是波阻抗，其定义为，![[波阻抗定义式]]

## 1.2. 电磁波的传播方向

[[坡印廷矢量]]表示电磁场的方向。
$$
\vec{S} = \vec{E}\times \vec{H}
$$

## 1.3. 线天线辐射的波阻抗

[[《Chapter 1 射频干扰》笔记#1.1.3. 近场情况]]
[[《Chapter 1 射频干扰》笔记#1.1.2. 远场情况]]

## 1.4. 环天线辐射的波阻抗

## 1.5. 波阻抗与辐射源的关系

![[波阻抗与辐射源距离关系.png]]

以 $\dfrac{\lambda}{2\pi}$ 为界限区分近场和远场。在近场线天线有高波阻抗 $Z_{w}$，波阻抗变化率为 $\dfrac{1}{2\pi f\epsilon_{0}r}$；环天线有低波阻抗，变化率为 $2\pi f\mu_{0}r$。

## 1.6. 材料的电性能

电磁波传播到的任何材料的特性最好通过其特征阻抗来描述：
$$
Z_{0} = \sqrt{\frac{j \omega\mu} {\sigma\!+\! j \omega\varepsilon}} \; \; \Omega
$$
- $\mu_{0}=4 \pi\times1 0^{-7}$ H/m (using free space as reference) 
- $\epsilon_{0} = 8.854 \times 10^{-12}$ F/m (using free space as reference) 
- $\sigma_{0} = 5.82\times 10^{7}$ (using copper as reference)

对于绝缘体，$\sigma \ll j \omega \epsilon$，有 $Z_{0}=\sqrt{ \dfrac{\mu}{\epsilon } } \Omega$；
对于导体，$\sigma \gg j\omega \epsilon$，有 $Z_{0}=3.68\times 10^{-7}\sqrt{ f }\Omega$

# 2. 屏蔽有效性
## 2.1. 屏蔽有效性的定义

屏蔽可以根据材料引起的 E 或 H 场的减少来指定。常用的参数称为屏蔽效能 (SE)，通常以 dB 表示。
$$
S E_{E-f i e l d}=2 0 \operatorname{l o g} \frac{E_{i}} {E_{t}} ~ ~ \mathrm{d B}
$$
$$
S E_{H-f i e l d}=2 0 \operatorname{l o g} \frac{H_{i}} {H_{t}} ~ ~ \mathrm{d B}
$$
- $E_i$ 是入射电场强度，单位为 V/m
- $E_t$ 是透射电场强度，单位为 V/m
- $H_i$ 是入射磁场强度，单位为 A/m
- $H_t$ 是透射磁场强度，单位为 A/m

## 2.2. 屏蔽机制

![[屏蔽机制.png|300]]
屏蔽的主要部分由两种基本机制负责：
- 由于屏蔽材料中的功率耗散而导致的吸收损耗
- 由于电磁波穿过的两种不同介质之间的边界处的阻抗不匹配而导致的反射损耗

屏蔽取决于屏蔽材料的厚度，可能必须考虑屏蔽材料界面之间多重反射的影响。

# 3. 吸收损耗

这里先考虑材料对入射波的吸收损耗。
![[吸收损耗.png|300]]
当材料入射的时候，电场有衰减如下，$E (t) = E (0)\cdot e^{-\gamma t}$（磁场类似）。当屏蔽材料为金属的时候（$\sigma \gg j \omega \epsilon$），我们不考虑 $\beta$ 造成的相位偏移，因此只考虑 $\alpha$ 的衰减,
$$
\begin{align}
\gamma  & = \sqrt{ j\omega \mu \sigma } = \sqrt{ j 2 \pi f \mu \sigma } = (1+j)\sqrt{ \pi f \mu \sigma } = \sqrt{ \pi f \mu \sigma } + j\sqrt{ \pi f \mu \sigma } \\
 \alpha & =\sqrt{ \pi f \mu \sigma }
\end{align}
$$
因此透射材料的电场和磁场的幅度可以表示为，
$$
| E ( t ) | = | E ( 0 ) | e^{-\alpha t}
$$
由于波通过屏蔽层的衰减而产生的损耗称为吸收损耗：
$$
\frac{| E ( 0 ) |} {| E ( t ) |}=\frac{| H ( 0 ) |} {| H ( t ) |}=e^{\alpha t}
$$

![[材料吸收损耗计算式]]

## 3.1. Exercise 1

“Exercise #1 : Calculate the absorption loss of Brass with a thickness of 2 mm at 10 kHz, 100 kHz and 1 MHz. Electrical properties Brass: $\sigma_{r}$ = 0.26 and $\mu_{r}$ = 1.” (“EE6303 lec8 electromagnetic shielding”, p. 15)

![[《Chapter 6 电磁屏蔽》笔记.png]]
## 3.2. 决定吸收损耗的因素

![[《Chapter 6 电磁屏蔽》笔记_1.png|300]]

从公式可以看出，吸收损耗取决于：
- 材料的厚度
- 趋肤深度，取决于材料的电特性和电磁波频率

对于相同的材料厚度：
- 铜的趋肤深度 > 钢的趋肤深度
- 在相同频率下，钢比铜具有更高的吸收损耗。

# 4. 反射损耗
当电磁波入射材料的时候，会在材料的两个表面上发生两次反射。
![[第一次反射.png|200]]
第一次反射，
$$
\begin{aligned} {E_{t 1}} & {{}=E_{i}-E_{r 1}=E_{i}-\left( \frac{Z_{\mathrm{w}}-Z_{s}} {Z_{\mathrm{w}}+Z_{s}} \right) E_{i}} \\ {} & {{}=\frac{Z_{\mathrm{w}}+Z_{s}-\left( Z_{\mathrm{w}}-Z_{s} \right)} {Z_{\mathrm{w}}+Z_{s}} E_{i}} \\ 
& =\frac{2 Z_{s}} {Z_{w}+Z_{s}} E_{i}
\end{aligned}
$$
$$
\begin{aligned} {} & {{} H_{t 1}=H_{t}-H_{r 1}=H_{t}-\bigg( \frac{Z_{s}-Z_{w}} {Z_{w}+Z_{s}} \bigg) H_{i}} \\ {} & {{}=\frac{Z_{w}+Z_{s}-\big( Z_{s}-Z_{w} \big)} {Z_{w}+Z_{s}} H_{i}} \\ {} & {{}=\frac{2 Z_{w}} {Z_{w}+Z_{s}} H_{i}} \\ \end{aligned}
$$

![[第二次反射.png|300]]
同样的，能得到第二次透射的波为，
$$
E_{t_{2}} = \dfrac{4Z_{w}Z_{s}}{(Z_{w}+Z_{s})^{2}}E_{i}
$$
$$
H_{t_{2}} = \dfrac{4Z_{w}Z_{s}}{(Z_{w}+Z_{s})^{2}}H_{i}
$$
对于导体材料，有 $Z_s\ll Z_{w}$，所以将上式近似，
$$
E_{t 2} \approx{\frac{4 Z_{w} Z_{s}} {{Z_{w}}^{2}}} \, E_{i}={\frac{4 Z_{s}} {Z_{w}}} \, E_{i} \qquad H_{t 2} \approx{\frac{4 Z_{w} Z_{s}} {{Z_{w}}^{2}}} \, H_{i}={\frac{4 Z_{s}} {Z_{w}}} \, H_{i}
$$
于是有电场或者磁场的反射损失，
$$
R=2 0 \mathrm{l o g} \frac{| E_{i} |} {| E_{t 2} |}=2 0 \mathrm{l o g} \frac{| H_{i} |} {| H_{t 2} |}=2 0 \mathrm{l o g} \frac{| Z_{w} |} {4 | Z_{s} |}\quad \left[ \pu{dB}\right]
$$
始终有有 $\lvert Z_{s} \rvert=\sqrt{ \dfrac{\omega \mu}{\sigma} }$
对于远场有 $Z_{w}=377\Omega$。
$$
\begin{align}
\lvert Z_{w} \rvert  & =\dfrac{1}{2\pi f \varepsilon_{0} r} & \text{E场主导源} \\
\lvert Z_{w} \rvert  & =2\pi f \mu_{0} r & \text{H场主导源} 
\end{align}
$$
## 4.1. Exercise 2
“Exercise #2 : Calculate the absorption loss and reflection loss of Copper at 1 MHz with a thickness of 0.25 mm for the following conditions. Electrical properties of Copper: $\sigma_{r}$ = 1 and $\mu_{r}$ = 1.
- The field source is in the far-field region. 
- The field source is in the near field region ( 0.1 m from the shield) and dominated by electric field.
- The field source is in the near field region (0.1 m from the shield) and dominated by magnetic field.” (“EE6303 lec8 electromagnetic shielding”, p. 21)

首先算吸收损失，因为不用分情况讨论。然后分远场和近场，近场再分电场主导和磁场主导。材料阻抗计算方式不变，主要是空气的阻抗计算方式不同。

# 5. 磁场的多次反射校正因子

- 厚屏蔽 ($t>\delta$)：吸收损耗高，因此可以忽略多次反射 
- 薄屏蔽 ($t<\delta$)：取决于场源：
	- 近场（E 场）：忽略多次反射，因为大多数情况下，入射波在第一边界处被反射，只有一小部分进入屏蔽层
	- 近场（H 场）：大部分入射波在第一边界处进入屏蔽层，必须考虑多次反射的影响

磁场的多次反射校正因子为，
$$
B = 20\log_{10}(1-e^{-2t/\delta})\quad \left[ \pu{dB}\right]
$$
只有在近场且磁场主导的时候并且厚度 $t<\delta$ 的时候考虑。

# 6. 电磁屏蔽效率总结

![[电磁屏蔽计算公式总结.png]]
反射损耗为正，磁场的多次反射校正因子为负。

当波阻抗 $Z_{w}$ 非常高的时候，B 可以忽略；当波阻抗 $Z_{w}$ 非常小，并且材料的厚度 $t\leq \delta$ 的时候，就需要考虑多次反射校正因子。

# 7. 对于单开孔的屏蔽有效性的近似

前面的都是考虑在无限厚并且无开孔的情况下的屏蔽有效性。
![[孔或者矩形槽.png|300]]
当在屏蔽材料上有单开孔，例如直径为 $d$ 的圆形开孔（circuilar hole）或者最长长度为 $d$ 的矩形槽 (rectangular slot)，SE 会下降。
$$
\mathrm{S E}=2 0 \mathrm{l o g} \! \left( \frac{\lambda/ 2} {d} \right) \quad \left[ \pu{dB}\right], \mathrm{~ f o r ~ d < \lambda/ 2 ~}
$$
可以看到，当 $d$ 越大的时候，屏蔽有效性就会越低。直到 $d = \dfrac{\lambda}{2}$ 即半波长的时候完全丧失屏蔽性能。
![[单开孔 SE 和 频率的关系.png|300]]

# 8. 对于多开孔的屏蔽有效性的近似

![[多开孔.png|200]]
对于直径为 $d$，间距为 $s$ 的多开孔而言，在 $s\geq \dfrac{d}{2}$ 即孔之间有足够间距的情况下，有屏蔽有效性的近似为，
$$
\mathrm{S E}=2 0 \operatorname{l o g} \! \left( \frac{\lambda/ 2} {d} \right) \!-\! 1 0 \operatorname{l o g} n \quad \left[ \pu{dB}\right]
$$
$\lambda$ 为相关频率的波长； $d$ 为槽的较大尺寸或孔的直径； $n$ 为开孔的数量。

多开孔比单个大开孔的屏蔽有效性会更高。

# 9. 低于截止频率的圆形波导

![[共面波导#^4538fe]]
因此在设计圆形波导的时候，使得其截止频率高于工作频率即可起到电磁屏蔽的作用。

![[低于截止频率的圆形波导.png|200]]

$d$ 决定了截止频率（corner frequency）；$L$ 决定了衰减的大小。

![[圆形波导截止频率计算式]]
当 $f>=f_{c}$，SE 约为 0；当 $f<f_{c}$ 有 $\text{SE} = 32(\dfrac{L}{d})~ \left[\pu{dB}\right]$

$L=2d\to 64\pu{ dB }$；$L=3d\to 94\pu{ dB }$，一般来说会把长度 $L$ 限制在 $3\sim 4d$ 以内。

# 10. 低于截止频率的矩形波导

$$
f_{c}=\frac{1. 5 \times1 0^{8}} {d} \quad \left[ \pu{Hz}\right]
$$
同样当 $f\geq f_{c}$ 的时候，SE 接近 $0\pu{ dB }$；当 $f< f_{c}$ 的时候，有 $SE = 27.3\left( \dfrac{L}{d} \right)~ \left[\pu{dB}\right]$。
[[EE6303 例题合集#矩形波导]]

# 11. 屏蔽外壳的空腔谐振

所有矩形盒式金属外壳在某些频率下都成为空腔谐振器。在发生这种共振的频率下，盒子中出现最大磁场，SE 显着下降。通过给定的屏蔽外壳的尺寸（L、W、H），就能计算出所有能产生空腔谐振的频率。
$$
f_{mnl}=\frac{c} {2 \pi\sqrt{\mu_{r} \varepsilon_{r}}} \sqrt{\left( \frac{m \pi} {L} \right)^{2}+\left( \frac{n \pi} {W} \right)^{2}+\left( \frac{l \pi} {H} \right)^{2}} \quad \left[ \pu{Hz}\right]
$$

如果是充满空气的金属屏蔽外壳，可以简化公式为，
![[充满空气的金属屏蔽外壳空腔谐振频率计算式]]
[[EE6303 例题合集#空腔谐振]]
