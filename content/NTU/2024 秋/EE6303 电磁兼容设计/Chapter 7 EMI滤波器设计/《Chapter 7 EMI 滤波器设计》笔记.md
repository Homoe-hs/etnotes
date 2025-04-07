---
对象类型: 笔记
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 传导 EMI 的传导模式

DM = Differential-Mode  
CM = Common- Mode

问题在于，用 EMI 接收机进行测量的时候，DM 信号和 CM 信号混杂在一起了。

# 2. EMI 滤波器设计

## 2.1. 并联电容器作为低通滤波器

$$
A_{d B}=2 0 \log \left\vert1+\frac{Z_{p}} {Z_{c a p}} \right \vert
$$
$$
A_{d B} \approx2 0 \mathrm{l o g} \left| Z_{p} \right|-2 0 \mathrm{l o g} \left| Z_{c a p} \right|
$$

## 2.2. 串联电感作为低通滤波器

$$
A_{d B}=2 0 \log \left \vert1+\frac{Z_{i n d}} {Z_{s u m}} \right \vert
$$
$$
A_{d B} \approx2 0 \mathrm{l o g} \left| Z_{i n d} \right|-2 0 \mathrm{l o g} \left| Z_{s u m} \right|
$$

[[EE6303 例题合集#EMI 低通滤波器]]

## 2.3. 有效低通滤波器配置

![[有效低通滤波器设计.png]]
这个很好理解。电容在频率越高的时候，阻抗越低，因此使用在高阻抗场景能使用更大的电容值；电感相反，更适用于小阻抗情况。

## 2.4. 

