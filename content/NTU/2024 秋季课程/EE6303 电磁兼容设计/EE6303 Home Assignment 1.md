---
aliases: []
tags:
---
# (a)

The equivalent circuit model of the carbon resistor can be draw as below,
![[EE6303 Home Assignment.drawio.png]]
Here we can know that, 
- $R = 47\pu{ k\Omega }$, 
- $l = 50\pu{ mm }  = 0.05\pu{ m }$, 
- $D = 5\pu{ mm } = 5 \times 10^{-3} \pu{ m }$, 
- $r = 0.25\pu{ mm } = 2.5 \times 10^{-4}\pu{ m }$
- $\epsilon_{0} = \dfrac{1}{36\pi}\times 10^{-9}\pu{ F/m }$

The lead capacitor can be calculated,
$$
\begin{align}
C_{lead}  & = \dfrac{\pi\varepsilon l}{\ln\left[\dfrac{D}{2r}+\sqrt{\left(\dfrac{D}{2r}\right)^2-1}\right]} \\
 &  = \dfrac{\pi \dfrac{1}{36\pi}\times 10^{-9} \times 0.05}{\ln\left[\dfrac{5 \times 10^{-3}}{2\times 2.5 \times 10^{-4}}+\sqrt{\left(\dfrac{5 \times 10^{-3}}{2\times 2.5 \times 10^{-4}}\right)^2-1}\right]}  \\
 & = 4.640\times 10^{-13} \pu{ F }=0.464 \pu{ pF }
\end{align}
$$
Assume there will be skin effect in the copper leads, the lead inductance can be given,
$$
\begin{align}
L_{lead} & =4l\times10^{-7}\ln\biggl(\frac{D-r}{r}\biggr) \\
 &  = 4 \times 0.05 \times 10^{-7}\times \ln{(\dfrac{5\times 10^{-3}-2.5\times 10^{-4}}{2.5 \times 10^{-4}})} \\
 & = 5.889 \times 10^{-8} \pu{ H } = 58.89 \pu{ nH }
\end{align}
$$
The can be indicate as below,
![[EE6303 Home Assignment with number.png]]

# (b)

With $R =120\pu{ \Omega }$
![[120.png|600]]

# （c）

With $R =680\pu{ k\Omega }$
![[680.png|600]]
# (d)

![[together.png|600]]

I put two figures into one, and I found that when the frequency increase, the overall impedance closing to one value around 0.6GHz. This is because for large value R, the effect of  parasitic capacitance dominates, however for small value R, the effect of parasitic inductance dominates.
