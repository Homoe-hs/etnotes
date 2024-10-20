---
publish: "true"
---
# 2022-11-18

需要做一个心电采集装置。

采集的信号特征
- $V_{pp}=5 mV, Freq=0.05Hz \sim 150Hz$；
- 差分信号；
- 来自多个电极；
- 存在干扰
	- 电极存在直流偏移；
	- 电力线有 1.5V 50Hz 的信号干扰；
- ADC 的满刻度电压为 2.5V

问题：
- 解决直流偏置问题是否需要分割增益，什么是分割增益
- 什么是陷波滤波器
- inst 建议使用一个带通滤波器，但是我认为一个低通滤波器也足够
- 右腿驱动电路是什么
# 2022-11-20

开始写报告，需要仔细审查**评分标准**以及**器件规格**。

> 这一部分是你报告中最大的部分。你很可能需要包括以下内容。
> 1.	对你的设计的概述
> 2.	你的原型顺序（如果相关的话）。我的意思是你经历了哪些事件的顺序来完成最终的设计？这应该包括相关的计算和 LTSpice 模拟。记住你是在写一份报告，而不是一本日志。你需要编辑这个，所以它只包括导致最终设计的信息。
> 3.	你的测试程序和结果。(例如：最终设计的 LTSpice 模拟)
> 4.	对你的最终设计和其性能的评估。(需要一个批判性的分析，并对未来的改进提出建议)
> 对于每个分节，写一个具体的标题，以帮助你的读者找到他们需要的信息。

# 2022-11-26
- 为避免接地问题，REF 应在连接到地面之前连接一个小电阻。
- 首先是选择要使用的器件。使用的 IA 是 AD8227，因为它的 GAIN 很容易通过连接一个外部电阻来确定，而且当 GAIN 为 10 时，它的 CMR 很高，接近 100dB。同时，它对温度不敏感，价格便宜。对于其他三个放大器，使用 OP07，因为它也很便宜，而且对温度不敏感。
- ADC 是 0 ~ 2.5 V？
- 低通滤波器和高通滤波器的组合与带通滤波器有什么区别？ 那为什么要拆开？ -将高通滤波器放在最后是为了消除器件可能带来的噪声。
- 由于这个装置应该是便携式的，所以它的组件必须具有低能耗、对温度不敏感和容易被带走的特点。最后，必须考虑整个装置的价格。
- 结果表明，该电路具有良好的性能，但可以考虑在该电路中进行一些改进，如安全保护和缺口电路，以形成一个更有竞争力的设计。
- 在 IA 部分，由于 AD8227 具有较高的 CMRR 和其他特性，所以使用了 AD8227，而其他两部分则使用了 OP07。在滤波器部分，巴特沃斯滤波器被用来过滤信号。

- Singular matrix: check node d:u1: 25 # int1 Iteration No.3
	- 在 IA 的 ref 接了一个 100 ohm 的电阻（参考的别人报告）就好了，但是不知道为什么这样就不会报错了
	- 看网上说是那个节点的电流太小了

- 巴特沃斯滤波器（Butterworth filter）是电子滤波器的一种，它也被称作最大平坦滤波器。巴特沃斯滤波器的特点是通频带内的频率响应曲线最大限度平坦，没有纹波，而在阻频带则逐渐下降为零。

# 2022-11-27

- 放弃使用二阶巴特沃斯滤波器，暂时来说有点困难并不能做好，并且电路的复杂程度并不构成评分的重要指标。
	- 采用原有的电路结构，但是在原来的基础上优化了电阻和电容的值
- 对于 zotero 无法引用 manual 和 datasheet 的问题
	- 暂时的解决方案：[Adding Datasheet or Manual item type - Zotero Forums](https://forums.zotero.org/discussion/86140/adding-datasheet-or-manual-item-type)

- 摘要：它是用过去式写的吗？它是否独立于报告并对报告进行总结？摘要不是用过去式写的。摘要是单独存在的。我的建议是将摘要改为过去式。
- 引言。设计问题是否已经确定？目标是否明确。设计问题已经被定义，目标也很明确。我认为把心电图的介绍性陈述减少一些可能会好一些。
- 分析。是否有对设计的概述？原型设计事件的顺序是否清楚，是否导致了最终的设计？最终的设计选择是否清楚？是否有对设计的批判性分析？有对设计的概述，原型设计事件的顺序是清楚的，并且导致了最终的设计。最终的设计选择是明确的。有对设计的批判性分析。但是，我建议批判性分析的部分可以更具体一些。
- 结论。你能从之前提出的结果和分析中得出所述的结论吗？可以从前面介绍的结果和分析中得到结论。关于陷波滤波器的部分也许可以更详细地解释。在分析部分，你应该讨论陷波滤波器，否则，你不能在结论部分谈论陷波滤波器。
- 参考文献。参考文献是否做得正确？所用的参考文献是否相关？参考文献是正确的、相关的。在这一部分，我认为可以有两到三个参考文献。
- 报告不够学术性

收到了以下反馈：
1. 摘要中混杂了过去时和一般现在时；
2. 引言中有太多与 ECG 词的定义相关的内容；
3. 对于电路的批判性分析不够具体；
4. 结论中出现了正文内容中没有的内容；
5. 参考文献明显过少；
6. 报告的学术性不够。
根据以上的反馈，摘要现在已经全部修改成了过去时；引言中过多的对于 ECG 本身的叙述被删除了；详细地分析了电路的优缺点，并把结论中谈及的内容进行了修改；增加了本应该有的引用；针对全文的非学术性语言进行了修改。

# 2022-11-28
- [Fetching Title#dvly](https://glenzac.wordpress.com/2018/11/09/ecg-sources-for-pspice-tina-multisim/)
	- 心电信号仿真