---
aliases:
  - 传输门型加法器
tags:
  - adder
  - digital
  - arthmetic_modules
---

![[Transmission-Gate-Based Adder.png|使用传输门和XOR门设计全加器]]
- 全加器可以用多路开关和XOR门设计，但这在互补静态CMOS电路中不可行，只能使用传输门实现
- **这种全加器的特点是和$S$与进位$C_o$的输出有相近的延时**

# 表达式

[[Full Adder#中间信号|全加器的中间信号]]：
$$P=A_i \oplus B_i$$

输出：
$$\displaylines{S=P\oplus C_i=\overline{\overline{P}\ \overline{C_i}+PC_i} \\ C_o=A_iB_i+PC_i=\overline{\overline{P}\ \overline{A_i}+P\overline{C_i}}}$$
