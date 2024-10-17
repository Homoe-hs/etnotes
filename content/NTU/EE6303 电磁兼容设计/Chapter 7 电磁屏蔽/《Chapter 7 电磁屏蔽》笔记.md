---
对象类型: 笔记
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 电磁场的特性

空间中特定点的电磁场特性取决于： 
- 距辐射源的距离
- 频率
- 辐射天线的类型（线或者环）

描述空间任意特定点电磁场特性的最佳参数是波阻抗，其定义为，![[波阻抗定义式]]

# 2. 电磁波的传播方向

坡印廷矢量表示电磁场的方向。
$$
\vec{S} = \vec{E}\times \vec{H}
$$

# 3. 线天线辐射的波阻抗

[[Chapter 2 射频干扰 笔记#1.1.3. 近场情况]]
[[Chapter 2 射频干扰 笔记#1.1.2. 远场情况]]


# 4. 环天线辐射的波阻抗

# 5. 波阻抗与辐射源的关系

![[波阻抗与辐射源距离关系.png]]

近场

# 6. 材料的电性能

电磁波传播到的任何材料的特性最好通过其特征阻抗来描述：
![[特征阻抗定义式]]

# 7. 吸收损耗

![[材料吸收损耗计算式]]

# 8. 反射损耗


# 9. 对于单开孔的屏蔽有效性的近似

![[孔或者矩形槽.png|300]]
当在屏蔽材料上有单开孔，例如直径为 $d$ 的圆形开孔或者最长长度为 $d$ 的矩形槽，SE 会下降。
$$
\mathrm{S E}=2 0 \mathrm{l o g} \! \left( \frac{\lambda/ 2} {d} \right) \mathrm{~ d B}, \mathrm{~ f o r ~ d < \lambda/ 2 ~}
$$ 可以看到，当 $d$ 越大的时候，屏蔽有效性就会越低。直到 $d = \dfrac{\lambda}{2}$ 的时候完全丧失屏蔽性能。
![[单开孔 SE 和 频率的关系.png|300]]

# 10. 对于多开孔的屏蔽有效性的近似

对于直径为 $d$，间距为 $s$ 的多开孔而言，在 $s\geq \dfrac{d}{2}$ 即孔之间有足够间距的情况下，有屏蔽有效性的近似为，
$$
\mathrm{S E}=2 0 \operatorname{l o g} \! \left( \frac{\lambda/ 2} {d} \right) \!-\! 1 0 \operatorname{l o g} n \quad \left[ \pu{dB}\right]
$$
$\lambda$ 为相关频率的波长； $d$ 为槽的较大尺寸或孔的直径； $n$ 为开孔的数量

# 低于截止频率的圆形波导

![[低于截止频率的圆形波导.png]]

$d$ 决定了角频率；$L$ 决定了。

$$
f_{c}=\frac{1. 7 5 3 \times1 0^{8}} {d} \, \, \mathrm{~ H z}
$$

$L=2d\to 64\pu{ dB }$；$L=3d\to 94\pu{ dB }$

# 低于截止频率的矩形波导

$$
f_{c}=\frac{1. 5 \times1 0^{8}} {d} \, \mathrm{~ H z}
$$

# 屏蔽外壳的空腔谐振


$$
f_{mnl}=\frac{c} {2 \pi\sqrt{\mu_{r} \varepsilon_{r}}} \sqrt{\left( \frac{m \pi} {L} \right)^{2}+\left( \frac{n \pi} {W} \right)^{2}+\left( \frac{l \pi} {H} \right)^{2}} \quad \left[ \pu{Hz}\right]
$$
所有可能发生空腔谐振的频率。

$$
f_{m n l}=1 5 0 \sqrt{\left( {\frac{m} {L}} \right)^{2}+\left( {\frac{n} {W}} \right)^{2}+\left( {\frac{l} {H}} \right)^{2}} \quad \left[ \pu{MHz}\right]
$$



