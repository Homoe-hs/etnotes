---
aliases:
  - 绝缘栅型场效应管
  - 绝缘栅效应晶体管
  - 金属-氧化物半导体场效应晶体管
  - metal-oxide-semiconductor field-effect transistor
  - insulated gate FET
  - IGFET
tags:
  - 实体
publish: "true"
---
MOSFET 是一种可以广泛使用在模拟电路与数字电路的场效应晶体管，起着类似于开关的作用。

## 结构

![[MOSFET_2.png|625]]

MOSFET 外部有三个端口，分别是栅极（G）、源级（S）、漏极（D）。栅极用于控制 MOSFET 的开关状态，源级是载流子产生的地方，漏极是接收载流子的地方。在栅极接触和沟道区之间具有薄绝缘层 （$\text{SiO}_{2}$ ）, 因此不同于 MESFET。栅极是绝缘的，它不会导通直流偏置电流。

## 小信号等效模型

MOSFET 的小信号等效电路与 MESFET 的相同。
![[MESFET_2.png]]

## 分类

![[MOSFET 的分类]]

## 最小特征尺寸

一般存储器件的最小特征尺寸是由金属接触间隔决定，而对于处理器等则是栅极长度。