---
aliases:
  - 进位选择加法器
tags:
  - adder
  - digital
  - arthmetic_modules
---
在[[Ripple-Carry Adder|行波进位加法器]]中，每个[[Full Adder|全加器]]必须等待输入的进位到达后才能产生一个输出进位。为了避免这种情况，可以预先考虑进位输入两种可能的值，并提前计算出这两种可能性的结果。一旦输入的进位值已知，就可以通过多路开关输出正确的结果。这种实现被称为进位选择加法器。

![[Carry-Select Adder_1.png#pic_center|进位选择加法器]]

- Both 0 and 1 carry bits are generated.
  0和1的进位被同时产生
- Once carry from previous stage is known, the carry from this stage is selected with MUX.
  一旦前一级产生的进位已知，这一级的进位就会被MUX选择输出

# Carry-Select Adders

- [[Linear Carry-Select Adder]]
- [[Square-Root Carry-Select Adder]]
