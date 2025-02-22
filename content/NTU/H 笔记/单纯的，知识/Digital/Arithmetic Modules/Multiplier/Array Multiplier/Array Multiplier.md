---
aliases:
  - 阵列乘法器
tags:
  - multiplier
  - digital
  - arthmetic_modules
---
![[Array Multiplier.png|4 Bits Array Multiplier]]

- Partial products are added to produce the result
  部分积相加以产生结果
- It requires $N-1$ M-bit adders
  它需要N-1个M位的加法器
- e.g. 4Bits: First two rows may be combined
  在例子中：前两行可以被合并

通过将[[Partial Products|部分积]]累加起来，我们可以得到计算的结果。阵列乘法器使用加法器阵列进行部分积的累加。上图中的HA表示[[Half Adder|半加器]]，FA表示[[Full Adder|全加器]]。

# Delay

![[Pasted image 20241029041944.png|Critical paths have the same length]]

在阵列乘法器中，不同的关键路径拥有同样的长度，延时为：$$t_{\text{p}}\approx [(M-1)+(N-2)]\cdot t_{\text{carry}}+(N-1)\cdot t_{\text{sum}}+t_{\text{and}}$$上式中：
- $t_{\text{carry}}$：输入和输出进位之间的传播延时
- $t_{\text{sum}}$：全加器输入进位与$S$之间的延时
- $t_{\text{and}}$：与门的传播延时
