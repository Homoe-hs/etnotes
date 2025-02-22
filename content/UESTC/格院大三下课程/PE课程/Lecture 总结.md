---
title: 未命名
date: 2023-06-15 02:04
modification date: 2023 六月 15日 星期四 02:04:31
aliases:
  - 
tags:
  - 
publish: "true"
---

![[Lecture 总结_6.png|400]]
![[Lecture 总结_2.png]]

## L 2 ave 和 rms 的计算

### 电感相关计算

![[电感电压计算式]]

电感储存能量
$$
W=\int p dt=\int i L di=\frac{1}{2}L i^2
$$

### 电容相关计算

![[电容电流计算式]]

电容储存能量
$$
W=\int p d t=\int C v d v=\frac{1}{2}C v^2
$$

### 电阻相关计算

电阻耗散功率（平均功率）
$$
p_{av}=i_{rms}^2R=\frac{V_{rms}^{2}}{R}
$$

### 平均值

$$
Y_{arv}=\frac{1}{T}\int \limits_0^T y(t)dt
$$

### 有效值

$$
Y_{rms}^2=\frac{1}{T}\int\limits_0^T y(t)^2dt
$$

### 典型波形的有效值、均值和波形因数

| 波形           | RMS                    | ARV              | FF                                  |
| -------------- | ---------------------- | ---------------- | ----------------------------------- |
| 正弦波         | $\frac{a}{\sqrt{ 2 }}$ | $\frac{2a}{\pi}$ | $\frac{\pi}{2\sqrt{ 2 }}$           |
| 半波整流正弦波 | $\frac{a}{2}$          | $\frac{a}{\pi}$  | $\frac{\pi}{2}$                     |
| 全波整流正弦波 | $\frac{a}{\sqrt{ 2 }}$ | $\frac{2a}{\pi}$ | $\frac{\pi}{2\sqrt{ 2 }}$           |
| 方波           | a                      | a                | 1                                   |
| 脉冲           | $a\sqrt{ D }$          | $aD$             | $\frac{1}{\sqrt{ D }}=\sqrt{ \frac{T}{\tau} }$                                    |
| 三角波         | $\frac{a}{\sqrt{ 3 }}$ | $\frac{a}{2}$    | $\frac{a}{\sqrt{ 3 }}\approx 1.154$ |

### 有直流偏置的正弦波的有效值

$$
V_{RMS}=\sqrt{\frac{A^2}{2}+B^2} \quad V_{TOTALrms}=\sqrt{\left(V_{ACrms}^2+V_{DCrms}^2\right)}
$$
A 为正弦波峰值；B 为直流偏置。

### MOSFET 特殊电流波形有效值

![[Lecture 总结_4.png|300]]

$$
I_{rms}^{2}=\frac{\phi}{3}\left[I^2_{off}+I_{off}I_{on}+I^2_{on}\right]
$$

### 全波可控硅相位角控制的平均电压和均方根电压的计算

![[Lecture 总结_5.png|400]]

$$
V_{avr}=\frac{A}{\pi}\left[1+\cos(\alpha)\right];0\le\alpha\le\pi
$$

$$
V_{rms}^{2}=\frac{A^2}{\pi}\left[\pi-\alpha+\frac{1}{2}\sin(2\alpha)\right]
$$

### 三角函数

![[Lecture 总结_3.png]]

## L 4 三种滤波电路和二极管的 PIV 和损耗的计算

### 二极管损耗计算

$$
\text{Losses}\colon P_{\text{Total}}=P_{\text{Conduction}}+P_{\text{Switching}}
$$

### 反向恢复电荷

$$
\mathbf{Q}_{rr}=\frac{\mathbf{I}_{rr}t_{rr}}{2}
$$

### 二极管导通损耗

$$
P_{cnd}=V_F\times I_F\times\phi
$$

### 反向恢复电流引起的二极管损耗

$$
P_{rr}=Q_{rr}\times V_{Block}\times f_{SW}
$$
### 功率二极管反向恢复效应

在 p-n 型二极管中正向传导结束后，反向电流会在短时间内流动。在结中的移动电荷耗尽之前，该设备不会获得其阻断能力。

### 功率二极管出现电压过冲的原因

电导调制效应起作用所需的大量少子需要一定的时间来储存，在达到稳态导通之前管压降较大；正向电流的上升会因器件自身的电感而产生较大压降。电流上升率越大，Up 越高。

### 半波滤波器

#### 优缺点

便宜简单；线圈使用率低。

#### PIV

$$
PIV=V_{p(in)}
$$

### 中间抽头

#### 缺点

1. 变压器次级绕组在任何时刻只有一半在使用；
2. 现在每个二极管两端的最大反向电压增加了一倍；
3. 半正弦波的频率现在加倍了。

#### 二极管的 PIV

$$
PIV=P_{sec}-0.7V=2V_{load}+0.7V
$$

### 全波桥式整流器

#### 纹波电压的计算

1. 忽略导通角

$$
\Delta V_{L}=\frac{I_{L}}{C}\cdot T
$$
2. 导通角 $\alpha$

$$
\Delta V_{L}=\frac{I_{L}}{C}\cdot \frac{\alpha}{180}\cdot T
$$

## L 5 器件性质、优缺点和使用场景

### 晶闸管

在门级给一定电流后建立发射级电流即可导通，由于负载存在因此电流有限。适用于高功率高压大电流。半控器件。阳极电流为 0 时关断。

### SCR

### MOSFET

#### 功耗计算

$$
P_{T o t a l}=I_{L o o d R M S}^{2}R_{D S (on)}+\left(\frac{F_{S W}.V_{D S (off)}}{2}\right)\left(T_{O N}I_{O N}+T_{O F F}I_{O F}\right)
$$

## L 6 热管理计算

### 等效热模型

![[Lecture 总结_7.png|350]]

温度从上到下逐渐减小。功耗类比电流，热阻类比热电阻，温度类比电压。

四点温度（1. Junction 2. Case 3. Heatsink 4. Ambient）三热阻（$1.\theta_{J C}\quad 2.\theta_{CS} \quad 3.\theta_{S A}$）

做提前先画等效热模型，再计算。

### 热电容

#### 热时间常数

$$
\tau=RC=\theta_{SA}\times C_{SA}
$$

#### 热容

$$
C_{S A}(J o u l e s\, p e r^{\circ}C)=H e a t\,C a p a c i t y(J\, p e r\, k g^{\circ}C)\times M a s s(k g)
$$
#### 升温时间

$$
\Delta T=\frac{P\times T}{C_{S A}}
$$
只要满足 $\tau\lt\Delta T$ 即可。

## L 7 缓冲电路

### 电路失效原因

1. 过热-热失效
2. 过电流-通常发生在导通过程中
3. 过电压-通常发生在关断过程中
4. 过高的 di/dt（电流变化率）
5. 过高的 dv/dt（电压变化率）
6. 开关损耗-过高的开关损耗是导致过热的主要因素之一。

### 缓冲电路的功能（对应失效原因）

- 在关断瞬态期间限制器件电压
- 在开启瞬态期间限制器件电流
- 在器件开启时限制电流的上升速率（di/dt）
- 在器件关断时限制电压的上升速率（dv/dt）
- 调整器件开启/关闭过程中的开关轨迹

### 缓冲电路的分类及应用

从电路拓扑的角度来看，缓冲电路可以分为三类：
1. 无极化串联 R-C 缓冲电路：用于保护二极管和可控硅
2. 极化 R-C 缓冲电路：
	- 用作关断缓冲电路，调整可控开关的关断开关轨迹
	- 用作过电压缓冲电路，将施加在可控开关上的电压限制到安全范围内；在器件关断时限制 dv/dt
3. 极化 L-R 缓冲电路：
	- 用作开启缓冲电路，调整可控开关的开启开关轨迹
	- 用作电流缓冲电路，在器件开启时限制 di/dt

### 电压缓冲电路

当缓冲电容是寄生电容的 3 倍并且电阻值等于未修改的谐振电路的特性阻抗时，可以获得最佳性能。
#### 合适电容和电阻的值

$$
C_{Snubber}=3\times C_{Switch}
$$

$$
R_{subber}=\sqrt{\frac{L_{stray}}{C_{switch}}}
$$
#### 振荡频率

$$
f=\frac{1}{2\pi\sqrt{LC_{Total}}}
$$

#### 电阻耗散

$$
P=f C V^2
$$

### 电流缓冲电路

#### 电阻耗散能量

$$
P_{Resistor}=\frac{1}{2}L_{Snubber}\times I_{Switch}\times f_{Switch}
$$

#### 电感和开关两端的峰值电压
$$
\mathbf{V}_{\mathrm{switch}}=\mathbf{V}_{\mathrm{supply}}+\mathbf{V}_{\mathrm{Df}}+(\hat{\mathrm{I}}_{\mathrm{switch}}\mathbf{R}_{\mathrm{smubber}}+\mathbf{V}_{\mathrm{Diode}})
$$

## L 8~L 9 降压电路

### Buck

$$
V_{OUT}=\phi\cdot V_{IN}
$$

### Boost

$$
V_{O U T}=\frac{V_{I N}}{1-\phi}
$$

### Buck-Boost

$$
V_{OUT}=\frac{\phi\cdot V_{IN}}{1-\phi}
$$

### 为什么要使用开关模式 dc-dc 转换？ 
- 与线性转换相比损耗更低
- 损耗更低
- 散热器更小
- 体积和重量更小
- 升压和降压动作。

## L 10~L 12 逆变器

### PWM 转换器输出

$$
\mathcal{V}_{out}=\frac{\mathcal{V}_{control}}{\hat{\mathcal{V}}_{carrier}}\times\mathcal{V}_{d}
$$
### PWM 波形输出时间

$$
t_{+on}=\frac{\nu_{c}-\left(-\hat{\nu}_{tri}\right)}{\widehat{\nu}_{tri}-\left(-\hat{\nu}_{tri}\right)}T=\left(\frac{\nu_{c}}{\hat{\nu}_{tri}}+1\right)\frac{T}{2}
$$

$$
t_{-o n}=T-t_{+o n}=\bigg(1-\frac{\nu_{c}}{\widehat{\nu}_{t r i}}\bigg)\frac{T}{2}
$$
### PWM 输出均值

$$
V_{A B(a v g)}=\frac{1}{T}\big(v_{d}t_{+o n}-v_{d}t_{-o n}\big)=v_{d}\biggl(\frac{v_{c}}{\hat{v}_{t r t}}\biggr)
$$
