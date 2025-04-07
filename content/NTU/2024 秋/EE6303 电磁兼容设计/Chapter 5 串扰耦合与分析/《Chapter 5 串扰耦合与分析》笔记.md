---
aliases: []
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 引入

当电路存在电压的时候，就会形成电场耦合；当电路存在电流的时候，就存在磁场耦合。于是当两个电路靠得非常近的时候，就会产生串扰。

串扰会对相邻电路产生噪声，由此导致信号完整性下降、减少噪声容限。

## 1.1. 并联微带线

![[并联微带线 串扰.png]]

当电压增加的时候，会造成干扰。


# 2. 频域串扰分析

![[频域串扰分析示例.png]]
攻击线在受害线的两端观察到串扰信号。

- Near End：受害线更靠近攻击线的电源的一端。
- Far End：受害线更远离攻击线电源的一端。

需要分析的就是攻击线路导致的 $V_{NE}$ 和 $V_{FE}$。
远端串扰为 $\dfrac{V_{FE}}{V_{G}}$，近端串扰为 $\dfrac{V_{NE}}{V_{G}}$

## 2.1. 平行线的分布参数

我们需要知道平行线的分布电感和电容来确定串扰。RLCG 模型，R 是串联的电阻，L 是自感和互感，C 是自容和互容，G 是连接到地的电阻。
![[平行线的分布电感和电容来确定串扰.png]]
- Ls1 = 导体 1 单位长度的自感 (H/m) 
- Ls2 = 导体 2 单位长度的自感 (H/m) 
- Lm = 导体 1 和 2 之间单位长度的互感 (H/m) 
- Cs1 = 导体 1 单位长度的自电容 (F/m) 
- Cs2 = 导体 2 单位长度的自电容 (F/m) 
- Cm = 导体 1 和 2 之间单位长度的互电容 (F/m)
在分析串扰的时候，我们更关心自感、互感和自容、互容。

为了简化分析，这里假设了频率足够低 $l\ll \lambda$，我们用集总电路模型来分析。将上面的电路用集总电路建模，并且分电容和电感来分析。
![[集总电路建模分析串扰.png]]
通过单位电容、单位电感和长度就能计算出自自容、自感等，
$$
\begin{gathered}
C_{1}=C_{s1}\times l & L_{1}=L_{s1}\times l \\
C_{2}=C_{s2}\times l & L_{2}=L_{s2}\times l \\
C_{12}=C_{m}\times l & M_{_{12}}=L_{_m}\times l 
\end{gathered}
$$
## 2.2. 电容串扰

大多数情况下，两条平行线具有相同的分布参数和终端电阻。即假设所有电阻相同以及电容相同。

![[电容串扰分析.png]]

由此能分析出来，由于电容串扰产生的干扰为，
$$
\frac{V_{NE}}{V_{G}}=\frac{V_{FE}}{V_{G}}=\frac{j\omega C_{12}R}{4-\omega^{2}R^{2}C^{2}\left(1+\dfrac{2C_{12}}{C}\right)+j4\omega R\left(C_{12}+C\right)}
$$
可以看到这个公式的分母由三个部分组成，并且分别是，不和频率相关，和 $\omega^{2}$ 相关，和 $\omega$ 相关。由此，
- 当低频时，第一项为主，其他项可忽略
- 当频率增加，第三项为主，其他项可忽略；
- 当频率增加地更多，第二项为主，其他项可忽略。

但是这个界限在哪？我们通过对比项之间的大小可以得知。
$$
\begin{aligned}
\text{当有~}\omega=\omega_{1} \\
&4\omega_{1}R\left(C_{12}+C\right)=4 \\
&\omega_{1}=\frac{1}{R\left(C_{12}+C\right)} \\
\\
\text{当有~}\omega=\omega_{2} \\
&\omega_{2}{}^{2}R^{2}C^{2}\left(1+\frac{2C_{12}}{C}\right)=4\omega_{2}R\left(C_{12}+C\right) \\
&\omega_{2}RC\left(C+2C_{12}\right)=4\left(C_{12}+C\right) \\
&\omega_{2}=\frac{4\left(C_{12}+C\right)}{RC\left(C+2C_{12}\right)}
\end{aligned}
$$
于是可以有以下近似，
$$
\begin{aligned}
\omega<\omega_{_1}: \\
&\frac{V_{NE}}{V_{G}}=\frac{V_{FE}}{V_{G}}\approx\frac{j\omega C_{12}R}{4} C \\
\omega_{1}<\omega<\omega_{2}: \\
&\frac{V_{NE}}{V_{G}} =\frac{V_{FE}}{V_{G}}\approx\frac{j\omega C_{12}R}{j4\omega R\left(C_{12}+C\right)}=\frac{C_{12}}{4\left(C_{12}+C\right)} \\
\omega>\omega_{2}: \\
&\frac{V_{NE}}{V_{G}}=\frac{V_{FE}}{V_{G}}\approx\frac{j\omega C_{12}R}{-\omega^{2}R^{2}C^{2}\left(1+\frac{2C_{12}}{C}\right)}=\frac{C_{12}}{j\omega RC\left(C+2C_{12}\right)} 
\end{aligned}
$$
在 $\omega<\omega_{1}$ 的时候，电容串扰随着频率线性增加；$\omega_{1}<\omega>\omega_{2}$ 串扰为固定值；$\omega_{2}<\omega$ 串扰随着频率增加而减少。

### 2.2.1. Exercise 1

“Determine the near-end and far-end capacitive crosstalk for the two parallel microstrip lines at 100 kHz and 10 MHz for: (a) RG = RL = RNE = RFE = 10 $k\Omega$; (b) RG = RL = RNE = RFE = 10 $\Omega$ .” (“EE6303 lec7 crosstalk coupling and analysis”, p. 18)
![[练习1.png]]

### 2.2.2. 电容串扰特性
![[电容串扰特性.png]]
- 近端和远端电容串扰具有相同的幅度和同相。
- 电容串扰随频率以+20dB/十倍频程的速率增加，在特定频率处达到最大值，然后随频率以+20dB/decade 的速率减小。 –20dB/十年。
- 具有高阻抗端子的电路更容易受到电容串扰的影响

## 2.3. 电感串扰
$$
\begin{align}
&\frac{V_{NE}}{V_{G}}=\frac{j\omega M_{12}R}{4R^{2}+j4\omega RL-\omega^{2}\left(L^{2}-M_{12}^{2}\right)} \\
&\frac{V_{FE}}{V_{G}}=-\frac{V_{NE}}{V_{G}}
\end{align}
$$
和电容串扰类似，
- 当 $\omega$ 低的时候，$4R^{2}$ 主导；
- 当 $\omega$ 增加的时候，$j 4\omega RL$ 主导串扰；
- 当 $\omega$ 继续增加的时候，$\omega^{2}(L^{2}-M_{12}^{2})$ 主导串扰；

所以，我们也能在不同频率下来近似计算。
当 $\omega=\omega_{1} \colon$ 
$$
\begin{array}
 {l} {4 \omega_{1} R L=4 R^{2}} \\ {\omega_{1}=\displaystyle\frac{R} {L}} \\  \\
\end{array}
$$
当 $\boldsymbol{\omega}=\boldsymbol{\omega}_{2}$，
$$
\begin{array} {l} {4 \omega_{2} R L={\omega_{2}}^{2} \left( L^{2}-{M_{1 2}}^{2} \right)} \\ {4 R L=\omega_{2} \left( L^{2}-{M_{1 2}}^{2} \right)} \\ {\omega_{2}={\dfrac{4 R L} {L^{2}-{M_{1 2}}^{2}}}} \\ \end{array}
$$
所以有，
当 $\omega < \omega_{1}$ 时，
$$
\frac{V_{\scriptscriptstyle{N E}}} {V_{\scriptscriptstyle{G}}}=-\frac{V_{\scriptscriptstyle{F E}}} {V_{\scriptscriptstyle{G}}} \approx\frac{j \omega M_{\scriptscriptstyle{1 2}} R} {4 R^{2}} \!=\! \frac{j \omega M_{\scriptscriptstyle{1 2}}} {4 R}
$$
当 $\omega_{1}<\omega < \omega_{2}$ 时，
$$
\frac{V_{N E}} {V_{G}}=-\frac{V_{F E}} {V_{G}} \approx\frac{j \omega M_{1 2} R} {j 4 \omega R L} \!=\! \frac{M_{1 2}} {4 L}
$$
当 $\omega_{2}<\omega$ 时，
$$
\frac{V_{N E}} {V_{G}}=-\frac{V_{F E}} {V_{G}} \!=\! \frac{j \omega M_{1 2} R} {-\omega^{2} \left( L^{2}-{M_{1 2}}^{2} \right)} \!=\! \frac{M_{1 2} R} {j \omega\left( L^{2}-{M_{1 2}}^{2} \right)}
$$

### 2.3.1. 电感串扰特性

![[电感串扰特性.png]]
- 近端和远端感应串扰异相（注意：观察接地电压的极性）。
- 感应串扰随频率以+20dB/十倍频程的速率增加，在特定频率处达到最大值，然后随频率以-20dB/十倍频程的速率下降。
- 具有低阻抗端子的电路更容易受到电感串扰的影响。

## 2.4. 串扰产生的能量

![[串扰产生的能量.png]]
通过观察电容串扰和电感串扰的频率响应，大多数能量主要集中在低频频谱中。在较高频率下，能量会恶化，因为串扰与频率成反比。较低频谱的串扰是主要问题。

同样，我们将电路分为电容串扰和电感串扰来说明，并且只考虑低频情况。此时有电容串扰为，
$$
\frac{V_{{\scriptscriptstyle N E}}} {V_{{\scriptscriptstyle G}}}=\frac{V_{{\scriptscriptstyle F E}}} {V_{{\scriptscriptstyle G}}} \approx\frac{j \omega C_{1 2} R} {4}
$$
电感串扰为，
$$
{\frac{V_{{\scriptscriptstyle N E}}} {V_{\scriptscriptstyle G}}}=-{\frac{V_{{\scriptscriptstyle F E}}} {V_{\scriptscriptstyle G}}} \approx{\frac{j \omega M_{1 2}} {4 R}}
$$
### 2.4.1. 低频电容串扰
在低频下有电容串扰，
$$
\frac{V_{N E}} {V_{G}}=\frac{V_{F E}} {V_{G}}=\frac{j \omega C_{1 2} R} {4}
$$

$$
V_{\scriptscriptstyle N E}=V_{\scriptscriptstyle F E}=\frac{j \omega C_{\scriptscriptstyle{1 2}} R V_{\scriptscriptstyle G}} {4}=\frac{j \omega C_{\scriptscriptstyle{1 2}} V_{\scriptscriptstyle G}} {2} \Biggl( \frac{R} {2} \Biggr)
$$
电容耦合可以被建模为从干扰源线路到受害线路的耦合噪声电流源 $I_{N}$。
![[1.png]]
$$
V_{{\scriptscriptstyle N E}}=V_{{\scriptscriptstyle F E}}=I_{\scriptscriptstyle N} \Biggl( {\frac{R} {2}} \Biggr), \; \; \; \mathrm{w h e r e} \; I_{\scriptscriptstyle N}={\frac{j \omega C_{\scriptscriptstyle1 2} V_{\scriptscriptstyle G}} {2}}
$$

### 2.4.2. 低频电感串扰
$$
\frac{V_{{\scriptscriptstyle N E}}} {V_{{\scriptscriptstyle G}}}=-\frac{V_{{\scriptscriptstyle F E}}} {V_{{\scriptscriptstyle G}}}=\frac{j \omega M_{1 2}} {4 R}
$$
$$
V_{{\scriptscriptstyle N E}}=-V_{{\scriptscriptstyle F E}}=\frac{j \omega M_{1 2} V_{\scriptscriptstyle G}} {4 R} \!=\! \left( \frac{j \omega M_{1 2} V_{\scriptscriptstyle G}} {2 R} \right) \! \left( \frac{1} {2} \right)
$$
电感耦合可以被建模为从干扰源线路到受害线路的耦合噪声电压源 $V_{N}$。
![[电感耦合.png]]
$$
V_{{\scriptscriptstyle N E}}=-V_{{\scriptscriptstyle F E}}={\frac{V_{\scriptscriptstyle N}} {2}}, \; \; \; {\mathrm{w h e r e}} \; V_{\scriptscriptstyle N}={\frac{j \omega M_{\scriptscriptstyle1 2} V_{\scriptscriptstyle G}} {2 R}}
$$
### 2.4.3. 电容加电感耦合

![[电感耦合加电容耦合.png]]
$$
V_{{\tiny N E}}=V_{{\tiny N E}, C A P}+V_{{\tiny N E}, D B}=I_{{\tiny N}} \left( {\frac{R} {2}} \right)+{\frac{V_{\tiny N}} {2}} 
$$
$$
V_{{\tiny F E}}=V_{{\tiny F E}, C A P}+V_{{\tiny F E}, D B D}=I_{{\tiny N}} \left( {\frac{R} {2}} \right)-{\frac{V_{\tiny N}} {2}}
$$
$$
I_{N}=\frac{j \omega C_{1 2} V_{G}} {2} \qquad\qquad\qquad V_{N}=\frac{j \omega M_{1 2} V_{G}} {2 R}
$$

# 3. 时域串扰分析
## 3.1. 数字信号的传播延迟

![[《Chapter 5 串扰耦合与分析》笔记.png]]
信号的传播速度：
$$
v = \dfrac{c}{\sqrt{ \epsilon_{r} }} \quad \left[ \pu{m/s}\right]
$$
单位长度的传播延迟为，
$$
PD = \dfrac{1}{v} = \dfrac{\sqrt{ \epsilon_{r} }}{c}\quad \left[ \pu{s/m}\right]
$$
信号的传播延迟为，
$$
t_{d} = PD \times l = \dfrac{l\sqrt{ \epsilon_{r} }}{c} \quad \left[ \pu{s}\right]
$$
## 3.2. 时域串扰分析

![[《Chapter 5 串扰耦合与分析》笔记_1.png]]
$$
I_{N} ( t ) \!=\! \left( \frac{C_{1 2}} {2} \right) \! \frac{d V_{G} ( t )} {d t}
$$
$$
V_{{}_{N}} \left( t \right)=M_{{}_{1 2}} \, \frac{d I_{G} \left( t \right)} {d t}
$$
有时域串扰，
$$
V_{N \mathbb{E}} \left( t \right) \!=\! {\frac{I_{N} \left( t \right) R} {2}} \!+\! {\frac{V_{N} \left( t \right)} {2}} \qquad\! V_{F \mathbb{E}} \left( t \right) \!=\! {\frac{I_{N} \left( t \right) R} {2}} \!-\! {\frac{V_{N} \left( t \right)} {2}}
$$
### 3.2.1. 时域的电容串扰

![[《Chapter 5 串扰耦合与分析》笔记_2.png]]

### 3.2.2. 时域的电感串扰

![[《Chapter 5 串扰耦合与分析》笔记_3.png]]

