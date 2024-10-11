---
aliases: []
tags:
---
这个推导相当简单。我们先观察这个 Ebers-Moll 公式电流关系式，
$$
\begin{align}
I_{E} & =-I_{F_{0}} \left[ \exp{(  \dfrac{qV_{B E}}{kT})} -1 \right]+\alpha_{R} I_{R 0} \left[ \exp{(  \dfrac{qV_{B E}}{kT})} -1 \right]\\ \\
I_{C} & =\alpha_{F} I_{F 0} \left[ \exp{(  \dfrac{qV_{B E}}{kT})} -1 \right]-I_{R 0} \left[ \exp{(  \dfrac{qV_{B E}}{kT})} -1 \right]
\end{align}
$$
简化一下，
$$
\begin{align}
I_{E} & =-I_{F_{0}} K+\alpha_{R} I_{R 0} K\\ \\
I_{C} & =\alpha_{F} I_{F 0} K-I_{R 0} K
\end{align}
$$
构建 $\alpha_{F}I_{E}$，
$$
\alpha_{F}I_{E} = -\alpha_{F}I_{F_{0}}K+\alpha_{R}\alpha_{F}I_{R_{0}}K
$$
将上式和 $I_{C}$ 相加，
$$
I_{C}+\alpha_{F}I_{E} = -I_{R_{0}}K+\alpha_{R}\alpha_{F}I_{R_{0}}K
$$
最后整理得，
$$
I_{C} = -(1-\alpha_{R}\alpha_{F})I_{R_{0}}K-\alpha_{F}I_{E}
$$
![[用 Ebers-Moll 模型推导击穿电流关系.png]]
代入到上图中的电路中去，此时 $V_{CB}$ 为负值，$K$ 会非常接近 $-1$，这样我们就得到了此时的反向偏置电流 $I_{CBO}$，即为 $I_{CBO} = I_{R_{0}}(1-\alpha_{F}\alpha_{R})$。
