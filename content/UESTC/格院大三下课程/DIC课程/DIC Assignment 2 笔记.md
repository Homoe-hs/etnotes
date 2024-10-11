---
title: DIC Assignment 2 笔记
date: 2023-06-07 10:30
modification date: 2023 六月 7日 星期三 10:30:49
aliases:
  - 
tags:
  - 
publish: "true"
---

## Assignment 2 作业内容

Assignment # 2是课程的主要部分。在这个任务中，您将使用 Assignment # 1中得出的数据表，设计和实现设计的不同部分。下面的部分详细说明了需要完成的工作。然而，由于要完成的工作量很大，因此将分为三个由 2 人组成的小组。这个分组包括每个小组的技术任务和任务之间的协调。具体而言，分组如下：

子组 1：技术任务为问题 1、6，协调任务为问题 3。

问题 1：放大器/电流源
(a) 计算适用于 PT 1000 探测器和模数转换器接口的合适放大器的参数（增益、输入阻抗等）。
(b) 通过计算来证明您的要求。
(c) 设计满足 Assignment # 1中得出的规格要求或 (a)和 (b)中得出的规格要求的放大器（此任务包括电流源）。
(d) 使用 ElectricVLSI 为放大器和电流源模块提出布局方案。

问题 3：组合电路
(a) 组合经验证的放大器和模数转换器设计，并通过仿真验证组合电路是否符合规格要求。
(b) 在验证模拟设计后，组合和优化电路的版图。

问题 6：检查温度是正数还是负数
(a) 提出控制绿色和红色 LED 的功能设计/框图。（ 如果测量温度为负值（即 T<0），红色 LED 应点亮；如果温度为正值（即 T>0），则绿色 LED 应点亮 ）
(b) 使用 Xillinx Vivado，在 (a)中编写一个行为描述，并通过仿真验证功能设计。
(c) 提出您设计的 RTL 电路。
(d) 提出数字部分的版图方案。

## 电流源设计

电流源是用来给 PT1000 供电的，首先是需要保证电流源是恒定的。其次要根据 PT 1000
的 datasheet 来决定给出的电流源的大小是多少。

![[Assignment 2 笔记_1.png]]

可以根据 pt1000 的数据表看出，在-25~75 的温度范围内，电阻在 900~1300 $\Omega$ 变化。如果恒定电流为 1mA，那么 PT1000 的电压变化范围为 0.9v-1.3v，属于非常理想的范围。

### 基础电流镜

![[Assignment 2 笔记_2.png]]

![[Assignment 2 笔记_3.png]]

目前这个参数能够实现 $I_{ref}=1mA$，输出比为 1。

M 2 用作电流源，提供 $I_{ref}$ 。$I_{out}$ 和 $I_{ref}$ 有以下的关系，
$$
I_{out}=I_{ref}\times \frac{\left( \frac{W}{L} \right)_{4}}{\left( \frac{W}{L} \right)_{3}}
$$
通过下面这张图可以看出，当电压是的 mos 管导通之后，VDD 的增加也会导致电流的增加。这样会使得电流非常不稳定。

![[Assignment 2 笔记_4.png]]

同样对 V1 进行直流扫描，发现和 VDD 有着类似的规律，同样会导致电流的线性变化。

![[Assignment 2 笔记_5.png]]

我们将 $I_{ref}$ 设定为 $100\mu A$。

![[Assignment 2 笔记_8.png]]

![[Assignment 2 笔记_9.png]]

### 自偏置电流基准源（beta multiplier current source）

[自偏置电流基准--Beta Multiplier - 知乎](https://zhuanlan.zhihu.com/p/555389065)

未加启动电路的自偏置电流基准源，输出为 1mA

![[Assignment 2 笔记_10.png]]



#### 启动电路

有两种选择：
一是添加启动电路，该启动电路的缺点是，在启动完成之后，仍要耗费静态电流

![[Assignment 2 笔记_1.jpg]]

二是添加 NMOS

![[Assignment 2 笔记_2.jpg]]

这个启动电路相对于前面提到的那个来说，在稳态下少一条电流支路，不会耗费多余的静态电流。

#### 体效应

![[体效应]]

![[考虑体效应的阈值电压计算式]]

![[Assignment 2 笔记_6.png]]

#### 最终设计

M 1 和 M2 的宽长比为 1.15

![[Assignment 2 笔记_14.png]]
### 电流源版图

![[Assignment 2 笔记_13.png]]

## 比较器设计

### 任务内容

问题 6：检查温度是正数还是负数
(a) 提出控制绿色和红色 LED 的功能设计/框图。（ 如果测量温度为负值（即 T<0），红色 LED 应点亮；如果温度为正值（即 T>0），则绿色 LED 应点亮 ）
(b) 使用 Xillinx Vivado，在 (a)中编写一个行为描述，并通过仿真验证功能设计。
(c) 提出您设计的 RTL 电路。
(d) 提出数字部分的版图方案。

### 代码

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.STD_LOGIC_UNSIGNED.ALL;
USE IEEE.STD_LOGIC_ARITH.ALL;

entity temp_comparator is
port(
    voltage: in std_logic_vector(8 downto 0);
    red_led: out std_logic;
    green_led: out std_logic
);
end temp_comparator;

architecture Behavioral of temp_comparator is
begin

process(voltage)
begin
  if voltage < "100110011" then --1000 ohms, 3V
    red_led <= '1';
    green_led <= '0';  -- when temp is neg,turn on the red LED, turn off the green LED
  else
    red_led <= '0';  
    green_led <= '1';  -- when temp is pstv,turn off the red LED, turn on the green LED
  end if;
end process;

end Behavioral;
```

### RTL

![[Assignment 2 笔记_15.png]]

### 门电路实现

![[
Snipaste_2023-06-11_17-47-36.png]]

### 版图实现

![[comparator.png]]

### 测试结果

![[Assignment 2 笔记_16.png]]

### 报告内容

这部分有几个函数。首先需要实现的功能是设置一个温度范围（-20-80）。第二，在这个温度范围之外，可以发出持续的高电位信号，驱动外部 LED 灯处于点亮状态。第三，在此温度范围内，可以继续发出低电位信号，使外部 LED 处于关闭状态。整个过程可以用两个比较器和/或门来实现。因此，我们可以确定我们需要的输入和输出信号。输入信号是经过修改的 12 位温度信号 (i_temp_data) 和每 30 秒读取一次 ADC 数据的使能信号 (i_temp_valid)。并输出信号控制 LED 开关高低电平信号（o_LED）。下面是温度检测电路的功能框图。

行为描述所有 Verilog 代码都显示在附录 A 中。 Simulation Result (test bench 代码见附录 A) 下面是运行 Test Bench 的仿真结果 (图14)。我们可以发现，当12位温度输入超出-20~80的范围时，LED 的数字信号输入为“1”，使 LED 点亮，直到温度回到设定范围内，LED 的数字输出为“1”。 LED 变为“0”。

这一部分的主要功能是实现对 ADC 传输的 9bits 信号进行比较，并且根据比较的结果点亮红色或者绿色的 LED 灯。根据 ADC 的设计，0 摄氏度对应的 3V 电压在经过 ADC 的转换之后，生成 9 位的二进制数“100110011”。将之后 ADC 传过来的数据和“100110011”相对比。在温度大于或等于 0 摄氏度的时候亮绿灯，在温度小于 0 摄氏度的时候亮红灯。

VHDL 代码在附录 A 中。RTL 电路和通过门电路实现的电路如下。

我们对电路的功能进行了测试，发现其能在温度为负的时候电亮红灯，温度为正的时候点亮绿灯，以下是测试结果。