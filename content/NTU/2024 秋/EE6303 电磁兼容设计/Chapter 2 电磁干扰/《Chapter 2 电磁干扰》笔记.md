---
date: 2024-09-03 16:15
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 测试设施

## 1.1. 平行板/TEM 室/GTEM 室

### 1.1.1. 平行板

平行板传输线由两个平行板组成，一个在另一个之上，顶板的宽度小于或等于底板的宽度。

![[平行板传输线.png|300]]

平行板支持 TEM 波传播，而所有在远场中传播的电磁波都是 TEM 波。

![[条状线.png]]

平行板传输线的更一般情况是上板的宽度小于或等于底板的宽度。这种传输线称为带状线。较大的接地平面可确保边缘附近的场线失真较小。底面宽度一般**至少**需要为带状线的 3 倍。

## 1.2. 电容和电感

对于平行板传输线而言，有以下这些参数可以计算，

![[电磁干扰笔记_1.png|200]]

![[平行板传输线电容计算式]]
![[平行板传输线电感计算式]]

### 1.2.1. 相速度和波阻抗

由此可以计算相速度，

![[平行板相速度计算式]]

![[平行板波阻抗计算式]]

![[平行板特征阻抗计算式]]

一般来说，用于测量 TEM 波的条状线之间的介质都是空气，有 $\epsilon \approx 1$，基本能看作真空条件，使用自由空间的波阻抗来计算。

条状线的特征阻抗为，

![[条状线特征阻抗计算式]]

如果其中的电介质是不色散的，那么传输线的特征阻抗和频率无关。

### 1.2.2. 插入损耗

这里的插入损耗和 RF 的是一个概念。

![[用 dB 表示的插入损耗计算式]]

在这里的功率损耗比是指入射功率与负载功率的比值。

![[功率损耗比定义式]]

### 1.2.3. 电阻匹配网路的电阻计算

电阻匹配网络的目的是让从 $Z_{in}$ 这一端向里面看的时候，阻抗为 $50\pu{ \Omega }$（一般情况，如果用其他值会说明）。

![[电阻匹配网络.png|200]]

对于上面这个电阻匹配网络，有，
$$
\begin{cases}
Z_{in} =R_2|| (R_1+Z_0)\\ 
Z_0  =R1+Z_{in}||R_2 \\
\end{cases}
$$

引入 $Z' = 1-\dfrac{Z_{in}}{Z_{0}}$ 并解得，

![[条状线匹配网络阻抗计算式]]

### 1.2.4. 条状线例题

[[EE6303 例题合集#Stripline example]]

## 1.3. TEM 小室

TEM 小室是一个放大版的平行板，外部用屏蔽壳包裹住，平行板和外壳之间使用介电系数接近 1 的电介质隔开。电磁波的传播模式也为 TEM 模。

![[TEM 小室横截面.png|300]]

### 1.3.1. 特征阻抗

![[TEM 小室特征阻抗计算式]]
#挂起/信息不足 

### 1.3.2. 最大工作频率

当TEM CELL中电磁波的模式变为  $\text{TE}_{10}$ 模时，此时的频率是其最高工作频率。它在设计上是用来传输 TEM 模的，如果变成 $\text{TE}_{10}$ 模就不符合设计要求了，所以是最高工作频率。

![[TEM 小室最高工作频率计算式]]

### 1.3.3. TEM 小室设计

需要满足的基础条件有，

![[TEM 小室设计条件]]

说人话就是，平行板要有测试物的 1.5 倍高，至少要比测试物宽。

根据这个能确定 b 的取值，然后查表（

### 1.3.4. TEM 小室的优缺点

优点：
- 内部测试不会被外部影响
- 外部不会被内部测试影响
缺点：
- 工作频率从 DC 最高只能到 $f_{c}$

### 1.3.5. TEM 小室例题

[[EE6303 例题合集#TEM 小室例题]]

## 1.4. GTEM 小室

GTEM 小室是指 G 赫兹 TEM 小室，隔板末端有50欧的负载，并且还需要贴有吸波材料防止反射。能够支持 $1\pu{ GHz }$ 以上的频率。

![[GTEM 小室.png|300]]

### 1.4.1. GTEM 小室的优缺点

优点：
- 工作频率能到数 GHz
- 有屏蔽
缺点：
- 小
- 贵

## 1.5. 开放区域测试场地 (OATS)

在开放区域中执行测试，确保附近物体不会反射
需要导电接地层
通常在天线与测试对象之间的距离为 3m 和 10m 时进行测试。

![[电磁干扰笔记_2.png|300]]

## 1.6. 屏蔽外壳

目的为低发射水平测试提供安静的环境，提供高功率辐射衰减，确保重复性，不受天气影响
缺点，体积大，成本高

### 1.6.1. 屏蔽有效性

![[屏蔽有效性计算式]]

屏蔽有效性越大越好。

### 1.6.2. 吸收系数 A

![[复传播系数计算式]]

所以我们可以得到
$$
A=20log_{10}\left(e^{-\alpha r}\right) \quad \left[ \pu{dB}\right]
$$
对于理想导体和良导体有 $\sigma \gg \omega\epsilon$ （复传播系数的色散项）。此时有， 
$$
\gamma \approx \sqrt{ j\omega \mu \sigma } = \dfrac{1+j}{\sqrt{ 2 }}\sqrt{ \omega \mu \sigma }=\sqrt{ \dfrac{\omega \mu \sigma}{2} }+j\sqrt{ \dfrac{\omega \mu \sigma}{2} }
$$
可以取近似为 $\alpha \approx \sqrt{\frac{\omega\mu\sigma}{2}}$ ，可以推出良导体中的吸收系数为，

![[良导体的吸收系数]]

#### 1.6.2.1. 一些其他的变形

用相对电导率替换电导率、频率替换角频率、材料厚度 $t$ 替换传播距离 $r$ ：
$$
A=-20log_{10}e\times t\sqrt{\pi f \mu \sigma_r \sigma_c } \quad \left[ \pu{dB}\right]
$$
用趋肤深度 $\delta=\sqrt{\dfrac{1}{\pi f \mu \sigma}}$ 替换：
$$
A=-20log_{10}e\times \frac{t}{\delta}\quad \left[ \pu{dB}\right]
$$
用相对磁导率和电导率替换（此处 $t$ 的单位是 $\mathrm{cm}$ ）：
$$
A=1.314 t \sqrt{f \mu_r \sigma_r}\quad \left[ \pu{dB}\right]
$$

### 1.6.3. 反射损耗

垂直入射的情况下，透射系数相对于阻抗的关系为，

![[透射系数计算式]]

透射波阻抗为，

![[透射波阻抗计算式]]

假设有入射波功率为 $P_{0}$，则有透射功率 $P_{0}\times T^{2}$

![[反射损耗计算式]]

#### 1.6.3.1. 金属屏蔽罩的反射损耗

对于金属有 $\omega\epsilon\ll \sigma$ 可以得到，
$$
\left|\eta_2\right| = \left|\sqrt{\frac{j\omega\mu}{\left(\sigma+j\omega\epsilon\right)}}\right| \approx \sqrt{\frac{\omega\mu}{\sigma}}
$$
又由于 $\eta_1 \gg \eta_2$ 从而对反射损耗进行近似：
$$
R \approx 10log_{10}\left|\frac{4\eta_2}{\eta_1}\right|
$$
#### 1.6.3.2. 材料对入射平面波的反射损耗

入射波的特征阻抗为 $120\pi$ 所以可以得到
$$R = -10log_{10}\left(\frac{4\sqrt{\frac{2\pi f \mu_0 \mu_r}{\sigma_c \sigma_r}}}{120\pi}\right)$$
其中 $\mu_0$ 为真空磁导率， $\sigma_c$ 为铜的电导率。两个下标是 $r$ 的是相对值。

#### 1.6.3.3. 材料对入射电场的反射损耗

入射电场的特征阻抗
$$
\eta_1=\frac{\eta_0}{\beta_0 r}
$$
代入真空光速
$$c=\frac{1}{\sqrt{\mu_0 \epsilon_0}}$$
代入相位系数
$$\beta_0=\frac{2\pi}{\lambda}=\frac{\omega}{c}$$
可以得到
$$\eta_1=\frac{1}{\omega \epsilon_0 r}=\frac{1}{2\pi f \epsilon_0 r}$$

$$R \approx -10log_{10}\left(8\pi f\epsilon_0 r\sqrt{\frac{2\pi f \mu}{\sigma}}\right)$$
#### 1.6.3.4. 材料对入射磁场的反射损耗

类似地，可以计算出入射磁场的特征阻抗： 
$$\eta_1=\eta_0\beta_0 r=2\pi f\mu_0 r$$
代入可以得到反射损耗约为：
$$R \approx -10log_{10}\left(\frac{4\sqrt{\frac{2\pi f \mu}{\sigma}}}{2\pi f \mu_0 r}\right)$$

#### 1.6.3.5. 反射损耗公式总结

![[入射平面波反射损耗]]
![[入射电场反射损耗计算式]]
![[入射磁场反射损耗计算式]]

## 1.7. 电波暗室

反射率是描述反射电场强度的指标。吸波材料的反射率是入射角、反射角的函数。

### 1.7.1. 测量吸波材料的反射率

1. 测量入射波到理想导电平面（PEC）的反射
2. 计算反射电场强度和入射电场强度的比$$\frac{E_{r_{PEC}}}{E_i}$$
3. 把吸波材料放到 PEC 上，测量反射场强并计算$$\frac{E_{r_{Absorb}}}{E_i}$$
4. 反射率计算$$R=20log_{10}\left(\frac{E_{r_{Absorb}}}{E_i}\frac{E_i}{E_{r_{PEC}}}\right)$$
5. 重复不同的入射角计算

### 1.7.2. 吸波材料的种类

#### 1.7.2.1. Dielectric Absorber

轻

高介电损失（考虑复介电系数 $\epsilon=\epsilon^{\prime}+j\epsilon^{\prime\prime}$ 对于复介电系数，实部的定义与一般的介电系数相同，虚部表示电流在介质中的损耗）

无磁性 $\mu_r=1$

超宽带

厚

##### 1.7.2.1.1. 相关公式

[[EE6303 例题合集#]]

##### 1.7.2.1.2. 电波暗室使用的 Dielectric Absorber 的一些特性

被造成金字塔型

金字塔的高度决定了对不同频率的吸收率

反射率在 30-50dB 之间

工作频率：数百 MHz 到数 GHz

#### 1.7.2.2. Magnetic Absorber

使用含有磁性的材料（铁氧体、碳、镍）

薄

重

有损耗（不太理解，没损耗还能叫吸波材料么）

窄带

在低频下工作良好

##### 1.7.2.2.1. 相关公式

仍然使用亥姆霍兹方程的解（真好用）：

$$E\left(t\right)=E_0\left(t\right)e^{-\gamma z}$$

与复介电系数类似，复磁导率的虚部表示介质的损耗。

对于复磁导率

$$\mu=\mu^\prime-j\mu^{\prime\prime}$$

可以计算得到复传播系数的实部:

$$\alpha \approx \frac{\omega}{2}\sqrt{\epsilon_0 \mu^\prime}\frac{\mu^{\prime\prime}}{\mu^\prime}$$

同样地这里也存在磁场的损耗角正切

##### 1.7.2.2.2. 电波暗室使用的 Magnetic Absorber 一些特性

薄铁氧体陶瓷瓦片

频率范围 30MHz-1GHz

能承受高温和高功率

非常重（每平方米数十 kg）

## 1.8. 电波暗室的优缺点

### 1.8.1. 优点

测试物的体积没有限制

可以测量数十 Hz 到 40GHz 甚至更高

支持电场、磁场和平面波测量

屏蔽效率大于 100dB，能支持高功率辐射测量，低辐射泄漏

### 1.8.2. 缺点

为了覆盖频率、照射角和极化方向需要的时间很长

如果要测量更大的物体和更长的测试距离，需要更大的暗室

非常贵



## 1.9. 模式搅拌/电波混响室

### 1.9.1. 最低可用频率 LUF

LUF 是最低谐振频率的大约 4 倍

最低谐振频率的定义：

$$f_{mnp}=\frac{c}{2}\sqrt{\left(\frac{m}{a}\right)^2+\left(\frac{n}{b}\right)^2+\left(\frac{p}{h}\right)^2}$$

其中 $c$ 为真空光速， $a$ 、 $b$ 、 $h$ 是这个房间的长宽高.

 $m$ 、 $n$ 、 $p$ 是正整数，表示电磁波在房间中的模式分布，最多有一个可以是 $0$

### 1.9.2. 品质因数 Q 值

定义：

$$Q=\omega\frac{最大储存的能量}{平均能量损失}$$

$$\frac{1}{Q_{total}}=\frac{1}{Q_1}+\frac{1}{Q_2}$$

其中 $Q_1$ 是墙壁导致的损失， $Q_2$ 是天线的损失

$$Q_1=\frac{3V}{2\mu_r S \delta (\omega)}$$

其中 $V$ 是内部体积， $S$ 是内部墙壁表面积， $\delta(\omega)$ 是电磁波在导体的趋肤深度

$$Q_2=\frac{16 \pi^2 V}{m N \lambda^3}$$

其中 $m$ 是天线阻抗失配导致的损失， $N$ 是总天线数量

对于测量到的 $Q$ 值，定义如下：

$$Q=\frac{16\pi^2 V \left\langle P_R\right\rangle}{\lambda^3 \left\langle P_T\right\rangle}$$

$\left\langle P_R\right\rangle$ 和 $\left\langle P_T\right\rangle$ 分别是接收和发射功率的系统平均值

### 1.9.3. 房间增益

定义为：

$$ \left\langle G\right\rangle=\frac{\left\langle P_R\right\rangle}{\left\langle P_T\right\rangle}$$

### 1.9.4. 测量到的电场

定义为：
$$\left\langle|E_T|^2\right\rangle=\frac{8\pi}{\epsilon_0 c \lambda^2}\left\langle P_R\right\rangle=\left\langle|E_x|^2\right\rangle+\left\langle|E_y|^2\right\rangle+\left\langle|E_z|^2\right\rangle$$


# 2. 测试设备

## 2.1. EMI 接收机

EMI 接收机用于测量 EUT 的辐射。

![[电磁干扰笔记_3.png|400]]
![[EMI 接收机的框图.png|400]]
![[CISPR 16-1-1 提供了关于 EMI 接收机的数据.png|400]]

### 2.1.1. 窄带信号

信号载波与接收机接收频率相同的情况下，3dB 带宽小于接收机 3dB 带宽的信号被定义为窄带信号。

一般是CW[[连续波]]，调制后且带宽小于接收机带宽的CW连续波信号

### 2.1.2. 宽带信号

信号载波与接收机接收频率相同的情况下，3dB 带宽小大于接收机 3dB 带宽的信号被定义为窄带信号。

窄脉冲（冲激函数）、时钟信号（谐波分量大，频谱图为sinc函数的包络）、UWB脉冲（超宽带脉冲）

### 2.1.3. 检波器

从已调信号中检出调制信号的过程称为解调或检波。接收机的检波器一般用来测量目标信号的功率或者电压。对于没有调制的信号（CW连续波），所有检波器必须输出相同的RMS值。

![[连续波信号的均方根计算式]]

检波器具有以下类型，Peak Detector (PK)，Quasi Peak Detector (QP)，Root Mean Square Detector (RMS)，Average Detector (AV)

#### 2.1.3.1. 峰值检波器（PK）

![[峰值检波器]]

#### 2.1.3.2. 准峰值检波器（QP）

![[准峰值检波器]]

#### 2.1.3.3. 其他检波器
##### 2.1.3.3.1. 包络检波器

![[包络检波器.png]]

极小的充电和放电时间常数，跟随信号的包络。

##### 2.1.3.3.2. 均方根检波器（RMS）

![[均方根检波器]]

##### 2.1.3.3.3. 平均值检波器（AV）

![[平均值检波器]]

## 2.2. 天线

天线用于辐射测试。一般而言，天线的增益都是在远场中测量，但是 EMI 检测却是在近场进行。

EMI 一般在 E 场/H 场和接收电压下工作，而不是在辐射强度和接收功率下工作。

由此需要重新定义一套天线参数，
- 天线系数（AF）
- 发射天线系数（TAF）

### 2.2.1. 天线系数

![[天线系数定义式]]

这个描述的是电场在**接收**天线的**负载**上产生单位电压的情况。很明显这边假设的是极化与天线是匹配的，并没有考虑极化损耗。天线系数越小，相同电场强度的情况下接收到的电压越高。

#### 2.2.1.1. 线天线

$$AF\mathrm{@20kHz}=75\mathrm{dB}/m$$
$$AF\mathrm{@20MHz}=25\mathrm{dB}/m$$

如果电场强度为 $1V/m$ 的话，天线接收到的电压为：

20kHz:

$$V=\frac{E}{AF}=E\left(\mathrm{dB}\right)-AF\left(\mathrm{dB/m}\right)=\frac{1}{10^{75/20}}=0-75=-75\left(\mathrm{dBV}\right)=0.17mV$$

20MHz:

$$V=\frac{E}{AF}=E\left(\mathrm{dB}\right)-AF\left(\mathrm{dB/m}\right)=\frac{1}{10^{75/20}}=0-25=-25\left(\mathrm{dBV}\right)=56.23mV$$

### 2.2.2. 发射天线系数

$$TAF=\frac{E_{1m}}{V_t} m^{-1}=20log_{10}E_{1m}-20log_{10}V_t \left(\mathrm{dB}/m\right)$$

其中 $E_{1m}$ 是发射天线在 1m 处测量到的场强， $V_t$ 是发射电压。TAF 越大，产生的电场强度越大。

对于同一个天线，AF 和 TAF 不一样

#### 2.2.2.1. 对数周期天线

对数周期天线可以在很宽的频率上产生强电场。

如果输入功率为 10W，频率 22MHz，1m 处产生的场强为 10V/m，可以计算得到：

假设是 50 欧负载，输入天线的电压为：

$$V=\sqrt{P\times Z_0}=22.360V$$

所以

$$TAF=\frac{10}{22.360}=0.45m^-1$$

用 dB 做法也可以：

$$22.360V=26.989\mathrm{dB}V=146.989\mathrm{dB}\mu V$$

$$10V/m=20\mathrm{dB}V\cdot m^{-1}=140\mathrm{dB}\mu V\cdot m^{-1}$$

$$TAF=-6.989\mathrm{dB}/m$$

#### 2.2.2.2. 环形天线（磁场天线）

感应电压 (Induced Voltage)：

$$V_i=-n\frac{\mathrm{d}\Phi}{\mathrm{d}t}=2\pi f n A B$$

$n$ 为线圈匝数， $f$ 为频率， $A$ 为线圈的截面积， $B$ 为磁感应强度。

### 2.2.3. $AF_H$ 和 $AF_B$

$$AF_H=\frac{H}{V_L}S/m=\frac{1}{2\pi f n A \mu_0}$$

$$AF_B=\frac{B}{V_L}=\frac{\mu H}{V_L} Tesla/V$$

$$AF=AF_H\times \eta_0=\frac{H}{V_L}\times \frac{E}{H}=\frac{E}{V_L}$$

$$AF\left(\mathrm{dB}/m\right)=AF_H\left(\mathrm{dB}S/m\right)+20log_{10}\left(\eta_0\right)$$

### 2.2.4. Antenna Example 1 作业形式

$$V_{in}=\sqrt{P\times Z_0}=50V=33.9794\left(\mathrm{dB}V\right)$$

$$E_{1m}=TAF\left(\mathrm{dB}/m\right)+V_{in}\left(\mathrm{dB}V\right)\\
=33.9794-4=29.9794\left(\mathrm{dB}V/m\right)
$$

$$E_{3m}=E_{1m}\left(\mathrm{dB}V/m\right)-20log_{10}(3m)+20log_{10}(1m)=20.436975\left(\mathrm{dB}V/m\right)
$$

$$V_L=E_{3m}\left(\mathrm{dB}V/m\right)-AF\left(\mathrm{dB}/m\right)=20.436975-23=-2.5630\left(\mathrm{dB}V\right)=0.74V$$

# 3. ESD

由高静电场引起的静电电荷的快速、自发转移。当两个具有不同静电势的物体相互靠近时，电荷会流过它们之间的火花。 

最常见的是由两种材料（可能相似或不同）接触和分离而产生，尽管不同的材料往往会释放更高水平的静电荷。

## 3.1. ESD 的危害

ESD 会造成电子器件损坏，严重的可能引起火灾。

## 3.2. 静电电势和电流

用以下的公式计算静电的电荷量。
![[电荷量计算式]]

静电释放实际上就是电容器的击穿。假设静电在 $t$ 内释放完，其电流为，
![[电容电流计算式]]

影响静电电压和电流的因素，
- 电荷转移（摩擦起电）很复杂，取决于：
	- 接触面积
	- 分离速度
	- 相对湿度 - 空气中的水分含量往往会降低地板、地毯、桌垫等的表面电阻，因为湿颗粒会产生模糊的表面电阻。绝缘表面上的导电薄膜。即高相对湿度意味着较低的电荷累积
- 材料的化学性质
- 表面功函数等。

## 3.3. 示例计算

[[EE6303 例题合集#静电电势和静电电流]]

## 3.4. ESD 耦合

### 3.4.1. ESD 电流的磁场耦合

磁场强度有，
![[距离导线远 d 处的磁场强度计算式]]

磁通量密度有，
![[磁通量密度计算式]]

磁场感应电压为，
![[磁场感应电压计算式]]

### 3.4.2. 感应电压计算

[[EE6303 例题合集#感应电压计算]]
