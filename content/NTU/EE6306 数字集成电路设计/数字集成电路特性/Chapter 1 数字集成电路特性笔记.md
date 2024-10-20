---
date: 2024-08-13 13:51
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
>[! tip] 
>如果想了解物理基础的，可以看《半导体物理与器件》的量子物理和固态物理相关章节。

>[! warning] 
>这一章节的内容可以看作为综述，牵扯了很多，但是又讲得很乱。很多东西没有推导，只有结论。
>
>其次就是没有任何例题！最好看看教材，然后做做教材课后的作业。
>

# 1. PN 结和二极管方程

![[PN 结]]

对于一个理想的 pn 结，我们通常用简单的开关-电阻模型来近似。

![[理想二极管模型]]

# 2. MOS 晶体管

以下讨论的均为理想长沟道 NMOS 器件。

## 2.1. NMOS 结构

![[NMOS 结构]]

## 2.2. 理想 NMOS 工作模式

![[理想 NMOS 的工作模式]]
### 2.2.1. PMOS

![[PMOS]]

## 2.3. MOS 晶体管类型和符号

![[EE6306 数字集成电路设计笔记_6.png|625]]

## 2.4. NMOS 的简单开关模型

![[MOS 的简单开关模型]]

## 2.5. 阈值电压

阈电压是第一个需要关注的点，阈电压的存在使得 NMOS 能处于开和关两个状态。栅源电压越大，下方吸引的电子越多，形成的沟道就越深。

![[阈电压]]

这里，NMOS 的费米能级为，
![[NMOS 费米能级计算式]]

## 2.6. 体效应

但是阈值电压并非一成不变的，其受到很多外在因素的影响，其中之一就是体效应。

![[体效应]]

## 2.7. 沟道夹断

当通道形成之后，我们需要在通道的两端，即漏源之间产生电压差以驱动电子的移动。但是 $V_{d}$ 的增加会导致漏和衬底之间产生耗尽层，这个耗尽层会挤压通道，使得通道在靠近漏的一段更小。

![[数字集成电路特性笔记_1.png|625]]

这里 $V_{gs}-V_{t}$ 可以形象地理解为形成的通道宽度，$V_{ds}$ 则是漏和衬底之间形成的耗尽层厚度。耗尽层厚度大于等于通道宽度的时候，就会形成通道夹断。

理论上沟道已经夹断，但是夹断点非常薄弱。电子冲出夹断点后，同样也会被漏极收集。

漏极电压越高，夹断点越后退，造成电子越难穿越，因此饱和区电流不再随电压增大而线性增大。因此夹断点之后进入饱和区。

如果漏极的电压继续上升，它的空间电荷区持续扩张达到源极，那么源极的电子就会不受沟道和栅压的控制，直接经过空间电荷区高速到达漏极，这就是源漏直接穿通了，这时 MOS 管也就直接损坏了

## 2.8. NMOS 线性区

![[NMOS 线性区]]

## 2.9. NMOS 饱和区

![[NMOS 饱和区]]
