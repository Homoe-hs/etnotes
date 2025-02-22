---
aliases: 
tags:
  - analysis
  - digital
  - eda_tools
---

- Also called Logic Simulation
- Netlist is a set of logic gates and their interconnects
- Models for logic gates are used
- Gate model includes function, input pin capacitance, output pin capacitance and delay model (for calculation of delays)
- Simulation results are waveforms of logic values, with or without delays
- Fast as compared to circuit simulation

# Logic Strength

- In Logic Simulation, Logic has a level and a strength
- Logic levels are 0 and 1
- Logic Strength can be strong or weak
- A strong 0 has a logic level 0 with forcing strength
- A weak 0 has a logic level 0 with resistive strength
- A logic not at any level has a logic strength of high impedance

# IEEE Std 1164-1993

IEEE Standard Std 1164-1993 defines a 9-value logic system

![[IEEE Std 1164-1993.png#pic_center|IEEE Std 1164-1993]]

# Signal Resolution Table

- Signal resolution table defines the logic function operation

![[Inversion (NOT) Resolution Table.png#pic_center|Inversion (NOT) Resolution Table]]
![[AND Resolution Table.png#pic_center|AND Resolution Table]]
![[OR Resolution Table.png#pic_center|OR Resolution Table]]

# Delay Models

- Delay Models describe delays inside logic cell
- Delays include:
	- **Pin-to-pin delay**: between an input pin and an output pin. It represents delay without interconnect
	- **Pin delay**: delay lumped with an input pin
	- **Net delay (Wire delay)**: delay of interconnect
