---
aliases:
  - Behavioural Synthesis
  - High-Level Synthesis
tags:
  - digital
  - design_synthesis
---

- It generates a structural view of an architecture design from a behavioural description of the task to be executed
  它从要执行的任务的行为描述中生成架构设计的结构视图
- It optimizes one or more performance factors such as area, speed and power
  它优化一个或多个性能因素，例如面积、速度和功耗
- Two main tasks:
	- [[Operation Scheduling]]
	- [[Data Path Allocation]]

# Difficulties

- A lack of understanding of what a behavioural description means at the architecture level for some domains, such as general-purpose $\mathrm{\mu Ps}$
- Behavioural synthesis assumes the availability of an established synthesis approach at the register transfer level
- Lack of physical layout information at the behavioural level, specially on interconnections and power consumption