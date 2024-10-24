---
对象类型: 笔记
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
笔记是否完成: false
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

# 9. 磁场的多次反射校正因子



# 10. 电磁屏蔽效率总结

![[电磁屏蔽计算公式总结.png]]
反射损耗为正，磁场的多次反射校正因子为负。

当波阻抗 $Z_{w}$ 非常高的时候，B 可以忽略；当波阻抗 $Z_{w}$ 非常小，并且材料的厚度 $t\leq \delta$ 的时候，就需要考虑多次反射校正因子。

# 11. 对于单开孔的屏蔽有效性的近似

前面的都是考虑在无限厚并且无开孔的情况下的屏蔽有效性。
![[孔或者矩形槽.png|300]]
当在屏蔽材料上有单开孔，例如直径为 $d$ 的圆形开孔（circuilar hole）或者最长长度为 $d$ 的矩形槽 (rectangular slot)，SE 会下降。
$$
\mathrm{S E}=2 0 \mathrm{l o g} \! \left( \frac{\lambda/ 2} {d} \right) \quad \left[ \pu{dB}\right], \mathrm{~ f o r ~ d < \lambda/ 2 ~}
$$
可以看到，当 $d$ 越大的时候，屏蔽有效性就会越低。直到 $d = \dfrac{\lambda}{2}$ 即半波长的时候完全丧失屏蔽性能。
![[单开孔 SE 和 频率的关系.png|300]]

# 12. 对于多开孔的屏蔽有效性的近似

![[多开孔.png|200]]
对于直径为 $d$，间距为 $s$ 的多开孔而言，在 $s\geq \dfrac{d}{2}$ 即孔之间有足够间距的情况下，有屏蔽有效性的近似为，
$$
\mathrm{S E}=2 0 \operatorname{l o g} \! \left( \frac{\lambda/ 2} {d} \right) \!-\! 1 0 \operatorname{l o g} n \quad \left[ \pu{dB}\right]
$$
$\lambda$ 为相关频率的波长； $d$ 为槽的较大尺寸或孔的直径； $n$ 为开孔的数量。

多开孔比单个大开孔的屏蔽有效性会更高。

# 13. 低于截止频率的圆形波导

![[共面波导#^4538fe]]
因此在设计圆形波导的时候，使得其截止频率高于工作频率即可起到电磁屏蔽的作用。

![[低于截止频率的圆形波导.png|200]]

$d$ 决定了截止频率（corner frequency）；$L$ 决定了衰减的大小。

![[圆形波导截止频率计算式]]
当 $f>=f_{c}$，SE 约为 0；当 $f<f_{c}$ 有 $\text{SE} = 32(\dfrac{L}{d})~ \left[\pu{dB}\right]$

$L=2d\to 64\pu{ dB }$；$L=3d\to 94\pu{ dB }$，一般来说会把长度 $L$ 限制在 $3\sim 4d$ 以内。

# 14. 低于截止频率的矩形波导

$$
f_{c}=\frac{1. 5 \times1 0^{8}} {d} \quad \left[ \pu{Hz}\right]
$$
同样当 $f\geq f_{c}$ 的时候，SE 接近 $0\pu{ dB }$；当 $f< f_{c}$ 的时候，有 $SE = 27.3\left( \dfrac{L}{d} \right)~ \left[\pu{dB}\right]$。
[[EE6303 例题合集#矩形波导]]

# 15. 屏蔽外壳的空腔谐振

所有矩形盒式金属外壳在某些频率下都成为空腔谐振器。在发生这种共振的频率下，盒子中出现最大磁场，SE 显着下降。通过给定的屏蔽外壳的尺寸（L、W、H），就能计算出所有能产生空腔谐振的频率。
$$
f_{mnl}=\frac{c} {2 \pi\sqrt{\mu_{r} \varepsilon_{r}}} \sqrt{\left( \frac{m \pi} {L} \right)^{2}+\left( \frac{n \pi} {W} \right)^{2}+\left( \frac{l \pi} {H} \right)^{2}} \quad \left[ \pu{Hz}\right]
$$

如果是充满空气的金属屏蔽外壳，可以简化公式为，
![[充满空气的金属屏蔽外壳空腔谐振频率计算式]]
[[EE6303 例题合集#空腔谐振]]
