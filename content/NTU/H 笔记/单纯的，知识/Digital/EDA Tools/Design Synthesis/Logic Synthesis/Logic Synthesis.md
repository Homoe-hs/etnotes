---
aliases: 
tags:
  - design_synthesis
  - digital
  - eda_tools
  - TODO
---
- User synthesis tools to translate HDL to a netlist of logic gates adn their connections.
  用户使用综合工具将HDL翻译为逻辑门及其连接的网表

- Logic Synthesis generates a gate-level implementation (structure view) of a logic function (logic-level view)
    逻辑综合生成逻辑函数的门级实现（结构视图）
- The logic function can be specified in terms of state transition diagrams, schematics, Boolean equations, truth table or HDL descriptions
  逻辑函数可以通过状态转换图、原理图、布尔方程、真值表或HDL描述来指定
- Synthesis results depend on the implementation architecture: multilevel logic, PLA, FPGA/CPLD
  综合结果取决于实现架构：多级逻辑、PLA、FPGA/CPLD

# Logic Synthesis Tasks

- The objective of logic synthesis is to optimize the area, speed, power, or their combination
  逻辑综合的目标是优化面积、速度、功耗或它们的组合。
- The task has two main stages:
  这一目标有两个步骤
	- Logic minimization: a technology independent phase, where the logic is optimized using a number of Boolean algebraic manipulation techniques.
	  逻辑化简：一种与技术无关的阶段，在此阶段中使用多种布尔代数操作技术对逻辑进行优化。
	- Technology mapping: a phase considers the implementation architecture, such as standard cells, PLA, FPGA/CPLD, etc.
	  工艺映射：一个考虑实现架构的阶段，例如标准单元、PLA、FPGA/CPLD等。

# Combinational Logic Synthesis

![[Pasted image 20241029052049.png#pic_center|Multi-Level Logic Implementation using OR-AND-NOT gate]]

对一个[[Full Adder|全加器]]进行Combinational Logic Synthesis. 全加器的布尔表达式：$$\displaylines{S=A\oplus B \oplus C_i \\ C_o=AB+BC_i+AC_i=\overline{\overline{A\cdot (B+C_i)}\cdot(\overline{B}+\overline{C_i})}}$$

将原始的表达式转换为使用更加简单逻辑门的形式
# Sequential Logic Synthesis

- **State Minimization**: Two states are equivalent if the output sequences for any input are the same
  **状态化简**：如果对于任意输入，两种状态的输出序列相同，则它们是等价的。
- **State Encoding**: Different code assignment for the states can result in different logic implementation
  **状态编码**：不同的状态编码分配可能会导致不同的逻辑实现。
- **State Machine Decomposition**: Dividing a large state Machine into 2 or more small ones. Logic will be simpler and easier to be minimized. Speed can be increased too.
  **状态机分解**：将一个大型状态机划分为两个或多个小型状态机。逻辑将更简单且易于最小化，速度也可能提高。
- **Retiming**: The clock speed depends on the delay between any two stages of a sequential circuit. By rearranging the sequential logic elements (flip flops), the delay can be reduced.
  **重定时**：时钟速度取决于顺序电路中任何两个阶段之间的延迟。通过重新排列顺序逻辑元件（触发器），可以减少延迟。
  
## Retiming of Sequential Logic Circuit

移动组合逻辑来平衡延迟

![[Pasted image 20241029052225.png|Retiming]]

![[Pasted image 20241029052317.png#pic_center|]]
- Moving the AND gate reduces delay on one path but increase delay on another
  移动与门减少了一个路径上的延迟，但增加了另一个路径上的延迟。