---
title: Buck 电路稳态增益分析
date: 2023-06-14 00:46
modification date: 2023 六月 14日 星期三 00:46:26
aliases:
  - 
tags:
  - 
publish: "true"
---

![[稳态增益计算]]

电感 L 上的电压 $V_{L}$ 为，
1. 当 S 导通的时候，$V_{L}=V_{i}-V_{o}$
2. 当 S 关断时，$V_L=-V_o$

根据能量守恒可知，电感电流在一个周期内变化为 0，
$$
\int^{DT_{s}}_{0}[v_{i}(t)-v_{o}(t)]  \, dt+\int ^{T_{s}}_{DT_{s}}[-v_{o(t)}] \, dt=0  
$$

解得 ![[Buck 电路稳态增益#^d7725c]]
