---
aliases:
  - 互补CMOS全加器
tags:
  - adder
  - digital
  - arthmetic_modules
---
由[[Full Adder]]改进而来。

![[Pasted image 20241104073849.png|利用互补静态CMOS实现的全加器]]
# 表达式

$$\displaylines{C_o=AB+BC_i+AC_i \\ S=A\oplus B \oplus C_i=ABC_i+\overline{C_o}(A+B+C_i)}$$

# Drawbacks 缺点

- The Complementary Static CMOS full adder cell has 28 transistors.
  互补静态CMOS全加器有28个晶体管
- It is large and slow.
  大且慢
- PMOS stacks are in carry and sum part.
  PMOS堆积在进位与求和部分
- Intrinsic capacitance of $C_o$ is large: 6 [[Gate Capacitance]] + 2 [[Diffusion Capacitance]] + Interconnect Capacitance.
  $C_o$的本征电容很大：6个栅电容+2个扩散电容+互联电容
- Carry propagates through 2 inverting stages.
  进位通过两个反相器传播
- Sum output requires extra logic (although not critical).
  求和输出需要额外的逻辑电路（虽然并不重要）

# Improvement 改进

![[Pasted image 20241021201112.png|改进的进位链]]
- Remove an inverter of the carry chain
  将进位链中的反相器移除，这样可以隔一个省去一个反相器的延时
