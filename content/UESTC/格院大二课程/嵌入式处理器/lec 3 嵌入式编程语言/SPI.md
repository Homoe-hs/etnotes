---
aliases:
  - Serial Peripheral Interface
  - 串行外设接口
tags: []
publish: "true"
---

# SPI
## 定义
SPI 是一种高速的全双工同步的通信总线。采用主从站结构，一个主站可对应多个从站。使用三种信号 Serial Data In (SDI)，Serial Data Out (SDO)，Serial Clock (SCK)。

## 结构
![[SPI结构.png]]
SCK：主站设置的串行时钟
SDI：主出从入
SDO：主入从出
SS（或CS）：从机选择或片选（从机是并联的）

## 工作方式
1. 主站通过SCK输出时钟信号。
2. 主站将SS/CS引脚切换到低电压状态，从而激活从站。
3. 主站每次沿 SDI 线向从站发送一个比特的数据，从机在接收到这些位时读取它们。
4. 如果需要响应，从机沿SDO线每次向主机返回一个比特的数据。主站在收到这些位时读取它们。

## 优点
- 全双工通信
- 高速度，最高能够达到 10Mpbs
- 不限于 8-bit 字
- 比 I2C更低的能耗需求

