---
title: System Design（Qe）
date: 2023-05-10 15:50
modification date: 2023 五月 10日 星期三 15:50:53
aliases:
  - 
tags:
  - 
publish: "true"
---

## Introduction (Q a)

### Project overview

在这个项目中，我们需要设计一个温度传感器。这个传感器需要能实现以下的功能：首先能够测量-25~+75 摄氏度的温度；其次能够将测得的温度以及设备 ID 输出给其他的设备；然后能够在温度超出测量范围或者温度为正或者负的时候点亮对应的 LED。

为了实现设计的功能，我们围绕着 PT1000构建了以下的功能模块。第一，通过使用一个恒定小电流直流源来给 PT1000 进行供电。在电流源恒定的时候， PT1000 能根据外界温度的变化而改变电阻阻值。第二，通过使用仪表放大器来放大 PT1000 上的电压压降并且滤除共模信号。第三，通过设计一个 ADC 元件将温度信号转换为一个 8bits 的数字信号。第四，使用一个 MCU 来实现温度数据的寄存、输出和比较。温度数据在输入 MCU 后被储存到了一个寄存器之中。通过一个 SPI 输出模块将 4bits 的设备 ID，bits 温度值和用来表示温度是否在范围之内的 1bit 信号。第四则是为所有需要供电的电路的电源元件。

In this project, we need to design a temperature sensor with the following functionalities: first, it should be able to measure temperatures ranging from -25 to +75 degrees Celsius; second, it should output the measured temperature and the device ID to other devices; third, it should light up the corresponding LED when the temperature exceeds the measurement range or when it is positive or negative.

To achieve the design's functionalities, we built the following functional modules around the PT 1000. First, we use a constant low current DC source to power the PT 1000. When the current source is constant, the resistance value of PT 1000 changes with the external temperature. Second, we use an instrumentation amplifier to amplify the voltage drop on PT 1000 and filter out the common-mode signal. Third, we design an ADC component to convert the temperature signal into an 8-bit digital signal. Fourth, we use an MCU to implement the storage, output, and comparison of temperature data. The temperature data is stored in a register after input to the MCU. The 4-bit device ID, bits representing temperature values, and a 1-bit signal indicating whether the temperature is within the range are output through an SPI output module. The fourth is the power component for all the power-supplying circuits that need it.

### Application

1.  环境监测：温度传感器系统可以用于测量室内和室外温度，帮助人们更好地管理室内温度，提高舒适度，并提高室内能源效率。
2.  工业控制：温度传感器系统可以用于监测工业设备的温度，防止设备过热或过冷，并提高设备的使用寿命和效率。
3.  农业生产：温度传感器系统可以用于农业生产中的温室和养殖业，监测环境温度，帮助农民掌握生产环境变化，提高农作物和养殖动物的生产效率。
4.  医疗保健：温度传感器系统可以用于医疗保健中的体温监测，帮助医务人员及时发现体温异常，预防疾病传播，保障患者的健康和生命安全。
5.  物流管理：温度传感器系统可以用于物流管理中的温度监测，帮助保证货物在运输过程中的质量和安全，减少货损率和退货率。

1. Environmental monitoring: The temperature sensor system can be used to measure indoor and outdoor temperatures, helping people better manage indoor temperatures, improve comfort, and improve indoor energy efficiency.
2. Industrial control: The temperature sensor system can be used to monitor the temperature of industrial equipment, prevent equipment from overheating or becoming too cold, and improve the lifespan and efficiency of equipment.
3. Agricultural production: The temperature sensor system can be used in greenhouse and livestock production in agriculture to monitor environmental temperature, help farmers understand changes in production environment, and improve crop and animal production efficiency.
4. Healthcare: The temperature sensor system can be used for body temperature monitoring in healthcare, helping medical staff detect abnormal temperatures in a timely manner, prevent disease transmission, and ensure the health and safety of patients.
5. Logistics management: The temperature sensor system can be used for temperature monitoring in logistics management, helping to ensure the quality and safety of goods during transportation, reduce damage and return rates.

### Challenge

我们认为，在整个温度测量系统之中，会有以下这些挑战，

1. 参考电阻的选择 - 选择合适的参考电阻可以保证温度测量的准确性和稳定性。
2. 放大器的设计 - 放大器需要具备高放大倍数和低噪声等特性，以便于传感器信号的放大和处理。
3. ADC 的设计 - ADC 需要具备足够的分辨率和采样速率，以确保准确地将模拟信号转换为数字信号。
4. 温度信号的校准 - 经过放大器和 ADC 转换后的数字信号需要进行校准，以补偿可能存在的误差和漂移。
5. 建立一个寄存器 - 通过建立寄存器，可以存储温度数据，并通过 SPI 串口向外输出，从而实现对温度传感器数据的读取和控制。

We believe that there will be the following challenges in the entire temperature measurement system:

1. Selection of reference resistor - Choosing the appropriate reference resistor can ensure the accuracy and stability of temperature measurement.
2. Amplifier design - The amplifier needs to have characteristics such as high gain and low noise to facilitate the amplification and processing of sensor signals.
3. ADC design - The ADC needs to have sufficient resolution and sampling rate to ensure accurate conversion of analog signals to digital signals.
4. Calibration of temperature signal - The digital signal after amplification and ADC conversion needs to be calibrated to compensate for any possible errors and drift.
5. Establishing a register - By establishing a register, temperature data can be stored and output externally through the SPI serial port, thereby achieving reading and control of temperature sensor data.

## Working Block (Q b)

## Sub-block (Q c)

All details are shown in **Appendix A**.

## Overall system design (Q e)

根据题目的要求，我们进行了以下的总体设计。

本设计旨在使用 PT100进行温度测量，主要包括以下模块：

- 恒流源模块
- 温度测量模块
- 差分放大降噪模块
- 校准模块
- ADC 转换模块
- MCU 控制模块
- SPI 输出模块
- LED 报警模块

首先给 PT100 提供一个稳定的电流源，使得 PT100 两端的电压差只和温度相关。随后通过使用仪用放大器放大电阻的差分信号并且进行一定的降噪。随后电压信号将经过校准电路进行校准，再将校准后的电压输送到 ADC。然后通过 ADC 将模拟信号转化为 12bits 数字信号。将 12bits 的数字信号输入到 MCU 的寄存器中。SPI 串口则会读取寄存器的温度值并通过 3.3V 电压输出。比较器将比较寄存器中的温度值判断是否需要点亮 LED。

According to the requirements of the task, we have made the following overall design.

This design aims to use PT 100 for temperature measurement, mainly including the following modules:

- Constant current source module
- Temperature measurement module
- Differential amplification and noise reduction module
- Calibration module
- ADC conversion module
- MCU control module
- SPI output module
- LED alarm module

Firstly, provide a stable current source for PT 100, so that the voltage difference between the two ends of PT 100 is only related to the temperature. Then, the differential signal of the resistance is amplified using an operational amplifier and filtered to reduce noise. Afterwards, the voltage signal will be calibrated and then sent to the ADC. The analog signal will then be converted to a 12-bit digital signal by the ADC. The 12-bit digital signal will be input to the MCU's register. The SPI interface will read the temperature value from the register and output it with a 3.3 V voltage. The comparator will compare the temperature value in the register to determine whether to turn on the LED alarm.

![[System Design（Qe）_1.png]]

Analog

| Module Name                           | Function Description                                       | Input                                | Output       |
| ------------------------------------ | ---------------------------------------------------------- | ------------------------------------ | ------------ |
| Constant current source module       | Provide a stable current source for PT 100                  | Power supply voltage                  | Current      |
| Temperature measurement module       | Measure temperature through PT 100                          | Current from constant current source | Voltage      |
| Differential Amplification and Noise Reduction Module | Amplify the differential voltage signal from PT 100 and reduce noise | Voltage                              | Amplified voltage |
| Calibration Module                    | Adjust the gain and offset of the amplified voltage signal | Amplified voltage                    | Calibrated voltage |
| ADC module                            | Convert analog signal to digital signal                     | Calibrated voltage                   | Digital data |

Digital

| Module Name        | Function Description                                   | Input                 | Output          |
| ------------------ | ------------------------------------------------------ | --------------------- | --------------- |
| MCU module         | Control the overall system and process temperature data | Digital data          | Temperature data |
| SPI output module  | Send temperature data to external devices              | Temperature data      | SPI output data |
| Comparator module  | Compare the temperature with the set threshold value   | Temperature data      | LED status      |

## Commentary and defects (Q f)

### Difficulty in eliminating noise

The Pipeline ADC is a high-speed and efficient ADC design, but it also has some difficulties and drawbacks, one of the main problems being the difficulty in eliminating the introduced noise.

The formula for the Pipeline ADC is as follows:

$$
Vout = \left( \frac{V_{ref}}{2^{n}}\right) \cdot \left( b_{0} + \frac{b_{1}}{2} + \frac{b_{2}}{2^{2}}+ ... + \frac{b_{n}}{2^{n}} \right)
$$

Where $V_{ref}$ is the reference voltage, $n$ is the number of bits in the ADC, and $b_{n}$ is the binary code output from the comparator.

In Pipeline ADC, due to the use of multiple stages in a cascaded architecture, the noise generated in each stage is transmitted to the next stage and ultimately accumulated, resulting in an increase in the overall noise level of the system. This problem is particularly serious during high-speed operation. In addition, since the noise in the ADC system is very difficult to predict and control, measures must be taken to reduce the impact of noise when designing an ADC. Common noise suppression techniques currently include:

1. Reducing input signal noise. This can be achieved by optimizing sensor design and selecting low-noise amplifiers, among other methods.

2. Reducing the noise of the ADC itself. This can be achieved by reducing the sampling rate, optimizing the power supply and reference voltage, and other methods.

3. Using digital signal processing techniques for noise suppression. This includes using digital filters, noise reduction algorithms, and signal averaging to reduce noise.

However, for Pipeline ADC, these noise suppression techniques may not be effective enough. This is because in Pipeline ADC, due to the coupling between stages, noise is easily accumulated and these noises are unknown before digital post-processing. Therefore, even if noise suppression techniques are used, it is difficult to completely eliminate noise.

To further illustrate the difficulty of eliminating noise in Pipeline ADC, let's take an example.

Suppose a 12-bit Pipeline ADC has a sampling frequency of 10 MHz and a reference voltage of 1 V. We assume that the gain of each stage is 1, and the noise power spectral density is -150 dBm/Hz, which means that the square of the noise voltage decreases to 10^-15 W per Hz. Temperature is 300k. Consider a sine wave input signal with an amplitude of 100 mV, a frequency of 1 MHz, and a phase of 0.

Since the input signal is a sine wave with a frequency of 1 MHz, its power is:

$$P_{in} = \frac{V_{p}^2}{2} = \frac{(70.7\text{ mV})^2}{2} \approx 2.5\text{ mW}$$

$$
P_{indBm}=10\cdot \log_{10}\left( \frac{P_{mW}}{1mW} \right)\approx 6.98 \text{ dBm}
$$

The noise power can be calculated based on the given ambient temperature and system bandwidth in the problem:

$$P_{noise} = 10\cdot log_{10} \left( \frac{K\cdot B\cdot T}{1 mW} \right) \approx -103\text{ dBm}$$

4. Calculate the signal-to-noise ratio.

Since ADC sampling noise is additive, we can calculate the signal-to-noise ratio (SNR):

$$SNR = 10\log_{10}\left(\frac{P_{in}}{P_{noise}}\right) \approx 103\text{ dB}$$

5. Calculate the theoretical resolution.

The theoretical resolution of a 12-bit ADC is:

$$LSB = \frac{V_{ref}}{2^{12}} = \frac{1\text{ V}}{4096} \approx 244\text{ $\mu$V}$$

6. effect of noise.

Based on the calculation of the signal-to-noise ratio (SNR), it can be seen that the noise of the ADC accounts for most of the entire signal. In this case, even if the input signal has no noise, the output of the ADC will still be affected by the noise, leading to a decrease in the accuracy of the output. In addition, since the Pipeline ADC uses a cascaded structure, the noise in each clock cycle will accumulate, resulting in a larger amount of noise in the final output. Therefore, the noise problem in Pipeline ADC is difficult to eliminate, and it is necessary to reduce the system bandwidth or adopt other noise reduction techniques to reduce the impact of noise.

### The accuracy of temperature sensor is difficult to be less than $0.25^{\circ}C$ 

温度传感器最终的输出精度受到整个系统的影响。从恒流源的稳定性，PT 1000 的稳定性，再到仪用放大器和 ADC 在放大信号和转换信号的时候都难免产生噪声。在进行仿真的时候，由于没有 PT1000 的热敏电阻模型，我们只能通过使用其他的热敏电阻模型来对 PT1000 进行近似。

我们对 PT1000 的 datasheet 进行了分析。随着温度从-25 逐渐上升到 75，PT 1000 的电阻变化从 4.00 $\ohm$ / $^{\circ}C$ 变化到 3.80 $\ohm$ / $^{\circ}C$ 
