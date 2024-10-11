---
title: Buck 电感电流
date: 2023-06-14 01:26
modification date: 2023 六月 14日 星期三 01:26:47
aliases:
  - 
tags:
  - 
publish: "true"
---

可近似认为电感电流的直流分量全部流入电阻 R，开关频率分量流入电容 C。

## 电感电流平均值 
$$
I_{L}=I_{o}=\frac{V_{o}}{R}
$$

## 电感电流脉动 
$$
I_{L\max}=I_{L}+\dfrac{1}{2}\Delta I_{L}^+
$$
$$
\begin{gathered}
 \Delta I_{L}^{+}=I_{L\operatorname*{max}}-I_{L\operatorname*{min}}=\frac{1}{L}\int_{0}^{D T_{s}}\left(\nu_{i}\left(t\right)-v_{o}\left(t\right)\right)d t=\frac{\left(V_{i}-V_{o}\right)D T_{s}}{L} \\
\Delta I_{L}^{-}=I_{L\min}-I_{L\max}=\frac{1}{L}\int_{D T_{s}}^{T_{s}}\left(-v_{o}\left(t\right)\right)c d t=\frac{-V_{o}\left(1-D\right)T_{s}}{L} 
\end{gathered}
$$
