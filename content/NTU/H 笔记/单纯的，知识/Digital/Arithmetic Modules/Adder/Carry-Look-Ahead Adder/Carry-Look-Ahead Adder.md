---
aliases:
  - 超前进位加法器
  - CLA
tags:
  - adder
  - digital
  - arthmetic_modules
---
![[Pasted image 20241029040708.png|Full Adder]]

- 超前进位加法器避免了逐级的进位传递。可以发现进位存在如下递推关系：$$C_{o,n}=f(A_n,B_n,C_{o,n-1})=G_n+P_nC_{o,n-1}$$递推关系展开后可以得到：$$C_{o,n}=G_n+P_n\left(G_{n-1}+P_{n-1}\left(\cdots+P_1\left(G_0+P_0C_{i,0}\right)\right)\right)$$其中$C_{i,0}$通常为$0$，$G$和$P$为[[Full Adder#中间信号|全加器中间信号]]
- 这样展开后，最终的进位输出与前面的位无关，代价是额外的逻辑门。

# Carry-Look-Ahead Generator

![[Pasted image 20241029040637.png|Carry-Look-Ahead Generator]]
$$\displaylines{C_1=&G_0+P_0C_0 \\ C_2=&G_1+P_1G_0+P_1P_0C_0 \\ C_3=&G_2+P_2G_1+P_2P_1G_0+P_2P_1P_0C_0 \\ C_4=&G_3+P_3G_2+P_3P_2G_1+P_3P_2P_1G_0+P_3P_2P_1P_0C_0}$$

# Carry-Look-Ahead Conceptual Diagram

![[Pasted image 20241029040729.png|Carry-Look-Ahead Conceptual Diagram]]
- The delay due to the carry is eliminated with the cost of extra logic
  通过增加额外的逻辑来消除进位引起的延迟

# 4-bit Carry-Look-Ahead Generator


![[Carry-Look-Ahead Adder.png#pic_center|4-bit Carry-Look-Ahead Generator]]
- 4位超前进位加法器的进位产生等式为：$$C_4=G_3+P_3G_2+P_3P_2G_1+P_3P_2P_1G_0+P_3P_2P_1P_0C_0$$
