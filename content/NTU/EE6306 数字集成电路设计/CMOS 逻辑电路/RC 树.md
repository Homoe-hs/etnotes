---
date: 2024-09-15 20:51
aliases: 
tags: 
---
![[RC 树.png|400]]

形如上图的电阻-电容网络即为 RC 树。

# 性质

- 仅有一个输入节点 $s$；
- 所有电容都在某个节点和地之间；
- 不包含任何电阻回路

# 路径电阻与共享路径电阻

这个特殊的电路拓扑的一个有意义的结果在于源节点和任意节点 $i$ 之间只存在唯一的电阻路径。沿着这条路径的总电阻定义为路径电阻 $R_{ii}$。由此延伸，从根节点 $s$ 到节点 $k$ 和节点 $i$ 这两条路径的共享路径电阻 $R_{ik}$ 为，
$$
R_{ik} = \sum R_{j}\Rightarrow(R_{j}\in[ path(s\to i)\cap path(s\to k)])
$$

# RC 链

为 RC 树网络的特殊情形，RC 链 (即梯形链) 不具有其他分支。

![[RC 链.png|400]]
