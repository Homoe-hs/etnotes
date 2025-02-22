---
aliases:
  - pulse width modulation
  - 脉宽调制
  - 脉冲宽度调制
tags: []
publish: "true"
---

脉冲宽度调制是将模拟信号变换为脉冲（数字信号）的一种技术，一般变换后脉冲的周期（[[占空比]]）固定，但脉冲的工作周期会依模拟信号的大小而改变。

## 概念

- 占空比（duty cycle）：在高模式下的时间长度 - 决定输出值。
- 频率/周期：PWM完成一个循环/周期的速度
- 分辨率：占空比可以被调制的颗粒度 - 决定输出的精确程度

## 平均电压
$$
平均电压=\text{high}\times \frac{\text{activetime}}{\text{period}}
$$
