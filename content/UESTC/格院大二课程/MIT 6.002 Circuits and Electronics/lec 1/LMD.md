---
aliases:
  - Lumped Matter Disciplines
  - 集总事物原则
tags: []
publish: "true"
---

# 集总事物原则
## 什么是 LMD
集总元件和用这种元件构成的电路，必须满足一系列约束，才能使这些定义以及接线端之间的相互作用有意义，我们将这些约束定义为集总事物原则。LMD 是电气工程中一组强加的假设，为网络分析中使用的集总电路抽象提供了基础。

如果元件满足集总事物原则，则可以忽略连接元件的导线的物理长度和拓扑结构，同时可定义元件的电压和电流。

## 集总元件的 LMD 约束
1. 对集总元件边界的选择需要在所有时刻使元件与外部任何闭环链接的磁链的变化率为零。换句话说，需要选择元件的边界使得一下公式对任何元件外部的闭通路成立。$$\dfrac{\partial \, \Phi_{B}}{\partial \,  t}=0 $$ 第一个约束背后的直觉是：元件两点间电压（或电位差）定义为将带有单位电荷的微粒从一端沿着某条通路逆着电场力移动到另一端克服电场力所做的功。因为要遵循集总抽象，需要该电压是**唯一**的，从而使得电压值不依赖于路径的选择。我们可通过选择元件的边界使得元件外部没有随时间变化的磁链，从而使其成立。 
2. 对集总元件边界的选择需要在所有时刻使元件内部总的随时间变化的电荷量为零。换句话说，需要选择元件的边界使得以下公式成立。其中 q 是元件内部的总电荷。$$\dfrac{\partial \, q}{\partial \, t}=0 $$ 第二个约束导致我们可定义唯一的流入并流出元件接线端的电流。如果随着时间变化，在元件内部没有电荷堆积或消耗，则可定义唯一的电流值。
3. 该元件在这样一种情况下工作：感兴趣的信号的时间尺度比电磁波通过集总元件时的传播延迟长得多。换句话说，我们的集总元件的尺寸必须比与 V 和 I 信号有关的波长小得多。在上述速度约束下，电磁波可以被视为在集总元件中瞬间传播。通过忽略传播效应，集总元件近似可类比为质点简化。在质点简化中可以忽略元件的物理特性，如长度、形状、大小和位置。波现象对微处理器设计越来越重要。

The first two assumptions result in Kirchhoff's circuit laws when applied to [[麦克斯韦方程组|Maxwell's equations]] and are only applicable when the circuit is in **steady state**. The third assumption is the basis of the lumped element model used in network analysis. Less severe assumptions result in the distributed element model, while still not requiring the direct application of the full Maxwell equations.

## 集总电路的 LMD 约束
1. 所有时刻与电路任意部分链接的磁链的变化率均为零。 
2. 所有时刻电路任意节点上电荷的变化率必须为零。节点就是电路中两个或更多元件接线端用导线相连的任意点。 
3. 信号的时间范围必须远大千电磁波通过电路的传播延迟。
