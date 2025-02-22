---
aliases:
  - Dynamic Dissipation
tags:
  - digital
  - power
---
# Goh

- Dynamic power is required to charge & discharge load capacitances when transistors switch.
  在晶体管开关时，充电和放电负载电容需要动态功耗
- One cycle involves a rising and falling output.
  一个周期包含一个上升和下降输出
- On rising output, charge $Q = CV_{DD}$ is required
  在输出上升时，需要电荷$Q = CV_{DD}$
- On falling output, charge is dumped to GND
  在输出下降时，电荷被释放到地（GND）
- This repeats $Tf_{sw}$ times over an interval of $T$
  这个过程在时间间隔$T$内重复$Tf_{sw}$次
- $P_{\text{dynamic}}=C_L V_{DD}^2 f_{sw}$, $f_{sw}=\alpha f$, 其中$f$为时钟频率，$\alpha$为[[Switching Activity]]

# Gwee

- When the capacitor $C_L$ gets charged through the pMOS transistor, its voltage rises from 0 to Vdd, and a certain amount of energy ($C_LV_{DD}^2$) is drawn from the power supply. Part of this energy ($1/2 C_LV_{DD}^2$) is dissipated in the pMOS device, while the remainder is stored on the load capacitance. During the high-to-low transition, this capacitor is discharged, and the stored energy is dissipated in the nMOS transistor
  当电容$C_L$通过pMOS晶体管充电时，其电压从0升高到Vdd，并从电源汲取一定量的能量($C_LV_{DD}^2$)。其中一部分能量($1/2 C_LV_{DD}^2$)在pMOS器件中耗散，剩余的能量存储在负载电容上。在高到低转换期间，该电容放电，存储的能量在nMOS晶体管中耗散
- Each switching cycle (consisting of an $L\to H$ and an $H\to L$ transition) takes a fixed amount of energy, equal to $C_LV_{DD}^2$
  每个切换周期（包括从L到H和从H到L的转换）需要固定的能量，等于$C_LV_{DD}^2$
- Power consumption is dependent on how often the device is switched. If the gate is switched on and off f times per second, the power consumption equals
  功耗取决于设备开关的频率。如果栅极每秒开关$f$次，则功耗等于
  $$P_{\text{dynamic}}=f C_LV_{DD}^2$$
	- Actual activity is somewhat lower as not all gates in the complete IC switch at the full rate of $f\mathrm{MHz}$ and this is accomodated by replacing $C_L$ by $C_{EFF}=\widehat{C_L}$ where $C_{EFF}$ (effective capacitance) is the average capacitance switched every clock cycle and $\widehat{P_{0\to 1}}$ is the activity factor.
	  实际活动要低一些，因为并非所有IC中的门都以$f\mathrm{MHz}$的全速率切换，因此将$C_L$替换为$C_{EFF}=\widehat{C_L}$来解决这一问题，其中$C_{EFF}$（有效电容）是每个时钟周期切换的平均电容，而$\widehat{P_{0\to 1}}$是活动因子

# CC

- In CMOS designs, power consumption is a function of power supply ($V_{DD}$), operating frequency ($f$), total load capacitance ($C_L$) and switching activity ($\alpha$).
  在CMOS设计中，功耗是电源电压($V_{DD}$)、工作频率($f$)、总负载电容($C_L$)和切换活动($\alpha$)的函数
  $$P=f\times C_L \times V_{DD}^2 \times \sum\alpha$$
- It can be seen from the equation that reducing  leads to quadratic power savings.
  由该方程可以看出，减少$V_{DD}$会带来二次方的功率节省
- However, reducing $V_{DD}$ also leads to delay increasing and loss of performance.
  然而，减少$V_{DD}$也会导致延迟增加和性能损失
