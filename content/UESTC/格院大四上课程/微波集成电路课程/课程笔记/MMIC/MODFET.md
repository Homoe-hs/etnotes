---
对象类型: 器件
aliases:
  - 高电子迁移率晶体管
  - High Electron Mobility Transistors
  - 调制掺杂场效应晶体管
  - HEMT
  - 二维电子气场效应晶体管
  - two-dimensional electron gas field-effect transistor
  - TEGFET
  - 选择性掺杂异质结构晶体管
  - selectively doped heterostructure transistor
  - SDHT
  - 异质结场效应晶休管
  - heterojunction field-effect transistor
  - HFET
tags:
---
HEMT（高电子迁移率晶体管）是一种异质结 FET，其有高载流子迁移率。下面将考虑 GaAs HEMT，因为 MMIC 基板通常是 GaAs。对于 GaAs HEMT，另一种半导体材料是砷化铝镓 (AlGaAs)，它的带隙比 GaAs 更宽，并且是 n 型掺杂的。

## 结构

![[微波集成电路 Slides 总结_36.png]]
上图显示了 HEMT 器件的横截面。它由半绝缘砷化镓基片、未掺杂砷化镓层、未掺杂 GaAlAs 薄层组成。上面是 n 掺杂 GaAlAs 层。

## 二维电子气

在薄 n 掺杂 AlGaAs 层中产生的电子完全落入 GaAs 层中，形成耗尽的 AlGaAs 层（下图中未掺杂的 AlGaAs 间隔层）。这是由于不同带隙材料产生的异质结在 GaAs 的导带内形成了量子阱（或谷），如下图所示的能带图所示。它们被限制在这个谷内并形成了称为**二维电子气**（2-DEG）。由于 GaAs 层未掺杂，因此电子避免与任何杂质碰撞。

![[微波集成电路 Slides 总结_37.png]]

其效果是形成一个非常薄的高迁移电子层，其浓度非常高。电子的高迁移率和缺乏碰撞意味着它们可用于制造具有高工作频率和低噪声系数的晶体管。

一种相对较新的 HEMT 在 Si 或 SiC 衬底上使用 GaN 和氮化铝镓 (AlGaN)。 GaN HEMT 的工作漏极电压范围为 20–40 V，并且可以在低微波范围的频率下提供高达 100 W 的功率，使这些器件广泛用于高功率发射器。图 2 的等效电路模型也可用于 HEMT，并且 HEMT 的 DC 偏置特性与 MESFET 相似。