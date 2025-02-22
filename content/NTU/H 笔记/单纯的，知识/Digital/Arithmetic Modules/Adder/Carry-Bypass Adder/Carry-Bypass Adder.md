---
aliases:
  - 进位旁路加法器
  - Carry-Skip Adder
tags:
  - adder
  - digital
  - arthmetic_modules
---

![[Carry-Bypass Adder_1.png|进位传播]]

[[Full Adder#中间信号|进位传播信号]]$P$可以用来加速进位链中的进位操作。当$P$有连续的高电平时，进位输入可以通过旁路晶体管立即进入下一模块，这一操作被称为进位旁路加法器。

# 特点

- Either carry bypass or generated in the chain.
  进位要么通过旁路，要么在链中生成。
- In either case, delay is smaller
  无论在哪种情境中，延时都减小
- $BP=\prod{P_n}$

# Delay 延时

![[Carry-Bypass Adder_3.png|延时的关键路径]]

上图假设了一个$N$位的加法器，被分成了$\frac{N}{M}$个等长的旁路级，每一级含有$M$位，灰色关键路径的传播延时$t_p$可以近似表达为（中文教材的图少画了一个MUX）：
$$t_p\approx t_{\text{setup}}+M\cdot t_{\text{carry}}+\left(\frac{N}{M}-1\right)t_{\text{bypass}}+(M-1)t_{\text{carry}}+t_{\text{sum}}$$
- $t_{\text{setup}}$: fixed delay to get [[Full Adder#中间信号|P and G signal]]
  得到P和G信号的固定延时
- $t_{\text{carry}}$: carry delay in 1 bit, worse is M bit in 1 stage, $t_{carry} \approx M\cdot t_{carry}$
  1位的进位延时，如果一级具有M位，那么大概是1位的M倍
- $t_{\text{bypass}}$: delay through MUX in 1 stage
  1级中MUX的延时
- $t_{\text{sum}}$: delay of sum $S$ in final stage
  最后一级求和的延时

# Manchester Carry-Bypass Adder

[[Manchester Carry Gates|曼彻斯特进位链加法器]]的进位链也可以用旁路晶体管改良。通过添加受到$BP$控制的传输管即可实现这一目的。
![[Carry-Bypass Adder_2.png|使用旁路晶体管改良曼彻斯特进位链加法器]]
