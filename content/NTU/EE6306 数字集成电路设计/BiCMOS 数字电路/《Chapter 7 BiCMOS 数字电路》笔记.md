---
对象类型: 笔记
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 简介

CMOS 有很多优点，例如低功耗、高集成密度等，唯一的问题就是运行速度。ECL 门则是有高开关速度，问题是功耗高。

于是集成 MOS 和 BJT 得到了 BiCMOS。

# 2. BiCMOS 门概览
## 2.1. 双井 BiCMOS 工艺
![[Optimized twin-well BiCMOS structure with self-aligned p and n+  buried layers for improved packing density..png]]
不要求画，但是需要能识别。
双极封装密度可以通过将掩埋 p 层自对准到掩埋 n+区域来提高，从而收紧相邻阱之间的隔离间距。

- 单个 n 外延层用于实现 PMOS 晶体管和双极 npn 晶体管。控制其电阻率以使其能够支持两种器件。
- 外延层下方的 n+埋层降低了双极器件的集电极电阻，同时提高了对闩锁的免疫力。
- p 埋层提高了封装密度，从而可以减小双极器件的集电极-集电极间距。这是以增加集电极基板电容为代价的。

由于双极器件功耗的限制，早期的 BiCMOS 电路是 CMOS 密集型电路。因此，BiCMOS 技术倾向于从 CMOS 工艺发展而来。最初的方法是将辅助步骤移植到完善的 CMOS 工艺中，以生产双极器件而不降低 CMOS 晶体管的特性。

## 2.2. BiCMOS 门概览
与 ECL 和 CMOS 门的情况一样，BiCMOS 反相器有多种版本，每种版本的特性略有不同。讨论一个就足以说明门的基本概念和性质。  BiCMOS 门模板如图所示。
![[BiCMOS 门.png|200]]
与 TTL 门一样，两者都使用双极推挽输出级。在 BiCMOS 结构中，输入级和分相器采用 MOS 实现，从而具有更好的性能和更高的输入阻抗。输出则是用两个 n 型 BJT。

BiCMOS 和 CMOS 的行为是类似的，
![[《Chapter 7 BiCMOS 数字电路》笔记.png]]
当输入为高电平的时候，PUN 关闭，PDN 将输出下拉；当输入为低的时候，PDN 关闭，PUN 将输出上拉。其中，$Z_{1}$ 和 $Z_{2}$ 都是为了在 PDN 和 PUN 关闭的时候消耗基极电荷。

电压传输特性可以通过检查得出。电路的逻辑摆幅小于电源电压。例如 PUN 导通的时候，BJT 内部总有 0.7V 的导通压降 $V_{BE(on)}$，于是输出电压为 $V_{DD}-0.7$。所以实际的逻辑摆幅为 $V_{DD}-2V_{BE(on)}$，这不仅减小了噪声容限，并且增加了功率耗散。

$V_{out}$ 无法完全关闭后续栅极的 PMOS 晶体管，因为 VBE (on)  PMOS 阈值。这导致稳态漏电流和功耗。

## 2.3. BiCMOS 反相器的传播延迟

BiCMOS 反相器的传播延迟由两个部分组成：
1. 打开（关闭）BJT，以及 
2. 对负载电容器充电（放电）。

让 BJT 保持在饱和区之外非常重要。因为建立和消除饱和晶体管的基极电荷需要相当长的时间，并且会导致栅极速度变慢。BiCMOS 反相器的一个吸引人的特点是该结构可以防止 Q1 和 Q2 进入饱和状态。它们要么处于正向活动模式，要么处于关闭状态。
![[《Chapter 7 BiCMOS 数字电路》笔记_1.png|200]]
对于高输出电平，当达到 VOH 时，Q2 保持正向激活模式。 PMOS 晶体管 M2 充当电阻，确保 Q2 的集电极电压始终高于其基极电压。
![[《Chapter 7 BiCMOS 数字电路》笔记_2.png|200]]
同样，在低输出端，M1 充当 Q1 基极和集电极之间的电阻，防止器件饱和。基本电量保持在最低限度，并且设备可以快速打开和关闭。

## 2.4. 瞬态行为

可以合理地假设，对于典型的电容负载，延迟主要由电容器（放电）充电时间决定。
### 2.4.1. 低到高瞬态（$V_{out}$）

输出充电电流可以用 [[BJT 共发射极电流增益]]和通过 PMOS 的电流（$I_{B}$）来表示，
$$
\dfrac{(\beta_{F}+1)(V_{DD}-(V_{BE(on)}+V_{out}))}{R_{on}}
$$
$R_{on}$ 为PMOS 晶体管的等效导通电阻
### 2.4.2. 高到低瞬态（$V_{out}$）

同理，分析输出的电流有，
$$
\dfrac{(\beta_{F}+1)(V_{out}-V_{BE(on)})}{R_{on}}
$$

# 3. 静态行为和健壮性问题

BiCMOS 栅极中电阻元件的使用使其对于实际设计没有吸引力。比较流行的电路有：
![[《Chapter 7 BiCMOS 数字电路》笔记_3.png]]
## 3.1. BiCMOS 的优点*

高密度、低功耗 BiCMOS 逻辑阵列和高速双极驱动器的集成所产生的门阵列比同类 CMOS 更快，并且比具有相同密度的同类 ECL 阵列消耗的功率少得多。模拟和数字功能可以集成在同一 BiCMOS 芯片上，并且可以选择 TTL 或 ECL 接口。

代价就是工艺复杂，BiCMOS 是 CMOS 密集型（CMOS-intensive）工艺。

# 4. BiCMOS 反相器的性能
## 4.1. 从低到高的瞬态
假设输入信号切换速度非常快，并且其上升/下降时间可以忽略不计。并且 $Q_{1}$ 立即关闭对于传播延迟没有影响。
![[《Chapter 7 BiCMOS 数字电路》笔记_4.png|300]]
传播延迟由两个部分组成：
1. $C_{int}$ 需要通过 $M_{2}$ 充电到 $V_{BE}$ 以开启 $Q_{2}$；
2. Q2 开启后将充当发射极跟随器（emitter follower），并且 $C_L$ 会充电。

有 Q2 开启时间，$t_{turn-on} = \dfrac{C_{\text{int}}V_{BE(on)}}{I_{\text{charge1}}}$，这里的 $I_{\text{charge1}}$ 为平均充电电流，$I_{\text{charge1}} = \dfrac{I_{\text{M2}}(V_{\text{int}}=0)+I_{\text{M2}}(V_{\text{int}}=V_{BE(on)})-\dfrac{V_{BE(on)}}{Z_{2}}}{2}$。通常 $Z_{2}$ 是个大电阻，因此最后一项也可以不计。

$C_L$ 充电时间为，$t_{c h a r g e} \,=\, {\dfrac{\Big( C_{i n t}+{\dfrac{C_{L}} {\beta_{F}+1}} \Big) {\dfrac{V_{s w i n g}} {2}}} {I_{c h a r g e 2}}}$。这里 $V_{\text{swing}}= V_{DD}-2V_{BE(on)}$，$I_{\text{charge2}}\approx I_{\text{charge1}}$ ，即与平均 PMOS 充电电流相当，正如在具有相似尺寸器件的 CMOS 反相器中观察到的那样。

$$
\begin{array}{l}
t_{p L H} = t_{\text{turn-on}} + t_{\text{charge}} &  = \dfrac{C_{\text{int}} V_{B E (\text{on})}}{I_{\text{charge 1}}} \times \dfrac{\left( C_{\text{int}} + \dfrac{C_{L}}{\beta_{F} + 1} \right) \dfrac{V_{swing}}{2}}{I_{\text{charge2}}} \\
\\
 & = a \times C_{\text{int}} + \dfrac{b \times C_{L}}{\beta_{F} + 1}
\end{array}
$$
同理有，
$$
t_{p H L} \,=\, t_{t u r n-o n}+t_{d i s c h a r g e} \,=\, \dfrac{C_{i n t} V_{B E ( o n )}} {I_{c h a r g e 3}}+\dfrac{\bigg( C_{i n t}+\dfrac{C_{L}} {\beta_{F}+1} \bigg) \dfrac{V_{s w i n g}} {2}} {I_{c h a r g e 4}}
$$
## 4.2. 集电极电阻 $R_{C}$

等效电路忽略了外在集电极触点和本征集电极-基极结之间存在的集电极电阻 rc。即使外部 VCE 大于 0.7V，rc 上的压降也会导致晶体管饱和，正如 BiCMOS 缓冲器设计所保证的那样。例如，100 欧姆的集电极电阻传导 1 mA 的瞬态电流会导致 0.1 V 的电压降。在驱动大电容负载时，经常会观察到超过 5 mA 的电流。晶体管因此饱和，导致传播延迟恶化； tp 由使晶体管进入饱和状态的时间以及随后以时间常数 rCCL 进行负载电容放电的时间组成。这个问题可以通过增加晶体管的尺寸、降低 rC 来避免。

所以延迟在原本的基础上，改进为 $t_{p (HL, LH)} \,=\, t_{t u r n-o n}+t_{\text{sat}}+\alpha R_{C}C_{L}$。

# 5. 功耗*
# 6. 技术缩放*
# 7. 设计 BiCMOS 数字门*
# 8. 低压 BiCMOS 数字电路
