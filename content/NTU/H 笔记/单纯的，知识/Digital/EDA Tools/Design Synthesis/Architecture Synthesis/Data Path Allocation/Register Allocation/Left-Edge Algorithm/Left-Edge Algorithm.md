---
aliases: 
tags:
  - digital
  - design_synthesis
  - architecture_synthesis
  - data_path_allocation
  - register_allocation
---

- 将所有值的生命周期按照左端点排序列在表中。
- 遍历整个列表，不断选择没有重复的段，并合并

![[Pasted image 20241029052908.png#pic_center|Lifetime Table]]
- 上图中，所有值都按照左序排列
- 其中e1，e3，e4没有重复，所以可以合并到一个寄存器R1中
- 其他的值也是这么操作。

- 使用图论可以轻松地知道每个资源之间的冲突情况。
	- 可以用一个无向图表示冲突情况：节点表示寄存器资源，无向边表示两个节点间存在冲突。
		- 寄存器数量即是能够保证相邻节点颜色不同的最小颜色数。

