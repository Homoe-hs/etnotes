---
date: 2025-04-08 22:50
modification date: 2025 四月 8日 星期二 22:50:10
tags: 
- 
---
# Q1

![[a. 保持测量 b. 保持条件下的 I-V 特性.png]]

# Q2

![[《IC Tech》笔记#4.3. 闩锁的原因]]

# Q3

![[《IC Tech》笔记#4.2.3. 闩锁触发的必要和充分条件]]

# Q4

施加 $I$ 测量 $V$ 的图像如下，

![[回滞测量的结果.png|300]]

施加 $V$ 测量 $I$ 的图像如下，

![[CMOS 闩锁 施加 V 测量 I.drawio.png|300]]

# Q5

![[《IC Tech》笔记#4.4.5. 保持特性表征：回滞测量]]

# Q6

Experiment design by Prof. Deepseek
7. Measure I-V characteristics to identify trigger/holding points
8. From snapback curve, estimate Rₛ and R_w from voltage drops  
9. Use separate measurements of isolated BJTs to estimate α's
10. Alternatively, measure sensitivity to well/substrate bias to extract parameters
11. Use curve fitting with latchup equations to extract parameters

# Q7

![[《IC Tech》笔记#4.5.1.1. 降低环路增益]]

# Q8

如果是 p+ 过压触发，
$$
I_{pTRIG}=\dfrac{V_{BEn}}{\alpha_{pnp}R_{S}} 
$$
如果是 n+ 过压触发，
$$
I_{nTRIG} = \dfrac{V_{BEp}}{\alpha_{npn}R_{W}}
$$
代入题目条件进行运算即可。


# Q9

![[《IC Tech》笔记#4.5.1.2. 降低 $R_{W}$ 和 $R_{S}$ 来提高触发电流]]

# Q10

![[《IC Tech》笔记#4.5.5. 策略 5：大闩锁保护窗口]]
