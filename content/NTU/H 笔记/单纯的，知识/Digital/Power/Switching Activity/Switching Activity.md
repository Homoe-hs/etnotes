---
aliases: 
tags:
  - digital
  - power
---
# Goh

- Suppose $\mathrm{system\ clock\ frequency}=f$
- Let $f_{sw}=\alpha f$, where $\alpha = \mathrm{activity\ factor}$
	- If the signal is a clock, $\alpha = 1$
	- If the signal switches once per cycle, $\alpha = 1/2$
	- Dynamic gates:
		- Switch either 0 or 2 times per cycle, $\alpha = 1/2$
	- Static gates:
		- Depends on design, but typically $\alpha = 0.1$
- Dynamic power: $P_{\mathrm{dynamic}}=\alpha C_L V_{DD}^2f$

# Gwee #TODO 

- The switching activity, $f_{0\to 1}$ , is a function of the nature and statistics of the input signals. If the input signals remain unchanged, no switching happens, and the dynamic power consumption is zero. On the other hand, rapidly switching signals increase the amount of switching and hence power dissipation.
- Other factors influencing the activity are the circuit style, function to be implemented and the overall network topology.
- $P_{\mathrm{dynamic}}=C_L V_{DD}^2 f_{0\to 1}$ can be modified to $P_{dynamic}=C_L V_{DD}^2 P_{0\to 1}f$, where $f$ is the average event rate of the inputs and $P_{0\to 1}$, the probability that an input transition results in a $0\to 1$ (power-consuming) event.

## Reduction

- **Logic Restructuring**: Changing the topology of a logic network may reduce its power dissipation (Chain vs Tree)
- **Input Ordering**: A simple reordering of the input signals can reduce switching activity
- **Glitch Reduction by Balancing Signal Paths**: Equalizing arrival times of signals can reduce the spurious transitions, thereby reducing glitches

# CC

没说