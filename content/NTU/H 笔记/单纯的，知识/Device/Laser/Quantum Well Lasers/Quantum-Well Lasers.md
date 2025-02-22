---
aliases:
  - QW Laser
tags:
  - laser
  - heterostructure
  - semi_conductor
---
# Single Quantum-Well lasers

- The structure of a quantum-well (QW) laser is similar to that of a [[Double-Heterojunction (DH) Laser|DH Laser]] except the thickness of the active layer in a QW laser is very small, less than $20 \mathrm{nm}$.
![[Pasted image 20241103050241.png#pic_center|]]
- The band diagram of a **single QW Laser** where the central GaAs region $L_y=20 \mathrm{nm}$, sandwiched by two AlGaAs layers.
- **Carriers and photons are confined in the single QW**

# Multiple Quantum-Well (MQW) Lasers

![[Pasted image 20241103050930.png#pic_center|cross section schematic of Separate-Confinement-Heterostructure (SCH) InGaAs/InGaAsP MQW laser]]

The 4 InGaAs QWs with InGaAsP barrier layers are sandwiched by the two InP cladding layers to form a waveguide with a step index change.

![[Pasted image 20241103051806.png#pic_center|Schematic of the bandgap of the SCH MQW layers.]]

- The InGaAs wells are $8\mathrm{nm}$ thick with a $E_g$ of $0.75e\mathrm{V}$ The GaInAsP barriers are 30 nm thick with a $E_g$ of $0.95e\mathrm{V}$.
- The alloy compositions make them [[Lattice-Matched Heterostructures|Lattice Matched]] to InP.

## Graded-Index SCH MQW Lasers

- One can also introduce graded-index (GRIN) to the SCH laser by increasing the $E_g$ of the cladding layers through many small stepwise increases rather than one step change. It will be called GRIN-SCH-MQW laser.

![[Pasted image 20241103053442.png#pic_center|energy bandgaps of a GRIN-SCH MQW laser]]
- It is also possible to change the energy bandgap of the GRIN cladding layer gradually rather than by steps.
![[Pasted image 20241103054013.png|Schematic of a Triple-Quantum-Well (TQW) Laser with GRIN-SCH]]

![[Pasted image 20241103054233.png#pic_center|Light output power vs current curves measured at different temperatures for the GRIN-SCH TQW laser]]

# Advantages Compared to DH Lasers

- Smaller $I_{\mathrm{th}}$ (17mA vs 80mA at room temperature, $I_{\mathrm{th}}$ os as small as possible)
- Higher $T_O$ (260℃ vs 110℃, higher the better)
	- This is because the GRIN-SCH structure can [[Carrier and Optical Confinements|confine both carriers and the optical field]] more effectively.

# Example

For high temperature laser operation, it is important to have a low-temperature coefficient of the threshold current, defined as$$\xi=\frac{\mathrm{d}I_{th}}{\mathrm{d}T}\frac{1}{I_{th}}$$
1. What is the coefficient for the laser with $T_O=110\mathrm{^\circ C}$?
2. If $T_O=50\mathrm{^\circ C}$, is this laser better or worse for high temperature operation?
## Solution

1. 考虑[[Double-Heterojunction (DH) Laser#Threshold Current Varies With Temperature|阈值电流与温度]]的表达式（您也没说这公式在SQW Laser也成立啊）：$$\displaylines{I_{th}=I_Oe^{\frac{T}{T_O}}\implies\xi=\frac{\mathrm{d}}{\mathrm{d}T}\left(I_Oe^{\frac{T}{T_O}}\right)\frac{1}{I_Oe^{\frac{T}{T_O}}}\\=\frac{I_O}{T_O}e^{\frac{T}{T_O}}\cdot \frac{1}{I_O e^{\frac{T}{T_O}}}=\frac{1}{T_O}=0.0091{^\circ C}^{-1}}$$
2. $$\xi=1/50=0.02{^\circ C}^{-1}>0.0091{^\circ C}^{-1}\implies \mathrm{worse}$$
