---
title: Boost 基本结构
date: 2023-06-13 23:17
modification date: 2023 六月 13日 星期二 23:17:49
aliases:
  - 
tags:
  - 
publish: "true"
---

Boost 通过降流的方式升压。输出平均电流和平均电压分别为，
$$
I_{o}=(1-D)I_{i}
$$
$$
V_{o}=\frac{1}{1-D}V_{i}
$$

![[Boost 基本结构_1.png|300]]

- 用电压源串联电感代替电流源
- 并列一个电感来平滑电压
- 使用二极管防止电容短接
