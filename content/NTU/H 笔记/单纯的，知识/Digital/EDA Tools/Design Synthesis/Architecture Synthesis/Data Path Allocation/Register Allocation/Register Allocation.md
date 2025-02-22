---
aliases: 
tags:
  - digital
  - design_synthesis
  - architecture_synthesis
  - data_path_allocation
---
- Intermediate values have to be stored for the next operation
  中间值必须存储以供下一个操作使用
- The tasks of register allocation is to assign the values to registers aiming at minimizing the number of registers and interconnections
  寄存器分配的任务是将值分配给寄存器，旨在最小化寄存器和连接的数量。
- Values that do not exist at the same period can share a single register
  在不在一个周期内的值可以共享一个寄存器。
- Well-known register allocation algorithm includes [[Left-Edge Algorithm]] and Clique Partitioning Technique
  著名的寄存器分配算法包括Left-Edge Algorithm和Clique Partitioning Technique。

![[Pasted image 20241029052846.png|Register Allocation Example]]