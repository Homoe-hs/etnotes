---
aliases:
  - 曼彻斯特进位链加法器
tags:
  - adder
  - digital
  - arthmetic_modules
---
- [[Transmission-Gate-Based Adder|传输门型加法器]]中的Carry Gate可以通过[[Full Adder#中间信号|全加器的中间信号]]进一步简化$$C_o=G_i+P_iC_i$$

# Static Logic 静态逻辑

![[Static Manchester Carry Gates.png#pic_center|静态逻辑实现Manchester Carry Gates]]

- 进位传播路径不充电（管子初始都不导通），如果进位传播信号$P=(A_i\oplus B_i)=1$，则$C_i$被传送至输出$C_o$
- 如果传播条件不满足，则输出由信号$D_i$下拉或$\overline{G_i}$上拉。

# Dynamic Logic 动态逻辑

![[Dynamic Manchester Carry Gates.png#pic_center|动态逻辑实现Manchester Carry Gates]]

- 使用动态实现可以让电路更加简洁。由于动态电路中的晶体管是单方向工作的，所以可以只用NMOS传输管来代替传输门。预充电输出使电路不再需要进位取消信号（对于进位链，传播的是进位信号的反信号时的情景）。
- [[Full Adder#Dynamic Implementation of P and G|Dynamic Implementation of P and G]]

# 4-Bit Manchester carry Chain

![[Pasted image 20241029035326.png|4-Bit Manchester carry Chain]]
- Uses pass transistors for carry chain
  在进位链中使用传输管。
- All pass transistors are precharged to $V_{DD}(\phi=0)$
  所有传输管都被预充电到$V_{DD}(\phi=0)$，初始导通。
