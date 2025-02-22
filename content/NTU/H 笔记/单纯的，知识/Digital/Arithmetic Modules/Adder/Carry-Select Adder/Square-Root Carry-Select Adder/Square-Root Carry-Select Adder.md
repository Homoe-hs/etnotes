---
aliases:
  - 平方根进位选择加法器
tags:
  - adder
  - digital
---

![[Square-Root Carry-Select Adder.png]]
考虑[[Carry-Select Adder|进位选择加法器]]中于后面几级多路开关的输入，会发现进位的输入远早于多路开关控制信号的输入。所以适当延长进位的传播延时可以达成更优解。

# 特点

- Initial stage has fewer bits
  最开始的级位数最少
- Increase 1 bit for per stage (No. Stage $P\approx\sqrt{2N}$)
  每一级增加1位，所以级数约为$\sqrt{2N}$

# 延时

$$t_{\text{p}}=t_{\text{setup}}+M\cdot t_{\text{carry}}+\sqrt{2N}\cdot t_{\text{mux}}+t_{\text{sum}}$$
其中：
- $t_{\text{setup}}$：形成[[Full Adder#中间信号|进位产生信号G和进位传播信号P]]所需要的固定时间
- $t_{\text{carry}}$：通过1位的传播延时。最坏情况下通过具有$M$位的进位链的传播延时为$M\cdot t_{\text{carry}}$
- $t_{\text{mux}}$：选择器的传播延时
- $t_{\text{sum}}$：最后一级输出$S$的传播延时