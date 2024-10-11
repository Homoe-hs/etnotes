---
title: 数字通信 Slides 例题解析
date: 2023-12-20 20:00
aliases: 
tags: 
documentclass: ctexart
publish: "true"
---
>[!tldr]
>本文档适用于 2020 级格院微电子数字通信（Digital Communication）课程。根据出现在 Slides 上的例题进行总结概括。每道例题会包括**解题所需知识点**和**计算过程与答案**两个部分。

>[!attention] 
>不保证完全正确, 请仔细甄别
>

## Lec 2

### 计算波特率

![[数字通信 Slides 例题解析_42.png]]

这道题要求计算波特率。波特率实际上就是符号速率。

![[符号速率|波特率]]

四级信令指的是一个符号可以表示四种状态，说明一个符号有两比特。

$$
Baud\ rate = \frac{24}{2}= 12\ Baud
$$

### 计算误码率

![[数字通信 Slides 例题解析_43.png]]

$$
bit\ error = \frac{10}{10^{6}\cdot 6}=1.66\times 10^{-6}
$$

## Lec 3 调制解调

### 匹配滤波器的脉冲响应

![[数字通信 Slides 例题解析_44.png]]

匹配滤波器的脉冲响应非常容易理解，就是原波形的镜像反转。

$$
h(t) = s(2 - t)
$$

### 误码率计算

![[数字通信 Slides 例题解析_45.png]]

![[数字通信 Slides 例题解析_50.png]]



$$
\begin{align}
P_B & = \sum_{i=1}^2P(e,s_i)=P(e\mid s_1)P(s_1)+P(e\mid s_0)P(s_0) \\
& =
\end{align}
$$



![[高斯分布的概率密度函数]]

$$
P_B=Q\bigg(\frac{a_1-a_0}{2\sigma_0}\bigg)
$$

$$
Q(x)\cong\frac{1}{x\sqrt{2\pi}}\exp\biggl[-\frac{x^{2}}{2}\biggr]
$$

![[数字通信 Slides 例题解析_46.png]]

## Lec 4 带通调制

## Lec 5 香农极限、熵和信源编码

### 香农极限

![[数字通信 Slides 例题解析_47.png]]

这里直接使用香农极限公式即可计算出在给定的带宽和信噪比条件下的最大信道容量。

![[香农极限公式]]

$$
C = 2\ kHz \cdot \log_{2}\left( 1+10^{\frac{S/N}{10}}\right)
$$

### 计算熵

![[数字通信 Slides 例题解析_48.png]]

总的概率和为 1。通过带入熵的计算公式可以直接算出。

![[熵的计算公式]]

### 香农-范诺编码

![[香农-范诺编码]]

### 信源编码效率计算

![[数字通信 Slides 例题解析_49.png]]

信源编码的效率就是熵和平均字长的比。

![[信源编码效率计算公式]]

![[熵的计算公式]]

![[编码向量的平均字长计算公式]]

## Lec 6 ISI 和整波

### 计算比特误码率

![[数字通信 Slides 例题解析_39.png]]

$$
P_{B}=Q\left(\sqrt{\frac{E_{a\nu g}}{N_{0}}}\right)
$$

$$
Q(x)\cong\frac{1}{x\sqrt{2\pi}}\exp\biggl[-\frac{x^{2}}{2}\biggr]
$$

![[数字通信 Slides 例题解析_40.png]]

![[滚降系数计算公式]]


![[数字通信 Slides 例题解析_41.png]]

如果想要没有 ISI，只要满足奈奎斯特带宽即可。

![[奈奎斯特带宽计算公式]]

## Lec 7 载波同步

这一个 slide 没有给出例题，只要理解并且能够计算锁相环和 Costas 环。

![[锁相环]]

![[Costas环]]

## Lec 8 均衡

### 设计三抽头迫零均衡器

![[数字通信 Slides 例题解析_36.png]]

设计一个三抽头的迫零均衡器，我们最后需要解得一个三位向量 $\begin{bmatrix}C_{-1}\\C_{0}\\C_{1}\end{bmatrix}$。题目中给出的向量分别需要对应以下五个采样点 $x(n)=\{x_{-2},x_{-1},x_{0},x_{1},x_{2}\}$，所以虽然给出了 7 个数据，我们需要掐头去尾使用中间的 5 个数据即可。因此可以列出矩阵方程，

$$
\begin{bmatrix}
x_{0}&x_{-1}&x_{-2} \\
x_{1}&x_{0}&x_{-1} \\
x_{2}&x_{1}&x_{0}
\end{bmatrix} \cdot \begin{bmatrix}C_{-1}\\C_{0}\\C_{1}\end{bmatrix} =\begin{bmatrix}0\\1\\0\end{bmatrix}
$$

将数据填入可以得到方程，

$$
\begin{align}
&& 0.87C_{-1}+0.15C_{0}-0.10C_{1}=0 \\
&& 0.12C_{-1}+0.87C_{0}+0.15C_{1}=1 \\
&& -0.2C_{-1}+0.12C_{0}+0.87C_{1}=0
\end{align}
$$

通过消元法即可算出结果为 $\begin{bmatrix}-0.236\\1.220\\-0.2226\end{bmatrix}$。

![[数字通信 Slides 例题解析_37.png]]

列出矩阵方程，

$$
\begin{bmatrix}
x_{0}&x_{-1}&x_{-2} \\
x_{1}&x_{0}&x_{-1} \\
x_{2}&x_{1}&x_{0}
\end{bmatrix} \cdot \begin{bmatrix}C_{-1}\\C_{0}\\C_{1}\end{bmatrix} =\begin{bmatrix}0\\1\\0\end{bmatrix}
$$

将数据填入可以得到联立方程，

$$
\begin{align}
&& 0.9C_{-1}+0.2C_{0}=0 \\
&& -0.3C_{-1}+0.9C_{0}+0.2C_{1}=1 \\
&& 0.1C_{-1}-0.3C_{0}+0.9C_{1}=0
\end{align}
$$

通过消元法即可算出结果为 $\begin{bmatrix}-0.2140\\0.9631\\0.3448\end{bmatrix}$。

### 信道传递函数

![[数字通信 Slides 例题解析_38.png]]

![[020b522a10366d34c8c0ca90ecbd1e2.jpg]]

## Lec 9-10 FDMA

### FDMA 信道数计算

![[数字通信 Slides 例题解析_26.png]]

本题需要计算 FDMA 系统在给定频谱条件下的可用信道数。

![[FDMA 同时支持信道数计算式]]

$$
N=\frac{B_{t}-2B_{g}}{B_{c}} = 416 
$$

### TDMA 码率计算

![[数字通信 Slides 例题解析_27.png]]

这道题目中暗含了 GSM 的带宽结构，在后面的 LTE 章节会有更详细的解释，这里简单说明。最大的结构为「帧」（frame）；帧中包含多个「子帧」（subframe）；子帧中包含多个「时隙」（time slot）；时隙由多个「符号」（symbol）构成；一个符号由多个「比特」（bit）构成。

#### 1 比特持续时间

这里已经给出了数据传输速度，所以直接计算即可。

$$
T_{b} = \frac{1}{270.833\ kbps} = 3.692\ \mu s
$$

#### 一个时隙持续的时间

题目中给出了，一个时隙由 156.25 个比特构成，

$$
T_{slot} = 156.25 \cdot T_{b}=0.577\ ms
$$

####  一帧持续时间

根据题目信息可以直接计算，

$$
T_{f} = 8 \times T_{slot} = 4.615\ ms
$$

### 同时支持用户数量计算

![[数字通信 Slides 例题解析_28.png]]

这一道题计算的是 TMDA 的总信道数（同时支持的用户数量），其实就是信道数乘以每个信道包含的时隙数即可计算出。

$$
N=\frac{8\times25MHz}{200kHz}=1000
$$

### 计算有效用户数量

![[数字通信 Slides 例题解析_29.png]]

这道题很好理解，唯一需要注意的地方在于保护带宽在带的两边都有，需要减去。

$$
N = \frac{B_{total}-2B_{guard}}{B_{channel}}=1249
$$

### 计算帧效率

![[数字通信 Slides 例题解析_30.png]]

这个很简单，一帧中只有在传输信息的比特是「有效」的比特。

$$
\varphi = \frac{58 \times 2}{8.25 +6 + 26 +58 \times 2} = 74.24\%
$$

### 用户数据速率和信道效率

![[数字通信 Slides 例题解析_31.png]]

这个很简单，一帧由八个用户均分即可。

$$
\begin{align}
& raw\ data = \frac{270.8333\ kbps}{8}=33.85\ kbps \\
& efficiency = \frac{33.85-10.1}{33.85}=70.13\%
\end{align}
$$

![[数字通信 Slides 例题解析_32.png]]

本题同样，

$$
raw\ data = \frac{48.6 \  kbps}{3} = 16.2\ kbps
$$

### 计算帧效率

![[数字通信 Slides 例题解析_33.png]]

由于时隙结构都是重复的，算帧效率就等于计算时隙效率。

$$
efficiency = \frac{260}{6+6+28+12+12+260}=80.24\ \%
$$

## Lec 11-12 信道编码与生成矩阵

### 根据生成矩阵将输入转化为码字

![[数字通信 Slides 例题解析_23.png]]

首先我们需要了解生成矩阵的构成，

![[系统线性分组码的生成矩阵]]

随后就是简单的矩阵运算。对于输入向量 $[110]$，分别将其与 $\begin{bmatrix}V_1\\V_2\\V_3\end{bmatrix}$ 的元素相乘即可。

$$
\begin{aligned}
U_{4} & = [110] \cdot G\\
& = 1 \cdot V_{1} + 1 \cdot V_{2} + 0 \cdot V_{3}\\
& = 101110
\end{aligned}
$$
生成码字 $U_{4}$ 的前三位为奇偶校验码，后三位才是输入信息 $[110]$ 对应的码字。

### 根据生成矩阵写奇偶校验矩阵

![[数字通信 Slides 例题解析_17.png]]

![[奇偶校验矩阵]]

由此可以根据生成矩阵 $G$ 直接构成奇偶校验矩阵 $H$ 为，

$$
H=
\begin{bmatrix}
I_{n-k} P^{T}
\end{bmatrix}=\begin{bmatrix}1&0&0&1&0&1\\0&1&0&1&1&0\\0&0&1&0&1&1\end{bmatrix}
$$

>[!tip]
>转置在形式上表现为矩阵沿着对角线翻折

### 综合征测试

![[数字通信 Slides 例题解析_24.png]]

通过将收到的码字与奇偶校验矩阵的转置点乘，根据结果可以知道是否出现错误，这就是综合征测试。

$$
\begin{align}
S & = r \cdot H^{T}\\
& = [001110] \cdot \begin{bmatrix}
1&0&0 \\
0&1&0 \\
0&0&1 \\
1&1&0 \\
0&1&1 \\
1&0&1
\end{bmatrix} \\
& = \begin{bmatrix}
1 & 1+1 & 1+1 
\end{bmatrix} \\
& = \begin{bmatrix}
1&0&0
\end{bmatrix}
\end{align}
$$

>[!tip]
>简单复习一下矩阵乘法：
> ![[数字通信 Slides 例题解析_25.png]]
>

### 定位错误比特

![[数字通信 Slides 例题解析_19.png]]

这一张图是一个示例。第一排为 8 个正确码字，下面是分别在 1，2，3 等位出错的样例，看懂即可。

### 根据接收到的码字通过综合征测试修正错误

![[数字通信 Slides 例题解析_20.png]]

在前面我们已经进行过综合征测试的计算，结果为 $[100]$。其意味着在第 4 位比特出错了。根据上表可查得正确码字应该为 $[001010]$。

### 汉明距离和汉明权重

![[数字通信 Slides 例题解析_21.png]]

![[汉明距离]]

![[汉明权重]]

### 构建奇偶校验矩阵并进行错误校验

![[数字通信 Slides 例题解析_22.png]]

#### 奇偶校验矩阵

奇偶校验矩阵为，

$$
H = [I\ \vdots\  P^{T}]=
\begin{bmatrix}
1&0&0&1&0&1&1 \\
0&1&0&1&1&1&0 \\
0&0&1&0&1&1&1
\end{bmatrix}
$$

#### 线性分组码码率和冗余

对于（k，n）的线性分组码而言，其码率为 $R = \dfrac{k}{n}$。所以本题的码率为 0.57。

冗余为 $Re = \dfrac{n-k}{k}=0.42$

#### 码字计算

$$
\begin{align}
U & = m \cdot G \\
& =[1110]\cdot \begin{bmatrix}1&1&0&1&0&0&0\\0&1&1&0&1&0&0\\1&1&1&0&0&1&0\\1&0&1&0&0&0&1\end{bmatrix} \\
& = [0001110]
\end{align}
$$

#### 综合征测试

$$
\begin{align}
S & = r \cdot H^{T} \\
& = [0001110] \cdot \begin{bmatrix}
1&0&0 \\
0&1&0 \\
0&0&1 \\
1&1&0 \\
0&1&1 \\
1&1&1 \\
1&0&1
\end{bmatrix} \\
& = [000]
\end{align}
$$
说明没有错误。

## Lec 13 卷积码

### 根据卷积码网格图进行编码

![[数字通信 Slides 例题解析_14.png]]

这道题目给出了一个（2，1，3）的卷积码编码器。$K=3$，$\dfrac{n}{k}=\dfrac{1}{2}$。给了输入，要求我们识图给出输出。这个图是对于卷积码编码器的网格图描述。

![[卷积码#网格图描述]]

题目说从最高位开始输入（MSB），输入的内容为：1，1，0，0，0。我们依次画出路径。

![[数字通信 Slides 例题解析_15.png]]

得出编码为：11，01，01，11，00。

## Lec 14-15 OFDM

### 计算 HyperLAN 数据速率

![[数字通信 Slides 例题解析_10.png]]

已知 FFT 大小为 64，意味着有 64 个载波参与信号传输，其中有 48 个载波传播数据。我们需要计算在一个载波上的符号的长度。每一条载波占据的带宽（载波之间的间隔）为，

$$
\Delta f = \frac{B}{N_{carrier}}= \frac{20\ MHz}{64} = 312.5\ kHz
$$
符号能传播的时间为，

$$
T_{s}=\frac{1\ s}{\Delta f} = 3.2\ \mu s
$$
再加上 $0.8 \mu s$ 的保护间隔，符号的长度为 $4\ \mu s$。

由于采用 QPSK 的调制方式，一个符号有 2 比特。48 个载波传播信息，那么就有 96 位比特在 $4\ \mu s$ 内传输。总的符号速率为，

$$
96 \times \frac{1}{4\mu}=24\ Mbits/s
$$

### 延时扩展与带宽计算

![[数字通信 Slides 例题解析_11.png]]

ISI-free 意味着信号要平坦衰落，意味着符号长度要大于延时扩展。

$$
T_{s}>\sigma=10\ ms
$$
由此计算出子载波的最大间隔为，

$$
\Delta f < \frac{1}{T_{s}} = 100\ Hz
$$

总共有 512 个子载波，可以由此计算出总带宽需要小于，

$$
B = 512 \times \Delta f < 51.2\ kHz
$$

## Lec 16 无线通信系统

![[数字通信 Slides 例题解析_9.png]]

1. 频道或载波频率对无线通信范围的影响是什么？
   - Transmission Range
   - Propagation Distance
   - Penetration and Attenuation
   - Spectrum Management

1. MIMO 如何提高系统性能（容量、误比特率等）？
   - Increased Capacity
   - Reduced Bit Error Rate (BER)

1. 无线系统的主要缺点是什么？
   - Channel Fading
   - Interference
   - Security Concerns
   - Limited Spectrum
   - Power Consumption

4. 6G 的应用是什么？
   - Higher Data Rates
   - Lower Latency
   - More Device Connections
   - Improved Coverage and Reliability

## Lec 17-18 LTE 系统

### 计算 LTE 的数据速率

![[数字通信 Slides 例题解析_7.png]]

为了计算 LTE 的数据速率，我们需要了解 LTE 系统的时频资源是如何分配的。

![[LTE 时频资源]]

在这道题目中，我们的信道带宽为 $10\ MHz$ 并且有着 600 个子载波。从时频资源栅格上来看，就是纵向有 600 个格子。使用 64-QAM 进行调制，意味着一个 OFDM 符号可以承载 $\log_{2}64=6$ 个比特。但是编码率仅为 1/3，意味着 6 个比特中只有 2 个比特传输信息。因此可以计算在一个时隙内的数据速率为，

$$
600 \times 7 \times 6 \times \dfrac{1}{3} = 8400\ bits/slot
$$

那么在一秒内的数据速率为，

$$
8400 \times \frac{1\ s}{0.5\ ms}=16.8\ Mbps
$$


### 计算 LTE 系统相关参数

![[数字通信 Slides 例题解析_8.png]]

#### 计算物理资源块和子载波数量

这个根据物理资源块的定义即可计算。

![[物理资源块]]

$$
\begin{aligned}
& \text{number of PRB} = \frac{5\ MHz}{180\ kHz}=MAX\{27.7\}=27 \\
& \text{number of subcarrier} = 27 \times 12 = 324
\end{aligned}
$$

#### 计算最大下载数据速率

题目中给出的条件为 16-QAM，编码率为 3/5，使用短 CP。一个时隙的数据速率为，

$$
324 \times 7 \times \log_{2}16 \times \frac{3}{5} = 5443.2\ bits
$$
一秒的数据速率为，

$$
5443.2 \times \frac{1\ s}{0.5\ ms}=10.88\ Mbps
$$

#### 如果使用 10 个物理资源块，下载可达到的速率是多少

如果只使用 10 个 PRB，那么可以使用的载波也只有 120 个。

$$
120 \times 7 \times 4 \times \frac{3}{5} \times 2 \times 10^{3} = 4.032\ Mbps
$$

####  64 QAM 调制且无需编码的理想条件下可实现的最大下载速率

使用 64-QAM 表明一个 OFDM 符号有 $\log_{2}64 = 6\ bits$。

$$
324 \times 7 \times 6 \times 2 \times 10^{3} = 27.216\ Mbps
$$

#### 2×2 MIMO 系统下的 16-QAM 3/5 编码率和 64-QAM 下载数据速率

MIMO 技术可以通过同时使用多个天线来提高系统的吞吐量。在这种情况下，由于有两个发射天线和两个接收天线，MIMO 系统可以传输两个独立的数据流，从而将传输速率提高一倍。

$$
\begin{aligned}
& \text{16-QAM}+ 2\times 2\ \text{MIMO} = 10.88 \times 2 = 21.76\ Mbps \\
& \text{64-QAM} + 2\times 2\ \text{MIMO} = 27.216 \times 2 = 54.432\ Mbps
\end{aligned}
$$

## Lec 19 链路预算设计

### 分贝毫瓦转换、接收功率

![[数字通信 Slides 例题解析_4.png]]

#### 分贝毫瓦转换

![[分贝毫瓦与毫瓦的转换式]]
![[分贝瓦与瓦转换式]]

$$
\begin{aligned}
50 W & = 10 \log _{10}(50 \cdot 10^{3}mW)=46.98\ dBm \\
& = 16.98\ dBW
\end{aligned}
$$

#### 接收功率

![[自由空间损耗计算式|FSL calculation]]

>[!important]
>要做好这道题，需要理解下面这张图。
>
> ![[数字通信 Slides 例题解析_35.png|200]]
> 
> 这张图的含义是，$dB$ 表示的是一个**存粹的数值**，它不代表任何单位。但是 $dBm$ 和 $dBW$ 则是**功率单位的分贝形式**。同单位的分贝形式相减相当于相除，单位被约掉了，得到的是他们之间的倍数关系。

对于 100m 处的 FSL 为，

$$
\begin{aligned}
FSL & = 92.4 + 20 \log _{10}(0.1)+20 \log _{10}(0.9) \\
& = 71.48\ dB 
\end{aligned}
$$

对于 10km 处的 FSL 为，

$$
\begin{aligned}
FSL & = 92.4 + 20 \log _{10}(10)+20 \log _{10}(0.9) \\
& = 111.48\ dB
\end{aligned}
$$

接收到功率为，

$$
\begin{aligned}
\text{Recieved Power}_{dBm} & = Power - FSL \\
& = 46.98\ dBm - 71.48 dB = -24.5 dBm\ (100m) \\
& = 46.98\ dBm - 111.48 dB = -64.5 dBm\ (10km) \\
\end{aligned}
$$

### 计算发射最小功率

![[数字通信 Slides 例题解析_5.png]]

![[自由空间损耗计算式|FSL calculation]]

$$
\begin{aligned}
FSL & = 92.4 + 20 \log_{10}(0.01)+20 \log_{10}(0.9)=81.48 dB \\
& = 92.4 + 20 \log _{10} (0.01)+ 20 \log_{10}(5) = 96.37 dB
\end{aligned}
$$
题目要求区域内终端接收到的最小的功率为 $10 \mu W=-20 dBm$，
$$
\begin{aligned}
\text{Transmissiong Power}_{dBm} & = \text{FSL} + \text{Recieved Power} \\
& = 81.48 + (-20) = 61.48\ dBm (900MHz)\\
& = 96.37 + (-20) = 76.37\ dBm (5GHz)
\end{aligned}
$$

### 计算 EIRP 和基站的覆盖范围

![[数字通信 Slides 例题解析_6.png]]

#### 计算 EIRP

![[有效辐射功率计算式|EIRP calculation]]

在这道题目中，发射机输出功率为 25dB，天线增益为 13dBi，发射机输出端与天线馈线之间的损耗为 $8 \times 1.5= 12 dB$。可以计算出 EIRP 为，
$$
\begin{aligned}
\text{EIRP}_{dB} & = P_{t}+G_{t}-L_{t} \\
& = 25\ dB + 13\ dB - 12\ dB  \\
& = 26\ dB = 398.11 W
\end{aligned}
$$

#### 计算覆盖范围

根据题目中可知，移动终端能接收到的最小功率为 $-100\ dBm$。根据上一题算出的结果可知，FSL 的最大值为 $126 dB$。

![[自由空间损耗计算式|FSL calculation]]

$$
\begin{aligned}
FSL_{max} & = 126\ dB \\
& = 92.4 + 20 \log_{10}d + 20 \log_{10}10 \\
& \rightarrow d = 4.78\ km
\end{aligned}
$$

## Lec 20 物理层的传输设计

### 计算接收机检测器级的 SNR 

![[数字通信 Slides 例题解析_1.png]]

这里需要使用噪声系数的计算式，

![[噪声系数计算式]]

由此可以计算出接收端的 SNR 为：

$$
\begin{aligned}
SNR_{out} & = SNR_{in}-NF \\
& = 20dB - 6 dB \\
& = 14dB
\end{aligned}
$$

### 计算带宽和覆盖范围

![[数字通信 Slides 例题解析_2.png]]

#### 计算带宽

![[带宽计算式]]

在题目中，$R_b$ 为 5Mb/s；码率调制系数 $\rho$ 为 coding rate；调制阶数为 2，题目中说明了使用 QPSK 进行调制；RC 滤波器形状因子为 0.5。带入全部数据即可算出带宽。

$$
\begin{aligned}
\text{B}& =\frac{R_b}{\rho\cdot m}(1+r)  \\
&=\frac{5\times10^6}{1/2\times2}(1+0.5) \\
&=\frac{5\times10^6}{1}(1+0.5) \\
&=7.5\text{ MHz}
\end{aligned}
$$

#### 计算覆盖范围

![[自由空间损耗计算式]]

通过计算自由空间的传播

![[无线通信系统链路预算计算式]] ^33b744

![[有效辐射功率计算式]]

![[信道信噪比计算式]]
### 计算带宽与有效辐射功率

![[数字通信 Slides 例题解析_3.png]]

#### 计算带宽

![[带宽计算式]]

$$
\begin{aligned}
B & =\frac{5M}{\frac{1}{2} \cdot 16}(1+0.5) \\
& = 0.9375\ MHz
\end{aligned}
$$

#### 计算有效辐射功率

![[有效辐射功率计算式]]

![[无线通信系统链路预算计算式]]

![[信道信噪比计算式]]
