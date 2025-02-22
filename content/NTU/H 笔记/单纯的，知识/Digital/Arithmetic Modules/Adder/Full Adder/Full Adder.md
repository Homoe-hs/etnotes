---
aliases:
  - 全加器
tags:
  - adder
  - digital
  - arthmetic_modules
---

- A Full Adder (FA) has 2 adder inputs ($A$, $A$), 1 carry input ($C_i$), a sum output ($S$) and a carry output ($C_o$)
  一个全加器（FA）有两个加法输入（$A$，$B$）、一个进位输入（$C_i$）、一个和输出（$S$）和一个进位输出（$C_o$）
- Boolean equations are:
  布尔表达式：$$\displaylines{S=A\oplus B \oplus C_i \\ C_o=AB+BC_i+AC_i}$$

# Truth Table 真值表

| $a$ | $b$  | $c_i$ | $s$  | $c_o$ |
| :-: | :-: | :---: | :-: | :---: |
|  0  |  0  |   0   |  0  |   0   |
|  0  |  0  |   1   |  1  |   0   |
|  0  |  1  |   0   |  1  |   0   |
|  0  |  1  |   1   |  0  |   1   |
|  1  |  0  |   0   |  1  |   0   |
|  1  |  0  |   1   |  0  |   1   |
|  1  |  1  |   0   |  0  |   1   |
|  1  |  1  |   1   |  1  |   1   |

# 中间信号

可以把$S$和$C_o$定义由某些中间信号产生的信号。这些中间信号包括：
- $G=AB$ 进位产生（carry generate）信号
- $D=\overline{A}\ \overline{B}$ 进位取消（carry delete）信号
- $P=A\oplus B$ 进位传播（carry propagate）信号，$G$和$D$的优先级比$P$高，所以在有些地方也会写成$P=A+B$

## Dynamic Implementation of P and G

![[Dynamic Implementation of P and G.png#pic_center|动态逻辑中间信号产生电路]]
- Precharge when $\mathrm{Clk} = 0$
  当$\text{CLk}=0$时预充电
- [[Bleeder]] to compensate for the [[Charge Leakage]] due to the pull-down leakage paths
  **Bleeder**用于补偿由于下拉泄漏路径引起的电荷泄漏。

# Inverting Property of Adder Cell 加法器单元的反相特性

![[Pasted image 20241029205717.png#pic_center|全加器的反相特性]]
布尔表达式：$$\displaylines{\overline{S}(A,B,C_i)=S(\overline{A},\overline{B},\overline{C_i}) \\ \overline{C_o}(A,B,C_i)=C_o(\overline{A},\overline{A},\overline{C_i})}$$
