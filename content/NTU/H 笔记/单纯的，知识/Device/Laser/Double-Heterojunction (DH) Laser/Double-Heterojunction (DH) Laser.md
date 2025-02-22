---
aliases:
  - DH Laser
tags:
  - laser
  - semi_conductor
  - heterostructure
---

The energy diagram of a DH lasers made of GaAs/AlGaAs
![[Pasted image 20241103040341.png#pic_center|]]
- The stimulated emission is from the GaAs, and the emission frequency $\nu$ is such that $h\nu=E_g(\mathrm{GaAs})$. The corresponding wavelength$$\lambda(\mu \mathrm{m})=1.24/E_g(e\mathrm{V})=0.880\mu \mathrm{m}$$
  受激发射源于GaAs，其发射频率$\nu$满足$h\nu=E_g(\mathrm{GaAs})$。
- To achieve tuning wavelength of laser, an AlGaAs layer should be the active layer instead of GaAs. But the bandgap of the AlGaAs active layer must be less than that of the p-AlGaAs and n-AlGaAs barrier layers.
  为了实现激光波长可调，有源层应该使用AlGaAs而不是GaAs。但AlGaAs有源层的带隙必须小于p-AlGaAs和n-AlGaAs势垒层的带隙。

# Threshold Current & Threshold Current Density

- The threshold current is the minimum current required for lasing to occur.
- The current upto threshold is given by the usual forward biased [[Diode I-V Relation|p-n junction current equation]].
  小于阈值电流的电流表达式由普通的正向偏置 p-n 结电流方程给出。$$I=I_o\left(e^{\frac{V_A-IR_S}{V_T}}-1\right)$$Where: ^52252a
	- $V_A$ is the applied voltage
	- $I_o$ is the saturation current at the operating temperature $T(K)$
	- $R_S$为串联等效电阻
- Once laser action starts above the threshold, then the junction voltage drop is $\frac{E_g}{q}$ , where $E_g$ is the active layer bandgap. The current now will be
  一旦激光作用超过阈值，结电压降为 $\frac{E_g}{q}$，其中 $E_g$ 是有源层的带隙。此时的电流将会是$$I=\frac{V_A-E_g/q}{R_S}$$ ^9ec28f
- The threshold current density can be expressed as$$J_{\mathrm{threshold}}=\frac{1}{\beta}\left[\alpha+\frac{1}{2L}\mathrm{ln}\left(\frac{1}{R_1R_2}\right)\right]$$where:
	- $\beta$ is the **gain factor**
	- $\alpha$ is the loss per unit length from absorption and other scattering mechanism
	- $L$ is the cavity length
	- $R$ is the reflectance of the cavity$$R=\left(\frac{n-1}{n+1}\right)^2$$
  $J_{\mathrm{threshold}}$ may be different in different book

# Threshold Current Varies With Temperature

![[Pasted image 20241103044849.png]]

- (a) Light Output versus Diode Current for a GaAs/AlGaAs DH laser.
	- the output power becomes lower at high temperature
	- $I_{\mathrm{threshold}}$ increases with temperature
- (b) Temperature Dependence of the Continuous-Wave Current Threshold.
	- $I_{\mathrm{threshold}}$ follows an exponential relation with temperature,$$I_{\mathrm{threshold}}=I_o e^{\frac{T}{T_o}}$$where:
		- $I_o$ is a **constant**, dependent on device type and size
		- $T_o$ is called **characteristic temperature**, 110 Celsius for this laser

# Example

A double heterojunction laser diode is connected in a closed circuit with a series resistor and a variable power supply. The device shows no emission at a bias of 2V and an injected current of 0.9A but strong emission at a bias of 5.7V and a current of 2A. Assume that the device operates at room temperature and has a saturation current of 0.1A.

## Solution

由于在室温（300K），所以热电压为$V_T=26m\mathrm{V}$

饱和电流$I_S=0.1\mathrm{A}$

在2V正向电压时没有发射，在此时套用普通的pn结电流公式：$$I=I_S\left(e^\frac{V_F-IR_S}{V_T}-1\right)$$

代入饱和电流和热电压可以解得$$R_S=2.16\Omega$$

代入超过阈值的电流公式求带隙：$$I=\frac{V_A-E_g/q}{R_S}\implies E_g=1.38e\mathrm{V}$$（这里的单位选择电子伏特会比较好算）

算波长$$\lambda=\frac{ch}{E_g}=900\mathrm{nm}$$
上式中：
- $c$为光速
- $h$为普朗克常数
