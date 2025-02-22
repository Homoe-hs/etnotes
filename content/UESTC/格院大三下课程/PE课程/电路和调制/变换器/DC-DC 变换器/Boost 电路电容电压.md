---
title: Boost 电路电容电压
date: 2023-06-14 03:21
modification date: 2023 六月 14日 星期三 03:21:28
aliases:
  - 
tags:
  - 
publish: "true"
---

电容充电时间：

$$
T_{r e c}=\frac{L}{R\left(1-D\right)}+\frac{1}{2}\left(1-D\right)T_{s}
$$

电容脉动电压：

$$
\Delta V_{C}=\frac{\left(T_{rec}-D T_{s}\right)V_{o}}{2C}\left(\frac{D}{\left(1-D\right)R}+\frac{\left(1-D\right)D T_{s}}{2L}\right)
$$

然而，实际中 S 关断时，电容 C 基本都处于充电状态，那么 C 放电仅存在于 S 导通时，可得：

$$
\Delta V_C=\Delta V_C^+\approx\frac{1}{C}\int_{0}^{D T_s}\frac{V_o}{R}dt=\frac{V_o D T_s}{CR}
$$
