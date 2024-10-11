---
title: 均衡（DC）
date: 2023-12-18 15:02
modification date: 2023 十二月 18日 星期一 15:02:19
aliases:
  - equalization
tags:
  - 
publish: "true"
---

为了补偿通道引起的 [[ISI]]，我们使用称为「均衡」的过程：一种校正通道频率响应的技术。

![[均衡（DC）_1.png]]

在通信系统中，一般接收机 $h_{R}(t)$ 是和发射机 $h_{T}(t)$ 相匹配的，我们只需要考虑均衡器 $h_{EQ}(t)$ 和通道响应 $h_{c}(t)$ 之间的匹配，是的其满足：

$$
H_{c}(f)H_{EQ}(f)=1\Rightarrow H_{EQ}(f)=\frac{1}{H_{c}(f)}=\frac{1}{|H_{c}(f)|}e^{-j\theta_{c}(f)}
$$
