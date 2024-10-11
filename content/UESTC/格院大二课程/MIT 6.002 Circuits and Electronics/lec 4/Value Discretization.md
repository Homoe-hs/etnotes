---
aliases: []
tags: []
publish: "true"
---

# Value Discretization
## Definition
Restrict values to be one of two. 

## Example
| HIGH |  LOW  |
|:----:|:-----:|
|  5V  |  0V   |
| TRUE | FALSE |
|  1   |   0   |
通过 value discretization 能够有更好的噪声宽容度，例如这个例子的噪声边界为 2.5V。

## 禁区
2.5V 对于上述的系统而言是没有意义的，于是我们创建一个禁区
![[禁区.png]]
我们使得信号被定义为一个范围而非某个值，而在禁区内的信号是无定义的。
但是这样的系统没有噪声边界。

## 输入噪声容限
通过将发送端限制到更严格的标准范围内，我们得以使系统有噪声边界。
![[更严格的标准.png]]
数字系统遵循静态规则：如果数字系统的输入满足有效的输入阈值，则系统保证其输出满足有效的输出阈值。
