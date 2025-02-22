---
aliases: 
tags:
  - architecture_synthesis
  - digital
  - design_synthesis
---
- The task is to assign the operation nodes of a [[Data Flow Graph|DFG]] to Control Steps (or Clock Cycles) under certain constraints and subject to the precedence constraint
  任务是将数据流图（DFG）的操作节点分配给控制步骤（或时钟周期），在特定约束和优先约束的条件下进行。（编译器里的抽象语法树？）
- The constraints can be:
	- Hardware Resource
	  硬件资源
	- Operation Speed (Number of Clock Cycles)
	  运行速度（时钟周期数）
- A high-level synthesiser can:
  高层综合器可以：
	- Optimize the **hardware** resource under the **speed** constraint
	  在速度约束下优化硬件资源
	- Optimize the **speed** resource under the **hardware** constraint
	  在硬件资源约束下优化速度

# Operation Scheduling Algorithms

（全是例子学个鸡毛）

![[Pasted image 20241029052640.png#pic_center|A DFG Example]]
## As Soon As Possible (ASAP)

所有资源都尽可能早地进入流水线。
![[Pasted image 20241029052658.png]]

## As Late As Possible (ALAP)

所有资源都尽可能晚地进入流水线。从最后一级倒退回去的遍历策略和ASAP一样。
![[Pasted image 20241029052719.png]]

## List Scheduling

- 根据一个Data Path上的节点数量来判断优先级，节点数量越多的一支优先级越高，越先进入流水线。
- 如果优先级一样，可以考虑其他的因素。
- 如果有空闲的资源会尽早利用上。
![[Pasted image 20241029052739.png]]

## Force Directed Scheduling

（没写）

## Integer Linear Programming Scheduling

（没写）