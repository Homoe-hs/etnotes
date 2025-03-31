---
对象类型: 
aliases: 
tags:
---
# Q1

- The short channel effect in MOSFETs refers to the phenomenon, lowering of $V_{t}$ etc. , happens when the length of gate shrink to close to the width of depletion layer $W_{dep}$. 
- When the MOSFET is under SCE, the drain current will increase with the drain-source voltage due to Channel Length Modulation Effect; The subthreshold swing will increase which makes the device hard to close completely; The threshold voltage could decrease due to Drain Induced Barrier Lowering.
- According to the formula $\Delta V_{T}=\frac{Q_{B} T_{o x}} {\varepsilon_{o x}} \frac{r_{j}} {L} ( \sqrt{1 \!+\! \frac{2 X_{d m}} {r_{j}}}-1 )$, there could be at least three ways to suppress the SCE,
	1. Increase the $\varepsilon_{ox}$ by using high-k material or reducing the thickness of oxide;
	2. Increase the $N_{B}$ to decrease the $X_{dm}$ to minimize the chance of punchthrough (Channel Engineering);
	3. Decrease the junction depth $r_{j}$ by using the shallow junction;

# Q2

Reasons why MOSFET made on Si has better high frequency performance are listed as follow,
1. Scaling down has improved the transconductance and decrease the gate capacitance, which made the progress in cutoff frequency of Si MOSFET; 
2. Introducing tensile strain and compressive strain through strained silicon technology to improve carrier mobility;
3. Using of high-k dielectric and metal gate optimizes gate capacitance and transconductance
4. Fin-FET and GAA-FET enhanced the control ability of gates;
5. Shallow junction and Salicide decrease the source/drain resistor.

# Q3

Tensile strain will change the shape of energe band, the lift of the CB degeneracy will reduce the intervalley scattering results in mobility improvement. Thus the cutoff frequency $f_{T}$ will be improved. 

# Q4

The FEOL CMOS fabrication flow can be described as follow,
1. Using p-type silicon substrate, photolithography defines the N-well and P-well, i mplants phosphorus and boron saperately;
2. Dry etching forms a shallow trench, filling with $\ce{ SiO_{2} }$；
3. Deposition of high-k dielectrics to form the gate;
4. Source and drain extension injection to form a shallow junction;
5. Formation of sidewall spacer;
6. Source (drain) injection to form a doped region;
7. Self-aligned silicide metal deposition;
8. contact hole etching and PVD the Cu to form Metal 1 interconnectio

![[FEOL.drawio 1.png]]

# Q5

1. By choosing the right metal, its thermal expansion coefficient can be made close to that of high-k dielectrics, thereby reducing thermal stress. Metals can also be integrated at low temperatures, avoiding high temperatures. As conductors, metals can also evenly distribute the electric field, reducing the risk of breakdown;
2. Metal materials (such as TiN) are dense and have stable lattices, which block the migration of impurity atoms;
3. The metal gate is a continuous thin film without polysilicon grain boundary defects, thus avoiding the oxidation of high-k dielectric to form a low-k interface layer.
