---
aliases:
  - 行波进位加法器
  - 逐位进位加法器
tags:
  - adder
  - digital
  - arthmetic_modules
---
![[Ripple-Carry Adder.png|Ripple-Carry Adder]]

- An n-bit adder can be constructed by cascading n [[Full Adder]]s
  一个n位加法器可以通过级联n个全加器来构造
- Ripple-Carry Adder is simple but suffer from long delay, specially when n is large.
  行波进位加法器简单，但在n值较大时会有较长的延迟

# Delay 延时

- For an n-bit Ripple-Carry Adder, the worst case delay occurs when a carry generated at LSB propagates all the way to MSB
  对于n位行波进位加法器，最坏情况下的延迟发生在最低有效位 (LSB) 生成的进位一路传播到最高有效位 (MSB) 时
$$t_{adder}=(n-1)\times t_{carry}+t_{sum}$$
- $t_{carry}$: propagation delay from $C_i$ to $C_o$
- $t_{sum}$: propagation delay from $C_i$ to $S$

- For 8-bit addition, one of the worst case delay occurs when $a=011111111b$ and $b=00000001b$
$$a+b=01111111b+00000001b=10000000b$$
