---
aliases:
  - 线性进位选择加法器
tags:
  - adder
  - digital
---

与[[Carry-Bypass Adder|进位旁路加法器]]类似，线性进位选择加法器可以将总共$N$位的加法器拆分为每级为$M$位的链状结构。下图展示了一个$N=16$，$M=4$的线性进位选择加法器及其关键路径。

![[Linear Carry-Select Adder.png]]

# 延时

- 总共$N$位的加法器，每级为$M$位的加法器最差延时$t_{\text{p}}$为：$$t_{\text{p}}=t_{\text{setup}}+M\cdot t_{\text{carry}}+\frac{N}{M}t_{\text{mux}}+t_{\text{sum}}$$上式中的各项为：
	- $t_{\text{setup}}$：形成[[Full Adder#中间信号|进位产生信号G和进位传播信号P]]所需要的固定时间
	- $t_{\text{carry}}$：通过1位的传播延时。最坏情况下通过具有$M$位的进位链的传播延时为$M\cdot t_{\text{carry}}$
	- $t_{\text{mux}}$：选择器的传播延时
	- $t_{\text{sum}}$：最后一级输出$S$的传播延时
- 线性进位选择加法器的延时**正比**于$N$，原因是在最坏情况下，0、1选择信号仍然需要逐一通过所有级。
