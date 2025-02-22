---
aliases: 
tags:
  - laser
  - semi_conductor
---
# Optical Gain

The photons released by stimulated emission can cause further stimulations as long as there is **population inversion**. This process is called **optical gain**.
只要存在**粒子数反转**，由受激发射释放的光子就能进一步引发更多的受激发射。这一过程被称为**Optical Gain**。

The gain obtained in a single travel in the active region is small.
在有源区内单次传播获得的增益很小。

To increase the optical gain, multiple passes of a wave must occur. This can be achieved by an optical cavity which is essentially a resonant cavity in which the photons have multiple reflections.
为了增加光学增益，光波必须进行多次传播。这可以通过光学腔体来实现，光学腔体本质上是一个谐振腔，光子在其中进行多次反射。

For semiconductor lasers, the most widely used cavity is the Fabry-Perot cavity.
对于半导体激光器，最广泛使用的腔体是法布里-佩罗谐振腔。

# Fabry-Perot Cavity

![[Pasted image 20241103032241.png]]
- (a) A typical laser structure showing the Fabry-Perot cavity.
  展示法布里-佩罗谐振腔的典型激光结构。
	- The **Fabry-Perot Cavity** is formed by mirrored surfaces on two sides (**left and right**). The other two sides (**front and back**) are roughened.
	  法布里-佩罗谐振腔由两侧（**左侧和右侧**）的镜面形成，其他两侧（**前侧和后侧**）粗糙。
- (b) The stationary states of the cavity.
  谐振腔的稳定状态。
	- The photons to be emitted towards these mirrored sides are multiple reflected back. Photons at **resonant modes** are allowed to build up through stimulated emission. 
	  光子向这些镜面发射时会被多次反射。光子在**谐振模式**下通过受激辐射积累。
- (c) The variation of refractive index (or dielectric constant) responsible for optical confinement.
  负责光限制的折射率（或介电常数）的变化。

## Resonant Modes

- Resonant modes are those for which integer multiple half wavelength of the light in the cavity equals the length of the cavity:$$m\left(\frac{\lambda}{2n}\right)=L$$or$$m\lambda=2nL$$where:
	- $m$ is an integer
	- $L$ is the cavity length
	- $n$ is the refractive index of the cavity
	- $\lambda$ is the light wavelength
![[Pasted image 20241103035316.png#pic_center]]
- Many values of $λ$ can satisfy the resonance condition but only those within the spontaneous emission spectrum will be produced.
  许多 $λ$ 的值可以满足谐振条件，但只有波长在自发辐射光谱内的会被产生。
- Due to optical loss, only the strongest can survive.
  由于光损耗，只有最强的可以留存
- The separation $\Delta \lambda$ between the allowed modes in the longitudinal (propagating) direction is the difference in the wavelengths corresponding to $m$ and $m+1$.
	- It can be obtained by differentiating $m\lambda=2nL$ and is expressed as$$\Delta \lambda=\frac{\lambda^2\Delta m}{2nL\left(1-\frac{\lambda}{n}\frac{\mathrm{d}n}{\mathrm{d}\lambda}\right)}$$
	- Although $n$ is a function of $\lambda$ but the change $\frac{\mathrm{d}n}{\mathrm{\lambda}}$ is very small. $\Delta m=1$. Therefore,$$\left|\Delta \lambda\right|\cong\frac{\lambda^2}{2nL}$$
