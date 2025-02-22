---
aliases:
  - 载流子和光限制
tags:
  - laser
  - semi_conductor
---
![[Pasted image 20241103025929.png#pic_center|Carrier Conffinement]]
- Take the [[Population Inversion#^103958|DH Laser]] as an example, the carriers are confined within the active region by the heterojunction energy barriers.
  以双异质结激光器为例，载流子通过异质结势垒被限制在有源区内。
  
  ![[Pasted image 20241103030345.png#pic_center|Optical Confinment]]
- The optical field is also confined within the active region by the abrupt reduction of the refractive index outside the active region.
  光场也通过有源区外折射率的急剧下降被限制在有源区内。
- AlGaAs has smaller refractive index than GaAs.
  AlGaAs的折射率比GaAs小。

![[Pasted image 20241103031217.png]]
- Consider that the three layer structure with layers 1,2,3 are n-AlGaAs, GaAs and p-AlGaAs, respectively. And $n_2>n_1,n_3$. The ray angle $\theta_{12}$ at the layer 1/2 intergace exceeds the critical angle given by Snell's law $$sin(\theta_c)=\frac{n_1}{n_2}$$ A similar situation occurs for $\theta_{23}$ at layer 2/3 interface. In this case, the propagation of optical radiation is confined in the direction parallel to the layer interface in the active region.
  考虑具有三层结构，其中层1、2、3分别是n-AlGaAs, GaAs和p-AlGaAs。而且 $n_2>n_1,n_3$。层1/2界面处的射线角度$\theta_{12}$超过了由**斯涅尔定律**给出的临界角$$sin(\theta_c)=\frac{n_1}{n_2}$$在层2/3界面处也会出现类似的情况。在这种情况下，光辐射的传播被限制在有源区内平行于层界面的方向。
- We can define a confinement factor $\Gamma$, which is the ratio of the light intensity within the active layer to the sum of light intensity both within and outside the active region.$$\Gamma=\frac{I_{\mathrm{active\ region}}}{I_{\mathrm{total}}}\cong1-e^{-Cd\Delta n}$$where:
	- $C$ is a constant
	- $\Delta n$ is the difference in refractive index
	- $d$ is the thickness of the active region