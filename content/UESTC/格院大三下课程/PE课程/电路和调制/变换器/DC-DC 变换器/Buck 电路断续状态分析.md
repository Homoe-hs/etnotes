---
title: Buck 电路断续状态分析
date: 2023-06-14 02:04
modification date: 2023 六月 14日 星期三 02:04:08
aliases:
  - 
tags:
  - 
publish: "true"
---

可以认为，当电感电流为 0 的时候，Buck 电路出现了断续的情况。
$$
L_{\min}=\frac{\left(1-D\right)R}{2f}
$$
$L_{min}$ 即为电流连续与断续的临界值。当 $L\lt L_{min}$ 时电感电流断续； $L\ge L_{min}$ 时电感电流连续。
