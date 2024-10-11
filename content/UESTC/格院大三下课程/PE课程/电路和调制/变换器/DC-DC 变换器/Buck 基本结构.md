---
title: Buck 基本结构
date: 2023-06-13 23:16
modification date: 2023 六月 13日 星期二 23:16:06
aliases:
  - 
tags:
  - 
publish: "true"
---

Buck 电路实现降压。输出电压均值等于，

$$
V_{o}=D\times V_{i}
$$

![[DC-DC 变换器基本结构_1.png|300]]

- 通过电容 C 平滑输出电压
- 通过电感 L 抑制电容的电流突变![[电容电流计算式]]
- 通过续流二极管为电感 L 提供续流回路
