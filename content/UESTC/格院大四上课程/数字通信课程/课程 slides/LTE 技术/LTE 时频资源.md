---
title: LTE 时频资源
date: 2023-12-21 22:22
modification date: 2023 十二月 21日 星期四 22:22:10
aliases: 
tags: 
publish: "true"
---
在分析 LTE 系统的时频资源之前，我们首先需要对一些基本的概念进行了解。LTE 系统中能划分的最小的时频资源为[[资源元素]]。

![[资源元素]]

为了方便时频资源的调度，将多个资源元素组合起来就形成了[[物理资源块]]。

![[物理资源块]]

## 频率资源

频率资源指系统的带宽，带宽越宽系统速率越高，这里我们以 20MHz 系统带宽为例进行讨论。20MHz 的带宽一般被分成 1200 个子载波，每 12 个子载波被组成一个 PRB，总共有 100 个 PRB。这里每个子载波带宽是 15KHz，每个 PRB 带宽是 $15KHz\cdot 12=180KHz$。可能有人注意到 100 个 RB 的总带宽 $100 \cdot 180KHz=18MHz<20MHz$, 这是因为每一种带宽还需要和旁边的频带之间有保护带宽，从而避免干扰。

## 时间资源

时间资源涉及 LTE 系统的帧结构。在介绍帧结构之前，我们先要说明时域的基本时间单位。

### 时域的基本时间单位

我们假设的 LTE 系统中有1200个带宽为15KHz 的子载波，每个子载波的 FFT 采样点数目为

$$
N_\mathrm{fft}=2^{\mathrm{ceil}(\log2(1200))}=2048
$$

整个系统的采样频率为 $15\ kHz \cdot 2048 = 30720000$，基本时间单位为 $T_{s} = \frac{1}{30720000}$。

### LTE 的帧结构

![[LTE 的帧结构]]

之所以 LTE 的一帧为 10ms，是因为我们定义了帧的长度为 $307200 \cdot T_{s} = 10\ ms$，一个时隙的长度为 $15360 \cdot T_{s} = 0.5\ ms$，一个常规的循环前缀（CP）为 $144 \cdot T_{s} = 4.68\ \mu s$。一个 OFDM 符号长度为 $1/15\ kHz = 66.67\ \mu s$。一个常规 CP + 一个 OFDM 符号的时间为 $4.68\ \mu s + 66.67\ \mu s=71.35\ \mu s$。

在常规 CP 中，一个时隙有 7 个 OFDM 符号和 7 个 CP，因此占用的时隙的长度为，

$$
\begin{aligned}
\text{时隙}& = \text{7个OFDM 符号}+\text{第一个CP}+\text{6个常规CP}\\
& = 7 \cdot 66.67 \ \mu s + 160*T_s + 6\cdot 4.68 \mu s \\
& = 0.5\ ms
\end{aligned}
$$
## 时频资源

下图是 LTE 系统的时频资源栅格。纵轴为频率，横轴为时间。

![[LTE 时频资源_1.jpg]]

这里将 [[资源元素|RE]] 和 [[物理资源块|RB]] 的含义具象化了，每一个最小的小格为一个 RE，也代表着一个 OFDM 符号。稍大的方格为 RB。

>[!info] 参考资料
>
>```cardlink
 >url: https://zhuanlan.zhihu.com/p/476434085
>title: "LTE系统的物理层知识 - 理论速率计算（1）"
>description: "介绍4G LTE系统时，会说系统峰值速率有100Mbps~400Mbps，读完这篇文章你将了解这个速率是怎么计算的。为了节省时间，对LTE基础知识介绍的文字从下面复制。 LTE 物理层技术概要我主要是将需要的知识点串起来，让读…"
>host: zhuanlan.zhihu.com
>```
>
>```cardlink
>url: https://zlearning.netlify.app/lte/physical/lte-physical-overview.html#:~:text=%E6%A0%B9%E6%8D%AE%E5%BE%AA%E7%8E%AF%E5%89%8D%E7%BC%80%E9%95%BF%E5%BA%A6%E4%B8%8D%E5%90%8C,%E5%8F%AF%E9%80%89%E7%9A%84RB%E6%95%B0%E3%80%82
>title: "LTE 物理层技术概要"
>description: "本文描述LTE-FDD和TDD的频带资源"
>host: zlearning.netlify.app
>```
>


